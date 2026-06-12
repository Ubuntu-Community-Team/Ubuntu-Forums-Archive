---
title: "ATI Radeon 7000/VE Problems"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by ammut on 2008-02-03
Ok, so my last post was garbled and I doubt anyone understood what I was asking.  This time, I'll try to be more clear.

I am running Ubuntu 7.10 on a Dell Dimension 3000.  It has a built in chipset (Intel 865G) which is incapable of running 3d acceleration.  I have only PCI expansion slots, so I have installed an ATI Radeon 7000/VE 64MB (PCI) graphics card.

From what I have read, it -seems- this card is 3d acceleration capable, however every driver I have tried seems to fail.  Is there a driver that works for this card? If so, where can I find it and a howto for installation purposes? :confused:

---

### Post by ammut on 2008-02-04
Ok, so I made a backup of my original xorg.conf, deleted the current, rebooted and now my card works but it is extremely slow.

my glxinfo output:
```
name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20061018 x86/MMX/SSE2 NO-TCL
OpenGL version string: 1.2 (1.3 Mesa 7.0.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias

```

So it loaded a driver, but something is still amiss.

---

### Post by ammut on 2008-02-04
so another update as to my situation:

I have completely removed fglrx from my system as per the ubuntu HOWTO on installing the open source ati driver.  I have done everything step-by-step to get this to work.  When I finalize my changes to xorg.conf and ctrl+alt+backspace to reload the xserver, it tells me I need to select the driver again with a window prompt that looks like the screens & graphics one.  

No matter what I select it boots into failsafe mode using the vesa driver.  so I have tried using the open source ati driver, fglrx as well as envy and have not had any success.  

Does the ATI Radeon 7000/VE PCI graphics card just not work with Ubuntu? I see numerous threads relating to this card and none seem to have been solved.  Any help is appreciated!!:confused:

---

### Post by chewit on 2008-02-04
as you can see in my sig, i have a ATi 7000, it works fine. I use the radeon driver which comes with 7.10

---

### Post by ammut on 2008-02-04
I appreciate the response! However, I must point out one thing:

When I am doing a sudo dpkg-reconfigure xserver-xorg, it does not give me the option for 'radeon'.  I see only 'ati' in the drivers list.  I had fglrx installed and it was an option, but I have removed it since.  Is there some way to force the 'radeon' driver to be the one I am using? In the end, all I want this card to do is be direct rendering capable.

My card is a PCI Radeon 7000, is yours an AGP? I think this might be causing some problems.

---

### Post by ammut on 2008-02-04
I just tried to reconfigure my xserver-xorg to use 'radeon' as the driver and had no good luck.  I got a black screen on startup, so I've gone back to using the onboard chipset w/ a vesa driver.

I have tried:
ati
envy
radeon
fglrx
vesa

with my Radeon 7000 PCI card.  None seem to work properly; my onboard chipset has much smoother graphics than the pci card.  I don't know why that is, seeing as how I only have 8MB onboard memory and 64MB on the pci card.  

I must admit, I am a noob.  But to truly understand Ubuntu one must play with the settings and try to figure out more about it.  Again, I appreciate any help on my quest to get direct rendering working :)

---

### Post by chewit on 2008-02-04
My 7000 card is PCI. 

Why isn't the Radeon driver not working?

---

### Post by ammut on 2008-02-04
maybe if you posted your xorg.conf file it would shed some light on my problem.  I have done a

sudo apt-get install xserver-xorg-video-all

which -should- in theory, install all the drivers I would ever need.  I still do not see 'radeon' as an option in the reconfiguration process.  I also cannot run

/usr/bin/restricted-manager

to use restricted drivers (which I had hoped might work).

---

### Post by reed026 on 2008-02-04
```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```

This is mine mate. I am running a low profile Radeon 7000 VE in a Dell GX260 running 7.10. 

My only problem appears to be 3d acceleration with Google Earth, however normal games are fine, such as enemy territory. I'll most likely upgrade to a NVidia product when it's time for an upgrade as ATI has been more of a headache than helpful.

---

### Post by chewit on 2008-02-04
> **ammut said:**
> maybe if you posted your xorg.conf file it would shed some light on my problem.  I have done a

sudo apt-get install xserver-xorg-video-all

which -should- in theory, install all the drivers I would ever need.  I still do not see 'radeon' as an option in the reconfiguration process.  I also cannot run

/usr/bin/restricted-manager

to use restricted drivers (which I had hoped might work).

I'm at school atm, i will post it when i get home. You say you can't see the radeon driver, well you can always download it & install it.

---

### Post by reed026 on 2008-02-04
ammut, 

After some research, I do not believe the fglrx driver is intended on use in Radeon 7000 VE Graphics Cards. Last night I attempted installing this driver to try it out for myself, however it screwed up my desktop and I had to manually remove it using a command prompt. 

I would just stick with the basic Radeon driver that comes installed with ubuntu as it will run fine enough for compiz fusion with only a few of the bells and whistles enabled.

---

### Post by ammut on 2008-02-04
Ok, well I think I have a plan of action to try to figure out what might be the problem here.  If anyone can think of another thing I can try or check, please add it here.

I will reinstall the entire xserver-xorg package list
I will try PCI 2:0:0 instead of 1:0:0 in case it is damaged
Use the above posted xorg.conf and cross my fingers

From what I can tell the 'ati' driver has replaced the 'radeon' driver.  It is not listed as a package available in Synaptic or through aptitude.  So I will try to use the 'ati' driver a few more times and see if reconfiguring the xserver-xorg will make it work.

---

### Post by ammut on 2008-02-04
compiz fusion you say? I'm still pretty lost in terms of understanding the graphics capabilities of linux but would love to learn more about it so I can run a linux only system.  

what exactly is compiz fusion?

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

I get this when I type compiz at the terminal line, then it reloads my windows and ends.  

So basically afaik, xserver-xorg creates an 'x windows system' which is the desktop gui environment.  There are add on things that go along with it like XGL (I don't know what this does either).  A DRI is a direct rendering file or something, right? I've seen an error numerous times telling me it is trying to load an xfree86 DRI file and failing.

Anyway, I'll post my progress and see if I can get this to work tonight.

---

### Post by ammut on 2008-02-04
Alright, so I went into the Synaptic package manager, reinstalled all the xserver-xorg files as well as the driver-ati.  I have moved the card to the second PCI expansion slot (1:1:0).  After doing this, I tried to reconfigure it on my own using

sudo dpkg-reconfigure xserver-xorg

Which made me realise that the dpkg-reconfigure utility is not recognizing my card right away when I allow it to autodetect.  It recognizes my onboard VGA chipset (intel) as the default one and there is no way in the BIOS to turn it off.  You can either select 'automatic' or 'onboard' as your VGA options.  

Is there another way to reconfigure xserver-xorg? 

Also, I tried using the xorg.conf that was posted above (changing the PCI slot ID) to no avail.  I am still using the VESA drivers on this card because ATI will not work.  It gives me a black screen and I cannot ctrl+alt+delete out of it, so I have to hard reset my machine.

Any ideas?

---

### Post by ammut on 2008-02-04
my xorg.conf configuration (working vesa driver on my pci card):
```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc101"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
	Driver		"vesa"
	BusID		"PCI:1:1:0"
	VideoRam	1024000
EndSection

Section "Monitor"
	Identifier	"DELL E173FP"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
	Monitor		"DELL E173FP"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```

My lspci output for (lspci | grep VGA):
```
01:01.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
```

My glxinfo output:
```
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_program, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_fragment_program, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texgen_reflection, GL_NV_texture_rectangle, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x3d 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

My Xorg.0.log output:
```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux fci32 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686
Build Date: 18 January 2008
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Feb  4 19:05:59 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "DELL E173FP"
(**) |   |-->Device "ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(II) Loader magic: 0x81e9800
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(--) using VT number 2

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2570 card 1028,019d rev 02 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,2572 card 1028,019d rev 02 class 03,80,00 hdr 00
(II) PCI: 00:1d:0: chip 8086,24d2 card 1028,019d rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24d4 card 1028,019d rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,24de card 1028,019d rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24dd card 1028,019d rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24d0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24db card 1028,019d rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24d3 card 1028,019d rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24d5 card 1028,019d rev 02 class 04,01,00 hdr 00
(II) PCI: 01:01:0: chip 1002,5159 card 148c,2049 rev 00 class 03,00,00 hdr 00
(II) PCI: 01:08:0: chip 8086,1050 card 1028,019d rev 02 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:30:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfe900000 - 0xfeafffff (0x200000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xea000000 - 0xf7ffffff (0xe000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI: (0:2:0) Intel Corporation 82865G Integrated Graphics Controller rev 2, Mem @ 0xe0000000/27, 0xfeb80000/19, I/O @ 0xed98/3
(--) PCI:*(1:1:0) ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE] rev 0, Mem @ 0xf0000000/27, 0xfe9f0000/16, I/O @ 0xde00/8, BIOS @ 0xfea00000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xe8000000 from 0xe9ffffff to 0xe7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfe9ef000 - 0xfe9effff (0x1000) MX[B]
	[1] -1	0	0xfeb7f900 - 0xfeb7f9ff (0x100) MX[B]
	[2] -1	0	0xfeb7fa00 - 0xfeb7fbff (0x200) MX[B]
	[3] -1	0	0xfeb7fc00 - 0xfeb7ffff (0x400) MX[B]
	[4] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[5] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[6] -1	0	0xea000000 - 0xea01ffff (0x20000) MX[B](B)
	[7] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[8] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0x0000ddc0 - 0x0000ddff (0x40) IX[B]
	[10] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[11] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[12] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[13] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[14] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[15] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[16] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[18] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[19] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[20] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[21] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[1] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[2] -1	0	0x0000ed98 - 0x0000ed9f (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfe9ef000 - 0xfe9effff (0x1000) MX[B]
	[1] -1	0	0xfeb7f900 - 0xfeb7f9ff (0x100) MX[B]
	[2] -1	0	0xfeb7fa00 - 0xfeb7fbff (0x200) MX[B]
	[3] -1	0	0xfeb7fc00 - 0xfeb7ffff (0x400) MX[B]
	[4] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[5] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[6] -1	0	0xea000000 - 0xea01ffff (0x20000) MX[B](B)
	[7] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[8] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0x0000ddc0 - 0x0000ddff (0x40) IX[B]
	[10] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[11] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[12] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[13] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[14] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[15] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[16] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[18] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[19] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[20] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[21] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[1] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[2] -1	0	0x0000ed98 - 0x0000ed9f (0x8) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe9ef000 - 0xfe9effff (0x1000) MX[B]
	[5] -1	0	0xfeb7f900 - 0xfeb7f9ff (0x100) MX[B]
	[6] -1	0	0xfeb7fa00 - 0xfeb7fbff (0x200) MX[B]
	[7] -1	0	0xfeb7fc00 - 0xfeb7ffff (0x400) MX[B]
	[8] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[9] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[10] -1	0	0xea000000 - 0xea01ffff (0x20000) MX[B](B)
	[11] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[12] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000ddc0 - 0x0000ddff (0x40) IX[B]
	[18] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[19] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[20] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[21] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[22] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[23] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[24] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[27] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[28] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[29] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
	[30] -1	0	0x0000ed98 - 0x0000ed9f (0x8) IX[B](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 01:01:0
(--) Chipset vesa found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe9ef000 - 0xfe9effff (0x1000) MX[B]
	[5] -1	0	0xfeb7f900 - 0xfeb7f9ff (0x100) MX[B]
	[6] -1	0	0xfeb7fa00 - 0xfeb7fbff (0x200) MX[B]
	[7] -1	0	0xfeb7fc00 - 0xfeb7ffff (0x400) MX[B]
	[8] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[9] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[10] -1	0	0xea000000 - 0xea01ffff (0x20000) MX[B](B)
	[11] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[12] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000ddc0 - 0x0000ddff (0x40) IX[B]
	[18] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[19] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[20] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[21] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[22] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[23] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[24] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[27] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[28] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[29] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
	[30] -1	0	0x0000ed98 - 0x0000ed9f (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe9ef000 - 0xfe9effff (0x1000) MX[B]
	[5] -1	0	0xfeb7f900 - 0xfeb7f9ff (0x100) MX[B]
	[6] -1	0	0xfeb7fa00 - 0xfeb7fbff (0x200) MX[B]
	[7] -1	0	0xfeb7fc00 - 0xfeb7ffff (0x400) MX[B]
	[8] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[9] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[10] -1	0	0xea000000 - 0xea01ffff (0x20000) MX[B](B)
	[11] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[12] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000ddc0 - 0x0000ddff (0x40) IX[B]
	[21] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[22] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[23] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[24] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[25] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[26] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[27] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[30] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[31] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[32] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
	[33] -1	0	0x0000ed98 - 0x0000ed9f (0x8) IX[B](B)
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 2.0
(II) VESA(0): VESA VBE Total Mem: 65536 kB
(II) VESA(0): VESA VBE OEM: ATI RADEON VE
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) VESA(0): VESA VBE OEM Product: R100
(II) VESA(0): VESA VBE OEM Product Rev: 01.00
(**) VESA(0): Depth 24, (--) framebuffer bpp 24
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level 2
(II) VESA(0): VESA VBE DDC transfer in appr. 2 sec.
(II) VESA(0): VESA VBE DDC read successfully
(II) VESA(0): Manufacturer: DEL  Model: a00b  Serial#: 826692693
(II) VESA(0): Year: 2004  Week: 49
(II) VESA(0): EDID Version: 1.3
(II) VESA(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) VESA(0): Sync:  Separate
(II) VESA(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) VESA(0): Gamma: 2.20
(II) VESA(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) VESA(0): Default color space is primary color space
(II) VESA(0): First detailed timing is preferred mode
(II) VESA(0): redX: 0.640 redY: 0.340   greenX: 0.279 greenY: 0.619
(II) VESA(0): blueX: 0.140 blueY: 0.069   whiteX: 0.310 whiteY: 0.330
(II) VESA(0): Supported VESA Video Modes:
(II) VESA(0): 720x400@70Hz
(II) VESA(0): 640x480@60Hz
(II) VESA(0): 640x480@75Hz
(II) VESA(0): 800x600@60Hz
(II) VESA(0): 800x600@75Hz
(II) VESA(0): 1024x768@60Hz
(II) VESA(0): 1024x768@75Hz
(II) VESA(0): 1280x1024@75Hz
(II) VESA(0): Manufacturer's mask: 0
(II) VESA(0): Supported Future Video Modes:
(II) VESA(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) VESA(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) VESA(0): Supported additional Video Mode:
(II) VESA(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) VESA(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) VESA(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) VESA(0): Serial No: U49314C21FTU
(II) VESA(0): Monitor name: DELL E173FP
(II) VESA(0): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 80 kHz, PixClock max 140 MHz
(II) VESA(0): EDID (in hex):
(II) VESA(0): 	00ffffffffffff0010ac0ba055544631
(II) VESA(0): 	310e010368221b78eecaf6a357479e23
(II) VESA(0): 	114f54a54b00714f8180010101010101
(II) VESA(0): 	010101010101302a009851002a403070
(II) VESA(0): 	1300520e1100001e000000ff00553439
(II) VESA(0): 	3331344332314654550a000000fc0044
(II) VESA(0): 	454c4c204531373346500a20000000fd
(II) VESA(0): 	00384b1f500e000a2020202020200073
(II) VESA(0): Using hsync ranges from config file
(II) VESA(0): Using vrefresh ranges from config file
(II) VESA(0): Printing DDC gathered Modelines:
(II) VESA(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) VESA(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) VESA(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) VESA(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) VESA(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) VESA(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) VESA(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) VESA(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) VESA(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) VESA(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) VESA(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 6a (800x600)
	ModeAttributes: 0x1b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 100
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
Mode: 102 (800x600)
	ModeAttributes: 0x1b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 100
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
Mode: 104 (1024x768)
	ModeAttributes: 0x1b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 128
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
Mode: 182 (320x200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 10d (320x200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 10e (320x200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
*Mode: 10f (320x200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 960
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 120 (320x200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 192 (320x240)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 193 (320x240)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 194 (320x240)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
*Mode: 195 (320x240)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 960
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 196 (320x240)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 203
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 1a2 (400x300)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 400
	XResolution: 400
	YResolution: 300
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 1a3 (400x300)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 800
	XResolution: 400
	YResolution: 300
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 1a4 (400x300)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 800
	XResolution: 400
	YResolution: 300
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
*Mode: 1a5 (400x300)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 1200
	XResolution: 400
	YResolution: 300
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 169
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 1a6 (400x300)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 1600
	XResolution: 400
	YResolution: 300
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 127
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 1b2 (512x384)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 512
	XResolution: 512
	YResolution: 384
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 1b3 (512x384)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 1024
	XResolution: 512
	YResolution: 384
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 169
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 1b4 (512x384)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 1024
	XResolution: 512
	YResolution: 384
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 169
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
*Mode: 1b5 (512x384)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 1536
	XResolution: 512
	YResolution: 384
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 112
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 1b6 (512x384)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 2048
	XResolution: 512
	YResolution: 384
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 84
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 1c2 (640x350)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 350
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 1c3 (640x350)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 350
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 145
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 1c4 (640x350)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 350
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 145
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
*Mode: 1c5 (640x350)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 1920
	XResolution: 640
	YResolution: 350
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 92
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 1c6 (640x350)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 350
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 72
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 100 (640x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 183 (640x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 127
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 184 (640x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 127
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
*Mode: 185 (640x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 1920
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 84
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 186 (640x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 63
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 101 (640x480)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 203
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 110 (640x480)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 101
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 111 (640x480)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 101
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
*Mode: 112 (640x480)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 1920
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 67
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 121 (640x480)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 52
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 103 (800x600)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 800
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 127
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 113 (800x600)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 67
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 114 (800x600)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 67
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
*Mode: 115 (800x600)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 2400
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 45
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 122 (800x600)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 33
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 105 (1024x768)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 1024
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 84
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 116 (1024x768)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 41
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 117 (1024x768)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 41
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
*Mode: 118 (1024x768)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 3072
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 27
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 123 (1024x768)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 4096
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 20
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 107 (1280x1024)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 1280
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 50
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 119 (1280x1024)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 24
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 11a (1280x1024)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 24
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
*Mode: 11b (1280x1024)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 3840
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 16
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 124 (1280x1024)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 5120
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 11
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 109 (132x25)
	ModeAttributes: 0xf
	WinAAttributes: 0x6
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0xb800
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 264
	XResolution: 132
	YResolution: 25
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
Mode: 10a (132x43)
	ModeAttributes: 0xf
	WinAAttributes: 0x6
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0xb800
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 264
	XResolution: 132
	YResolution: 43
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
Mode: 130 (132x44)
	ModeAttributes: 0xf
	WinAAttributes: 0x6
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0xb800
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 264
	XResolution: 132
	YResolution: 44
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0

(II) VESA(0): Total Memory: 1024 64KB banks (65536kB)
(II) VESA(0): DELL E173FP: Using hsync range of 30.00-70.00 kHz
(II) VESA(0): DELL E173FP: Using vrefresh range of 50.00-160.00 Hz
(II) VESA(0): Not using mode "1152x864" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x350" (no mode of this name)
(II) VESA(0): Not using built-in mode "512x384" (no mode of this name)
(II) VESA(0): Not using built-in mode "400x300" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
(--) VESA(0): Virtual size is 1280x1024 (pitch 1280)
(**) VESA(0): *Built-in mode "1280x1024"
(**) VESA(0): *Built-in mode "1024x768"
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "640x480"
(++) VESA(0): DPI set to (100, 100)
(II) VESA(0): Attempting to use 60Hz refresh for mode "1280x1024" (11b)
(II) VESA(0): Attempting to use 85Hz refresh for mode "1024x768" (118)
(II) VESA(0): Attempting to use 85Hz refresh for mode "800x600" (115)
(II) VESA(0): Attempting to use 85Hz refresh for mode "640x480" (112)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe9ef000 - 0xfe9effff (0x1000) MX[B]
	[5] -1	0	0xfeb7f900 - 0xfeb7f9ff (0x100) MX[B]
	[6] -1	0	0xfeb7fa00 - 0xfeb7fbff (0x200) MX[B]
	[7] -1	0	0xfeb7fc00 - 0xfeb7ffff (0x400) MX[B]
	[8] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[9] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[10] -1	0	0xea000000 - 0xea01ffff (0x20000) MX[B](B)
	[11] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[12] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000ddc0 - 0x0000ddff (0x40) IX[B]
	[21] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[22] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[23] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[24] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[25] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[26] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[27] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[30] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[31] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[32] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
	[33] -1	0	0x0000ed98 - 0x0000ed9f (0x8) IX[B](B)
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 2.0
(II) VESA(0): VESA VBE Total Mem: 65536 kB
(II) VESA(0): VESA VBE OEM: ATI RADEON VE
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) VESA(0): VESA VBE OEM Product: R100
(II) VESA(0): VESA VBE OEM Product Rev: 01.00
(==) VESA(0): Write-combining range (0xf0000000,0x4000000)
(II) VESA(0): virtual address = 0xb3a75000,
	physical address = 0xf0000000, size = 67108864
(II) VESA(0): VBESetVBEMode failed...Tried again without customized values.
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(**) Option "dpms"
(**) VESA(0): DPMS enabled
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc101"
(**) Generic Keyboard: XkbModel: "pc101"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9
SetClientVersion: 0 9
```

The above is with the vesa driver, but I can reconfigure my pci card to use only ati drivers.  I do not have the option to use radeon or r128 from dpkg-reconfigure xserver-xorg.  I have removed fglrx entirely from the drive since it does not work with rv100 cards.

---

### Post by ammut on 2008-02-04
Ok, now comes the outputs of the 'ati' driver.  I have followed the HOWTO located at:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

xorg.conf output:
```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc101"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
	Driver		"ati"
	BusID		"PCI:1:1:0"

EndSection

Section "Monitor"
	Identifier	"DELL E173FP"
	Option		"DPMS"


EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
	Monitor		"DELL E173FP"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Option		"AIGLX"		"true" 
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode 0666
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection
# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```

Xorg.0.log output:
```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux fci32 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686
Build Date: 18 January 2008
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Feb  4 20:25:05 2008
(==) Using config file: "/etc/X11/xorg.conf.failsafe"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Failsafe Monitor"
(**) |   |-->Device "Failsafe Device"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(II) Loader magic: 0x81e9800
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 8

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2570 card 1028,019d rev 02 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,2572 card 1028,019d rev 02 class 03,80,00 hdr 00
(II) PCI: 00:1d:0: chip 8086,24d2 card 1028,019d rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24d4 card 1028,019d rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,24de card 1028,019d rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24dd card 1028,019d rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24d0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24db card 1028,019d rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24d3 card 1028,019d rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24d5 card 1028,019d rev 02 class 04,01,00 hdr 00
(II) PCI: 01:01:0: chip 1002,5159 card 148c,2049 rev 00 class 03,00,00 hdr 00
(II) PCI: 01:08:0: chip 8086,1050 card 1028,019d rev 02 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:30:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfe900000 - 0xfeafffff (0x200000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xea000000 - 0xf7ffffff (0xe000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI: (0:2:0) Intel Corporation 82865G Integrated Graphics Controller rev 2, Mem @ 0xe0000000/27, 0xfeb80000/19, I/O @ 0xed98/3
(--) PCI:*(1:1:0) ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE] rev 0, Mem @ 0xf0000000/27, 0xfe9f0000/16, I/O @ 0xde00/8, BIOS @ 0xfea00000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xe8000000 from 0xe9ffffff to 0xe7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfe9ef000 - 0xfe9effff (0x1000) MX[B]
	[1] -1	0	0xfeb7f900 - 0xfeb7f9ff (0x100) MX[B]
	[2] -1	0	0xfeb7fa00 - 0xfeb7fbff (0x200) MX[B]
	[3] -1	0	0xfeb7fc00 - 0xfeb7ffff (0x400) MX[B]
	[4] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[5] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[6] -1	0	0xea000000 - 0xea01ffff (0x20000) MX[B](B)
	[7] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[8] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0x0000ddc0 - 0x0000ddff (0x40) IX[B]
	[10] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[11] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[12] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[13] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[14] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[15] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[16] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[18] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[19] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[20] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[21] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[1] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[2] -1	0	0x0000ed98 - 0x0000ed9f (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfe9ef000 - 0xfe9effff (0x1000) MX[B]
	[1] -1	0	0xfeb7f900 - 0xfeb7f9ff (0x100) MX[B]
	[2] -1	0	0xfeb7fa00 - 0xfeb7fbff (0x200) MX[B]
	[3] -1	0	0xfeb7fc00 - 0xfeb7ffff (0x400) MX[B]
	[4] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[5] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[6] -1	0	0xea000000 - 0xea01ffff (0x20000) MX[B](B)
	[7] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[8] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0x0000ddc0 - 0x0000ddff (0x40) IX[B]
	[10] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[11] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[12] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[13] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[14] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[15] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[16] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[18] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[19] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[20] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[21] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[1] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[2] -1	0	0x0000ed98 - 0x0000ed9f (0x8) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe9ef000 - 0xfe9effff (0x1000) MX[B]
	[5] -1	0	0xfeb7f900 - 0xfeb7f9ff (0x100) MX[B]
	[6] -1	0	0xfeb7fa00 - 0xfeb7fbff (0x200) MX[B]
	[7] -1	0	0xfeb7fc00 - 0xfeb7ffff (0x400) MX[B]
	[8] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[9] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[10] -1	0	0xea000000 - 0xea01ffff (0x20000) MX[B](B)
	[11] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[12] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000ddc0 - 0x0000ddff (0x40) IX[B]
	[18] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[19] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[20] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[21] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[22] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[23] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[24] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[27] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[28] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[29] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
	[30] -1	0	0x0000ed98 - 0x0000ed9f (0x8) IX[B](B)
(WW) "dbe" will not be loaded unless you've specified it to be loaded elsewhere.
(WW) "dri" will not be loaded unless you've specified it to be loaded elsewhere.
(WW) "glx" will not be loaded unless you've specified it to be loaded elsewhere.
(WW) "vbe" will not be loaded unless you've specified it to be loaded elsewhere.
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 01:01:0
(--) Chipset vesa found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe9ef000 - 0xfe9effff (0x1000) MX[B]
	[5] -1	0	0xfeb7f900 - 0xfeb7f9ff (0x100) MX[B]
	[6] -1	0	0xfeb7fa00 - 0xfeb7fbff (0x200) MX[B]
	[7] -1	0	0xfeb7fc00 - 0xfeb7ffff (0x400) MX[B]
	[8] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[9] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[10] -1	0	0xea000000 - 0xea01ffff (0x20000) MX[B](B)
	[11] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[12] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000ddc0 - 0x0000ddff (0x40) IX[B]
	[18] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[19] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[20] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[21] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[22] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[23] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[24] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[27] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[28] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[29] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
	[30] -1	0	0x0000ed98 - 0x0000ed9f (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe9ef000 - 0xfe9effff (0x1000) MX[B]
	[5] -1	0	0xfeb7f900 - 0xfeb7f9ff (0x100) MX[B]
	[6] -1	0	0xfeb7fa00 - 0xfeb7fbff (0x200) MX[B]
	[7] -1	0	0xfeb7fc00 - 0xfeb7ffff (0x400) MX[B]
	[8] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[9] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[10] -1	0	0xea000000 - 0xea01ffff (0x20000) MX[B](B)
	[11] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[12] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000ddc0 - 0x0000ddff (0x40) IX[B]
	[21] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[22] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[23] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[24] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[25] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[26] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[27] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[30] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[31] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[32] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
	[33] -1	0	0x0000ed98 - 0x0000ed9f (0x8) IX[B](B)
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 2.0
(II) VESA(0): VESA VBE Total Mem: 65536 kB
(II) VESA(0): VESA VBE OEM: ATI RADEON VE
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) VESA(0): VESA VBE OEM Product: R100
(II) VESA(0): VESA VBE OEM Product Rev: 01.00
(**) VESA(0): Depth 16, (--) framebuffer bpp 16
(==) VESA(0): RGB weight 565
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level 2
(II) VESA(0): VESA VBE DDC transfer in appr. 2 sec.
(II) VESA(0): VESA VBE DDC read successfully
(II) VESA(0): Manufacturer: DEL  Model: a00b  Serial#: 826692693
(II) VESA(0): Year: 2004  Week: 49
(II) VESA(0): EDID Version: 1.3
(II) VESA(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) VESA(0): Sync:  Separate
(II) VESA(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) VESA(0): Gamma: 2.20
(II) VESA(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) VESA(0): Default color space is primary color space
(II) VESA(0): First detailed timing is preferred mode
(II) VESA(0): redX: 0.640 redY: 0.340   greenX: 0.279 greenY: 0.619
(II) VESA(0): blueX: 0.140 blueY: 0.069   whiteX: 0.310 whiteY: 0.330
(II) VESA(0): Supported VESA Video Modes:
(II) VESA(0): 720x400@70Hz
(II) VESA(0): 640x480@60Hz
(II) VESA(0): 640x480@75Hz
(II) VESA(0): 800x600@60Hz
(II) VESA(0): 800x600@75Hz
(II) VESA(0): 1024x768@60Hz
(II) VESA(0): 1024x768@75Hz
(II) VESA(0): 1280x1024@75Hz
(II) VESA(0): Manufacturer's mask: 0
(II) VESA(0): Supported Future Video Modes:
(II) VESA(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) VESA(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) VESA(0): Supported additional Video Mode:
(II) VESA(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) VESA(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) VESA(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) VESA(0): Serial No: U49314C21FTU
(II) VESA(0): Monitor name: DELL E173FP
(II) VESA(0): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 80 kHz, PixClock max 140 MHz
(II) VESA(0): EDID (in hex):
(II) VESA(0): 	00ffffffffffff0010ac0ba055544631
(II) VESA(0): 	310e010368221b78eecaf6a357479e23
(II) VESA(0): 	114f54a54b00714f8180010101010101
(II) VESA(0): 	010101010101302a009851002a403070
(II) VESA(0): 	1300520e1100001e000000ff00553439
(II) VESA(0): 	3331344332314654550a000000fc0044
(II) VESA(0): 	454c4c204531373346500a20000000fd
(II) VESA(0): 	00384b1f500e000a2020202020200073
(II) VESA(0): Using EDID range info for horizontal sync
(II) VESA(0): Using EDID range info for vertical refresh
(II) VESA(0): Printing DDC gathered Modelines:
(II) VESA(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) VESA(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) VESA(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) VESA(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) VESA(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) VESA(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) VESA(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) VESA(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) VESA(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) VESA(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) VESA(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 6a (800x600)
	ModeAttributes: 0x1b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 100
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
Mode: 102 (800x600)
	ModeAttributes: 0x1b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 100
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
Mode: 104 (1024x768)
	ModeAttributes: 0x1b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 128
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
Mode: 182 (320x200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 10d (320x200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
*Mode: 10e (320x200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 10f (320x200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 960
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 120 (320x200)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 192 (320x240)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 193 (320x240)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
*Mode: 194 (320x240)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 195 (320x240)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 960
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 196 (320x240)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 203
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 1a2 (400x300)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 400
	XResolution: 400
	YResolution: 300
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 1a3 (400x300)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 800
	XResolution: 400
	YResolution: 300
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
*Mode: 1a4 (400x300)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 800
	XResolution: 400
	YResolution: 300
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 1a5 (400x300)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 1200
	XResolution: 400
	YResolution: 300
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 169
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 1a6 (400x300)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 1600
	XResolution: 400
	YResolution: 300
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 127
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 1b2 (512x384)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 512
	XResolution: 512
	YResolution: 384
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 1b3 (512x384)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 1024
	XResolution: 512
	YResolution: 384
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 169
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
*Mode: 1b4 (512x384)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 1024
	XResolution: 512
	YResolution: 384
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 169
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 1b5 (512x384)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 1536
	XResolution: 512
	YResolution: 384
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 112
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 1b6 (512x384)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 2048
	XResolution: 512
	YResolution: 384
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 84
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 1c2 (640x350)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 350
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 1c3 (640x350)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 350
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 145
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
*Mode: 1c4 (640x350)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 350
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 145
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 1c5 (640x350)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 1920
	XResolution: 640
	YResolution: 350
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 92
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 1c6 (640x350)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 350
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 72
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 100 (640x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 183 (640x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 127
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
*Mode: 184 (640x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 127
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 185 (640x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 1920
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 84
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 186 (640x400)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 63
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 101 (640x480)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 203
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 110 (640x480)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 101
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
*Mode: 111 (640x480)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 101
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 112 (640x480)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 1920
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 67
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 121 (640x480)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 52
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 103 (800x600)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 800
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 127
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 113 (800x600)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 67
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
*Mode: 114 (800x600)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 67
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 115 (800x600)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 2400
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 45
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 122 (800x600)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 33
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 105 (1024x768)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 1024
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 84
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 116 (1024x768)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 41
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
*Mode: 117 (1024x768)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 41
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 118 (1024x768)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 3072
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 27
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 123 (1024x768)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 4096
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 20
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 107 (1280x1024)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 1280
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 50
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 119 (1280x1024)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 24
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
*Mode: 11a (1280x1024)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 24
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 11b (1280x1024)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 3840
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 24
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 16
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 124 (1280x1024)
	ModeAttributes: 0xbb
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc00050fd
	BytesPerScanline: 5120
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 11
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
Mode: 109 (132x25)
	ModeAttributes: 0xf
	WinAAttributes: 0x6
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0xb800
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 264
	XResolution: 132
	YResolution: 25
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
Mode: 10a (132x43)
	ModeAttributes: 0xf
	WinAAttributes: 0x6
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0xb800
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 264
	XResolution: 132
	YResolution: 43
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
Mode: 130 (132x44)
	ModeAttributes: 0xf
	WinAAttributes: 0x6
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0xb800
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 264
	XResolution: 132
	YResolution: 44
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0

(II) VESA(0): Total Memory: 1024 64KB banks (65536kB)
(II) VESA(0): Failsafe Monitor: Using hsync range of 31.00-80.00 kHz
(II) VESA(0): Failsafe Monitor: Using vrefresh range of 56.00-75.00 Hz
(II) VESA(0): Not using built-in mode "1280x1024" (width too large for virtual size)
(II) VESA(0): Not using built-in mode "1024x768" (width too large for virtual size)
(II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x350" (no mode of this name)
(II) VESA(0): Not using built-in mode "512x384" (no mode of this name)
(II) VESA(0): Not using built-in mode "400x300" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
(--) VESA(0): Virtual size is 800x600 (pitch 800)
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0):  Built-in mode "640x480"
(**) VESA(0): Display dimensions: (340, 270) mm
(**) VESA(0): DPI set to (59, 56)
(II) VESA(0): Attempting to use 72Hz refresh for mode "800x600" (114)
(II) VESA(0): Attempting to use 73Hz refresh for mode "640x480" (111)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe9ef000 - 0xfe9effff (0x1000) MX[B]
	[5] -1	0	0xfeb7f900 - 0xfeb7f9ff (0x100) MX[B]
	[6] -1	0	0xfeb7fa00 - 0xfeb7fbff (0x200) MX[B]
	[7] -1	0	0xfeb7fc00 - 0xfeb7ffff (0x400) MX[B]
	[8] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[9] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[10] -1	0	0xea000000 - 0xea01ffff (0x20000) MX[B](B)
	[11] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[12] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000ddc0 - 0x0000ddff (0x40) IX[B]
	[21] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[22] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[23] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[24] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[25] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[26] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[27] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[30] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[31] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[32] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B](B)
	[33] -1	0	0x0000ed98 - 0x0000ed9f (0x8) IX[B](B)
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 2.0
(II) VESA(0): VESA VBE Total Mem: 65536 kB
(II) VESA(0): VESA VBE OEM: ATI RADEON VE
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) VESA(0): VESA VBE OEM Product: R100
(II) VESA(0): VESA VBE OEM Product Rev: 01.00
(==) VESA(0): Write-combining range (0xf0000000,0x4000000)
(II) VESA(0): virtual address = 0xb3a5a000,
	physical address = 0xf0000000, size = 67108864
(II) VESA(0): VBESetVBEMode failed...Tried again without customized values.
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(**) Option "dpms"
(**) VESA(0): DPMS enabled
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc101"
(**) Generic Keyboard: XkbModel: "pc101"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9
SetClientVersion: 0 9
```

glxinfo output:
```
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 16 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x39 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

```

I followed the instructions to the letter on the above community documentation (for the second time) and was unable to get this to work.  I was booted into low graphics mode when I issued a startx command and again, nothing seems to work.

---

### Post by ammut on 2008-02-05
Ok so I've had a breakthrough! I have gotten my setup to recognize the pci card and use the ati driver.  However, now it is running extremely slow, even when I type or when it is displaying text.  Starting new programs is a pain.  They take 5x the amount of time to load than they used to on my 8MB onboard VGA chipset.

I also still do not have direct rendering enabled.  I have looked for options to turn on that may remedy these situations and have modified my xorg.conf file a few times now.

Xorg.conf:
```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection


#Section "Files"
#	Load "dri"
#	Load "glx"
#	Load "dbe"
#	Load "vbe"
#EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc101"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
	Driver		"ati"
	BusID		"PCI:1:1:0"	
	Option		"XAANoOffscreenPixmaps"
	Option		"RenderAcceleration"	"true"
	#VideoRAM	131072	
EndSection

Section "Monitor"
	Identifier	"DELL E173FP"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
	Monitor		"DELL E173FP"
	DefaultDepth	24
	SubSection "Display"
		Virtual		1024 768	
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Option		"AIGLX"		"true" 
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode 0666
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection
# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"

```

Can anyone out there help me get direct rendering enabled? I would really like to be able to play 3d games! Any help is much appreciated as usual :lolflag:

---


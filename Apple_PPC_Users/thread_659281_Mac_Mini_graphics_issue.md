---
title: "Mac Mini graphics issue"
date: 2008-01-05
forum: Apple PPC Users
---

### Post by fixerdave on 2008-01-05
I have a couple of graphics issues, probably related, that I can't get past: during boot, the splash screen is "out of range" on my monitor and won't display.  The same thing happens when some full-screen (I assume) 3D graphics applications start.  The monitor just goes black except for displaying "out of range".  

I'm wondering if anyone might have some pointers on where I should look.



Background:

I'm running Feisty on a ppc Mac Mini, and I'm very, very happy with it.  I'm using VGA to my monitor, not HDMI.    

I expect the problem is that I'm running my video through a monitor switch box.  So, this isn't any kind of bug but just an unusual configuration that is causing problems.

2D graphics are great. I've used: 
  [COLOR="Red"]sudo dpkg-reconfigure xserver-xorg -phigh[/COLOR]
with the ATI driver to choose my available resolutions.  My monitor is capable of  1680x1050 and that's the highest I've chosen.

Basically, everything is fine except during boot, I don't get the splash screen, the monitor reports that the signal is "out of range".  I also get the same report when I try to run some 3D graphics apps. I expect both issues are the result of the system not having the correct monitor parameters and wrongly assuming that the higher-res settings are okay. My assumption is that the monitor switch box is reporting its available range rather than passing through the monitor's.

glxgears runs fine.

I'm not dual-booting (well, I still have OS-X on a firewire drive - using the Option key to boot from it when I want, but the local drive is all Ubuntu)

On boot:  first screen is text, probably at around 1200x800 or so, the next is text at about 640x480, then it goes out of range.  Windowed 3D apps are fine, like glxgears, but some apps just switch to "out of range," leaving me to guess at how to exit, or forcing me to restart X.

So, where can I tell Ubuntu what the valid settings are for my monitor?  I don't really care about the splash screen, but the 3D apps would be nice.

    David...


P.S.  I'm a tech by profession, old-school Windows expert, but am somewhat new to Linux and Ubuntu.  BTW, after using MS DOS/Windows (every version, from the time DOS worked with a serial terminal) and OS-X, I have to say that Ubuntu is the future of computing.


glxinfo (just in case it will help):  

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 1x TCL
OpenGL version string: 1.3 Mesa 6.5.2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_histogram, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_ATI_fragment_shader, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x4b 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

---

### Post by BladeMelbourne on 2008-01-05
I'm running Gutsy on my Mac Mini.

I disabled the splash screen when my computer boots.

sudo nano /etc/yaboot.conf
I altered my 'append' value as below:

```
image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
        append="video=ofonly nosplash"
```
After modifying this file execute: sudo ybin -v

As for the full screen 3D applications, I assume they may not be using your settings from /etc/X11/xorg.conf - or you may not have specified valid 'HorizSync' or 'VertRefresh' in the 'Monitor' section of this file. You can edit this file using: sudo nano /etc/X11/xorg.conf - although be careful as you may stop xwindows from loading.

HTH.

---

### Post by fixerdave on 2008-01-06
Hi,  thanks for the reply.

I took your advice and did some research on the xorg.conf monitor section and discovered that I had the horizontal refresh range with a bottom value too low.  So, now my 3D graphics at least show, though they are slow, so I still have a bit of work to do.

The yaboot conf file mod made no difference, well at least no difference that I could see.  But, like I said at the start, I don't really need to see the splash screen.

Side note: I made a stupid typo in the conf file and managed to lock myself out of the system.  X11 crashed out but it wouldn't dump me to terminal mode.  How do you get yaboot to boot without X11?  I had to use the Live CD to get access to the HD and fix my mistake.  Anyway, after I figure out why I'm getting 1.5fps in 3D, I'll work on learning yaboot.

Thanks again,

     David...

---

### Post by BladeMelbourne on 2008-01-06
Hi Dave,

In /etc/yaboot.conf, I have added the following:

```
image=/boot/vmlinux
        label=LinuxText
        read-only
        initrd=/boot/initrd.img
        append="video=ofonly single"
```

If I break my xorg conf, I can type "LinuxText" at the boot menu and it will boot to the command line.
It's very important to run 'sudo ybin -v' after modifying yaboot.conf, otherwise the boot menu will not be updated.

When you start glxgears from a terminal console (while xwindows is running), what framerate are you getting?

For your reference, I have added my own /etc/X11/xorg.conf below:
```
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"macintosh"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:lwin_switch"
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


Section "Device"
	Identifier	"ATI Technologies Inc RV280 [Radeon 9200]"
	Driver		"ati"
	BusID		"PCI:0:16:0"
	Option		"UseFBDev"		"False"
	Option 		"PanelSize" 		"1280x1024"
	Option          "DMAForXv"       	"true"
	Option 		"AGPMode" 				"4"
	Option 		"EnablePageFlip" 		"true"
	Option 		"ColorTiling" 			"1"
	Option         "RenderAccel"           "True"
	Option 		"AGPFastWrite" 			"True" #Can hard lock machine
EndSection

Section "Monitor"
	Identifier	"Philips 190S"
	Option		"DPMS"
	HorizSync	30-82
	VertRefresh	56-76
	Option 		"PreferredMode"  	"1280x1024" #not used in old driver?
	Modeline 	"1280x1024" 135.00 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync #Good
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV280 [Radeon 9200]"
	Monitor		"Philips 190S"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024"
		Virtual         1280 1024
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Option          "AIGLX"			"True"
EndSection

Section "Module"
	Load	"i2c"
	Load	"ddc"
	Load	"dri"
	Load	"dbe"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
EndSection

Section "Extensions"
	Option			"Composite"		"Disable"
	Option			"XINERAMA"		"Disable"
EndSection
```

Note that my screen res (1280x1024) is less than yours, so adjust those lines as necessary.

I remember my glxgears framerate being between 750 and 830, however today it is 1180 fps.

I couldn't run Gutsy with the Gutsy ati driver, so I'm using the one from Feisty (xserver-xorg-video-ati_6.6.3-2_powerpc).

- Mike -

---

### Post by flatblack on 2008-01-22
I installed Ubuntu 7.10 from 7.04 .. It boots fine, but gnome wont load (atleast thats what I think).

It has to be some sort of video driver issue, but I have no idea what (or where to get the error messages..)  When I type gdm restart, the screen blinks a couple of times and kicks me back to the command prompt..

I was curious about you saying you were using the 7.04 driver?  How do I do that?  Any advice on how to get this working?

Thanks!

---

### Post by BladeMelbourne on 2008-01-22
My 1st post in this thread should explain it:
[http://ubuntuforums.org/showthread.php?t=674351](http://ubuntuforums.org/showthread.php?t=674351)

Please let me know if you need more info.

---


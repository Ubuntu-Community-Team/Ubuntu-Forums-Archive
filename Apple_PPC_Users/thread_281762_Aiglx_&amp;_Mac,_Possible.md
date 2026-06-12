---
title: "Aiglx &amp; Mac, Possible??"
date: 2006-10-21
forum: Apple PPC Users
---

### Post by sbentzen on 2006-10-21
is aiglx and macintosh hardware possible, because i have an ati 9200 mobility and was wondering because it didn't start up with the live cd. EDIT:  I realized my error, i am infact not a testing user, just a normal user who has upgraded the thing, not a tester, just got the RC and was wondering if aiglx would work with mac hardware.

---

### Post by techrush on 2006-10-22
it should work with that card using the open source r200 driver. although im not %100 sure on this. if you can find a tutorial on using the open source ATI drivers to make aiglx work then it should apply to your ibook as well.

---

### Post by ssam on 2006-10-22
if you are running edgy just install compiz and compiz-gnome in synaptic (i think its in the universe). and run

```
compiz --indirect-rendering --strict-binding --replace gconf & gnome-window-decorator &
```

aiglx is installed and running by default (if your graphics card supports it).

the only trouble is that [https://launchpad.net/distros/ubuntu/+source/compiz/+bug/58373](https://launchpad.net/distros/ubuntu/+source/compiz/+bug/58373) has not been fixed so everything will look blue on powerpc.

---

### Post by ssam on 2006-10-22
there is now an upstream fix. i built a patched package of xorg-server. see the bug report for more details

[http://tygier.co.uk/pub/xserver-xorg-core_1.1.1-0ubuntu12_powerpc.deb](http://tygier.co.uk/pub/xserver-xorg-core_1.1.1-0ubuntu12_powerpc.deb)

---

### Post by anders_gud on 2006-10-23
> **ssam said:**
> there is now an upstream fix. i built a patched package of xorg-server. see the bug report for more details

[http://tygier.co.uk/pub/xserver-xorg-core_1.1.1-0ubuntu12_powerpc.deb](http://tygier.co.uk/pub/xserver-xorg-core_1.1.1-0ubuntu12_powerpc.deb)

Great!
Works here on a Tibook 1Ghz (just dist-upgraded), but slow as hell...
I'm new to compiz, are there any common pitfalls?

here is my glxinfo:
 
name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x4b
display: :0  screen: 0
direct rendering: Yes
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 1x TCL
OpenGL version string: 1.3 Mesa 6.5.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_histogram, 
    GL_EXT_packed_pixels, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_stencil_wrap, GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_blend_equation_separate, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATI_fragment_shader, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

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

the second line is mysterious... libGL warning

---

### Post by eidex on 2006-10-23
forget about that error message, in another forum they posted its just a cosmetic problem, i'll try to find the link and post it later. 

i use beryl on my ibook g4 1,2ghz(ati 9200) and it runs quite smooth, i did some tweaks on my xorg.config and post them later. the only thing that i dont like about compiz is that the fan runs even more often than it did with metacity

greetings


btw: thanks ssam for the patched package, i will try it out later and see if it works (i was running on 16bit color depth the last days to get rid of the blue colors)

---

### Post by sbentzen on 2006-10-23
thank you, could you please post the patch, and if beryl works, i like that better than compiz, it just sounds better

---

### Post by AlphaMack on 2006-10-26
> **ssam said:**
> if you are running edgy just install compiz and compiz-gnome in synaptic (i think its in the universe). and run

```
compiz --indirect-rendering --strict-binding --replace gconf & gnome-window-decorator &
```

aiglx is installed and running by default (if your graphics card supports it).

the only trouble is that [https://launchpad.net/distros/ubuntu/+source/compiz/+bug/58373](https://launchpad.net/distros/ubuntu/+source/compiz/+bug/58373) has not been fixed so everything will look blue on powerpc.

Now how do I undo that and get my windows to look normal again?  ( uninstalled compiz)

EDIT:  Scratch that.  I got it.

---

### Post by bogoliubov on 2006-10-26
> **eidex said:**
> forget about that error message, in another forum they posted its just a cosmetic problem, i'll try to find the link and post it later. 

i use beryl on my ibook g4 1,2ghz(ati 9200) and it runs quite smooth, i did some tweaks on my xorg.config and post them later. the only thing that i dont like about compiz is that the fan runs even more often than it did with metacity

greetings


btw: thanks ssam for the patched package, i will try it out later and see if it works (i was running on 16bit color depth the last days to get rid of the blue colors)


I'm very much interested in those tweaks that you did. I installed the patched xserver, but compiz is very slow on my iBook G4 1.2GHz.

What's the difference between aiglx and xgl; and what are the difference between compiz and beryl?

---

### Post by eidex on 2006-10-26
add the following lines to your sources.list:

#Mental-ppc
deb [http://mental-ppc.tuxfamily.org/dists](http://mental-ppc.tuxfamily.org/dists) edgy-mppc all 
#deb-src [http://mental-ppc.tuxfamily.org/dists](http://mental-ppc.tuxfamily.org/dists) edgy-mppc all

in this repository you will find beryl, ( you can browse ist here: [http://mental-ppc.tuxfamily.org/dists/dists/edgy-mppc/all/)](http://mental-ppc.tuxfamily.org/dists/dists/edgy-mppc/all/)), just apt-get beryl

i think you need to install compiz and compiz-gnome too and then just try to start beryl-manager, if its still slow then i think its because of your xorg.config, i will post mine on monday, i dont have access to my installation earlier!

you dont need xgl, it runs with the installed aiglx, i dont know the differences between compiz and beryl, but speedwise there is a huge difference on my ibook!

dont forget to install the patched xserver from ssam, otherwise everything is ugly blue!

---

### Post by bogoliubov on 2006-10-26
> **eidex said:**
> add the following lines to your sources.list:

#Mental-ppc
deb [http://mental-ppc.tuxfamily.org/dists](http://mental-ppc.tuxfamily.org/dists) dapper-mppc all 
#deb-src [http://mental-ppc.tuxfamily.org/dists](http://mental-ppc.tuxfamily.org/dists) dapper-mppc all

in this repository you will find beryl, ( you can browse ist here: [http://mental-ppc.tuxfamily.org/dists/dists/edgy-mppc/all/)](http://mental-ppc.tuxfamily.org/dists/dists/edgy-mppc/all/)), just apt-get beryl

i think you need to install compiz and compiz-gnome too and then just try to start beryl-manager, if its still slow then i think its because of your xorg.config, i will post mine on monday, i dont have access to my installation earlier!

you dont need xgl, it runs with the installed aiglx, i dont know the differences between compiz and beryl, but speedwise there is a huge difference on my ibook!

dont forget to install the patched xserver from ssam, otherwise everything is ugly blue!

Ok, it works. And it's much faster than compiz. But it's still rather slow. Can I reduce the amount of effects somehow?

Also, I saw that there are a new xserver available throught apt. Should I donwload this, or wait (since I have a patched version)?


Thank's alot for your help, I'm looking forward to seeing your xorg.conf!

---

### Post by eidex on 2006-10-26
i think the mental repositories offer the patched xserver too, so let apt-get install it to find out if it still works, if not you can install ssams version again.

about speed:

i think we have the same model so i think it depends on your xorg.config, as i said i cant post it now but try to modify it as others did for ati/beryl (on x86) and we can compare our modifications on monday!

---

### Post by bogoliubov on 2006-10-26
> **eidex said:**
> i think the mental repositories offer the patched xserver too, so let apt-get install it to find out if it still works, if not you can install ssams version again.

about speed:

i think we have the same model so i think it depends on your xorg.config, as i said i cant post it now but try to modify it as others did for ati/beryl (on x86) and we can compare our modifications on monday!

I already have some modifications, but I just want to make sure that what I have put in will really make things faster (and to the other way round).

Have a nice weekend and thank's alot for your help so far!

---

### Post by anders_gud on 2006-10-27
Got beryl working and it's indeed faster than compiz, but I suspect there are optimizations and tweaks needed to get it work properly.
FI. VLC, Blender and other apps relying on Xv and opengl do not seem to be compatible with Beryl. I've also had some mysterious hard crashes I think is related to either AIGLX, Beryl or Emerald.
The best thing about this is the accelerated X over remote, brilliant!
Post your experiences!

---

### Post by mattl on 2006-10-30
Has anyone had any success with Beryl on PowerBook G4 1.67Ghz?

---

### Post by adibudeen on 2006-10-30
I had Beryl running on my iBook G4, but there was just one problem that I couldn't stand:

In Firefox, Konqueror, or any other browser, the scrolling was painfully slow, and it would cause the cpu fan to come on full blast (which is loud on the iBook).

As much as I surf the web, I'd rather have fast scrolling than eye candy.  It's unfortunate, because I do like it and don't find the effects themselves to be that slow at all.

---

### Post by ADBlues on 2006-10-30
Please forget my ignorance but now that I've installed the beryl packages how can I start beryl?
I believe I'm missing something...

Thanks
         Alex

---

### Post by cloudaj on 2006-10-30
you start beryl with:
 beryl-manager &

I seemed to get everything working, and beryl launches, but i lose all window decorations.  I've sporadically seen this issue mentioned around the web, but I haven't found a working cure yet.  I've gotten to the point where the window decorations appear, but then they disappear right away.  (This is a compiz error, not specific to beryl).  Wondering if anyone can help, I can post my xorg.conf file if need be, and my machine is a powerbook G4, 15", with a mobility radeon 9700 using the opensource ati driver.  (which was installed by default?).

---

### Post by ADBlues on 2006-10-30
> **cloudaj said:**
> you start beryl with:
 beryl-manager &

I seemed to get everything working, and beryl launches, but i lose all window decorations.  I've sporadically seen this issue mentioned around the web, but I haven't found a working cure yet.  I've gotten to the point where the window decorations appear, but then they disappear right away.  (This is a compiz error, not specific to beryl).  Wondering if anyone can help, I can post my xorg.conf file if need be, and my machine is a powerbook G4, 15", with a mobility radeon 9700 using the opensource ati driver.  (which was installed by default?).

I've the same machine but when I launch beryl I got a lot of errors and I lost some portions of the windows:

 libGL warning: 3D driver claims to not support visual 0x4b
compiz.real: SmcOpenConnection failed: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
libGL warning: 3D driver claims to not support visual 0x4b
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No manageable screens found on display :0.0

I'll appreciate if you could post your xorg.conf... I believe this will be useful.

  Thanks

---

### Post by digbys on 2006-10-30
I finally managed to get beryl up w/o the white screen problem. Seems I had to reduce the display bit depth in xorg.conf from 24 to 16. As mentioned vlc & others won't work in beryl. I'm running on a mac mini/ati9200 and the effects are just a tad slow for it to be workable on a daily basis.

---

### Post by bogoliubov on 2006-10-31
> **eidex said:**
> i think the mental repositories offer the patched xserver too, so let apt-get install it to find out if it still works, if not you can install ssams version again.

about speed:

i think we have the same model so i think it depends on your xorg.config, as i said i cant post it now but try to modify it as others did for ati/beryl (on x86) and we can compare our modifications on monday!

Hello. Here's parts from my xorg.xonf. Don't know exactly what is important but I guess these parts are:

Section "Module"
    Load    "i2c"
    Load    "bitmap"
    Load    "ddc"
    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "type1"
    Load    "vbe"
    Load    "dbe"
EndSection

Section "Device"
    Identifier  "ATI Technologies, Inc. M9+ 5C63 [Radeon Mobility 9000 (AGP)]"
    Driver      "radeon"
    BusID       "PCI:0:16:0"
    Option      "UseFBDev"      "true"
    Option      "DRI" "true"
    Option      "ColorTiling" "on"
    Option      "AccelMethod" "EXA"
    Option      "XAANoOffscreenPixmaps"
    Option      "AGPMode" "4"
    Option      "AGPFastWrite" "on"
    Option      "ColorTiling"   "on"
    Option      "RenderAccel" "true"
    Option      "UseFWPLL" "true"
    Option      "EnableDepthMoves" "true"
    Option      "BackingStore" "true"
    Option      "DynamicClocks" "on"
# Dual screen stuff
    Option      "CRT2Position" "RightOf"
    Option      "MergedFB" "true"
#   Option     "MetaModes"     "1024x768-1280x1024 1024x768"
#   Option      "MergedNonRectangular" "true"
### Cloning
# Option      "CloneMode" "1280x1024"
EndSection


Section "ServerLayout"
    Identifier  "Default Layout"
    Screen      "Default Screen"
    InputDevice "Generic Keyboard"
    InputDevice "Configured Mouse"
    InputDevice "Synaptics Touchpad"
    Option  "MergedFB" "On"
EndSection

Section "DRI"
    Mode    0666
EndSection

---

### Post by eidex on 2006-10-31
sorry for the delay, here is my xorg.conf! dont ask me why it its the way it is, i tried out some parameters a few weeks ago and benchmarked them, and this was the config with the best result.

my window effects are very smooth, but i head to replace the standard minimize effect which was a bit slow with the zoom effect which looks better and runs perfect.

i also dont know how good it runs with other applications like watching dvds because i just used the machine for internet and mail to test edgy.

hope that helps!

btw, i load beryl with the gnome-session-manager, so i dont have problems with windows without windowmangaer, if you load it later applications like firefox have to be restarted to have a windowmanager

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. M9+ 5C63 [Radeon Mobility 9000 (AGP)]"
	Driver		"radeon"
	BusID		"PCI:0:16:0"
#	Option 		"AGPMode" "4"
#	Option		"UseFBDev"		"true"
#	Option      	"XAANoOffscreenPixmaps" "true"
#	Option      	"DRI"     "true"
#	Option      	"EnablePageFlip" "On"
#	Option      	"CloneMode" "1024x768"
	
        Option          "XAANoOffscreenPixmaps"         
        Option          "AccelMethod"                   "XAA"   
        Option          "AGPMode"                       "4"    
        Option          "AGPFastWrite"                  "True"
        Option          "EnablePageFlip"                "True"  # Artefakte?
        Option          "ColorTiling"                   "1"     
        Option          "UseInternalAGPGART"            "no"    
        Option          "backingstore"                  "true"
        Option          "AllowGLXWithComposite"         "true"
        Option          "RenderAccel"                   "true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. M9+ 5C63 [Radeon Mobility 9000 (AGP)]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
	Option          "AIGLX" "true"
EndSection

Section "DRI"
	Mode	0666
        Group 	0
EndSection

			    
Section "Extensions"
	Option         "Composite"   "Enable"
EndSection
					 
#Section "Device"
#    Option      "XAANoOffscreenPixmaps" "true"
#    Option      "DRI"     "true"
#EndSection

```

---

### Post by ADBlues on 2006-10-31
I've tried the various config posted but none helped.
When I to launch Beryl-manager I always get a blue background with white squares (the opened windows) and no writings or icons.
I'm able to blind navigate the menus so xorg does not crash.

In this case I get these errors:

```
alex@kirk-ux:~$ Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
libGL warning: 3D driver claims to not support visual 0x4b
beryl: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
Initiating splash
beryl: water: GL_ARB_fragment_program is missing
X connection to :0.0 broken (explicit kill or server shutdown).

```


If, from beryl-manager I choose compiz as window manager, the screen remains readable but I lost the windows borders and the ability to move\close\enlarge them.
In this case I get these errors:

```
alex@kirk-ux:~$ Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.
libGL warning: 3D driver claims to not support visual 0x4b
compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No manageable screens found on display :0.0

```

My card is an ATI Radeon 9600 M10 (MV350)...
When I launch glxinfo the card is claimed capable of direct rendering and I can see the gears spinning (slowly but smoothly) when I run glxgears.
 
I'm very disappointed, I hope someone could help me.

  Thanks in advance.

---

### Post by eidex on 2006-10-31
is there any way of improving the speed of scrolling in firefox with beryl enabled, its awfully slow compared to metacity?

edit:

they are working on it: [http://bugs.beryl-project.org/ticket/183]("http://bugs.beryl-project.org/ticket/183")

---

### Post by bogoliubov on 2006-10-31
> **eidex said:**
> sorry for the delay, here is my xorg.conf! dont ask me why it its the way it is, i tried out some parameters a few weeks ago and benchmarked them, and this was the config with the best result.

my window effects are very smooth, but i head to replace the standard minimize effect which was a bit slow with the zoom effect which looks better and runs perfect.

i also dont know how good it runs with other applications like watching dvds because i just used the machine for internet and mail to test edgy.

hope that helps!

btw, i load beryl with the gnome-session-manager, so i dont have problems with windows without windowmangaer, if you load it later applications like firefox have to be restarted to have a windowmanager


[/CODE]


Thanks alot! I already had some of the options that you use, but I added the rest. Except for XAA, I read on the radeon manpage that one should use EXA...  Anyhow it's faster now.

BUT, Now I get really wide desktop! Resolution became 800x600 at first, but I removed the 800x600 option and now I have 1024x768, but it's really wide. What can I do about this? I have no idea which line in xorg.conf that causes this...

---

### Post by eidex on 2006-10-31
dear bogoliubov,

i have no idea what you meen with "wide desktop"...

---

### Post by bogoliubov on 2006-10-31
> **eidex said:**
> dear bogoliubov,

i have no idea what you meen with "wide desktop"...

Sorry, a bit difficult to explain I guess. My resolution is 1024x768, but the desktop is much larger. So, some windows end up out of my reach. When I switch between desktops (by spinning the cube), I can see what's on the "non-reachable" part of the desktops, but that's it. 

Does that make it more clear? I have no idea why it's like this, but it's really annoying.

---

### Post by ADBlues on 2006-11-01
I've reinstalled Edgy from scratch but Compiz (or Beryl, it doesn't matter) won't work with aiglx.

When I launch compiz the screen become cyan with white squares.

So no success...
I hope someone could help me!

   Thanks in advance.

Alex

---

### Post by bogoliubov on 2006-11-02
> **ADBlues said:**
> I've reinstalled Edgy from scratch but Compiz (or Beryl, it doesn't matter) won't work with aiglx.

When I launch compiz the screen become cyan with white squares.

So no success...
I hope someone could help me!

   Thanks in advance.

Alex

Sorry mate, no idea what could cause this. But did you install the patched xorg (as discussed on this thread)? That solved my problem with the blue desktop.

---

### Post by ADBlues on 2006-11-02
> **bogoliubov said:**
> Sorry mate, no idea what could cause this. But did you install the patched xorg (as discussed on this thread)? That solved my problem with the blue desktop.

Yes,
I've installed the patched xorg also.
BTW, my defect does not look like the "classical" blue-ish screen but just a cyan background with completely white squares in place of the windows and grey shadows in place of menus and boxes. I'm sorry but I don't know how to generate screnshots to show you.
The Xserver is operative (not crashed) and I can operate it despite "blindly".
I've no experience in that but it looks like a lack of resources or a not completely supported video-card even if other people have the same hardware working flawlessy.

Thanks anyway :-)

---

### Post by fuoco on 2006-11-03
ADBlues: I have the same problem as you do. My machine is an iBook 14'' 1.42 Ghz with radeon 9550.
glxinfo claims direct rendering works, but glxgears gives me around 25-30FPS only, and takes 100% of cpu when running.
With beryl I also get the white-blank windows, and then too cpu is 100% (careful not to burn the cpu as therm_adt7460 is not autoloaded and fans won't start).

I don't know what's the problem we have. I know the card should work ok with the r300 driver, I had it working a long time ago in gentoo. I believe first thing is to solve the 3D accelleration problem and then check what's going on with beryl.

---

### Post by ADBlues on 2006-11-03
How to get the measurement of teh FPS with glxgears?
I just got some writings in the console.

---

### Post by fuoco on 2006-11-03
> **ADBlues said:**
> How to get the measurement of teh FPS with glxgears?
I just got some writings in the console.

use 'glxgears -printfps'

It is strange because I see here people who have the same system and got it working

---

### Post by bogoliubov on 2006-11-04
> **fuoco said:**
> ADBlues: I have the same problem as you do. My machine is an iBook 14'' 1.42 Ghz with radeon 9550.
glxinfo claims direct rendering works, but glxgears gives me around 25-30FPS only, and takes 100% of cpu when running.
With beryl I also get the white-blank windows, and then too cpu is 100% (careful not to burn the cpu as therm_adt7460 is not autoloaded and fans won't start).

I don't know what's the problem we have. I know the card should work ok with the r300 driver, I had it working a long time ago in gentoo. I believe first thing is to solve the 3D accelleration problem and then check what's going on with beryl.

I guess you already knew this, but you can always add the therm_adt7460 module to /etc/modules. That way, it'll start when you boot the computer.

As for the problem with hardware acceleration, have a look at your xorg.conf and compare with what was written on earlier pages in this thread. But perhaps you've already tried this. In that case, I don't know what else to do. Perhaps check the output of glxinfo and see if there is something that won't work.

---

### Post by cloudaj on 2006-11-04
Alright, so now that i've been messing with this all night, i've finally realized that for some reason, direct rendering is being reported as not working on my machine.  Woohoo wasting my time!  

However, I am not sure exactly why its not enabled.  I'll post my Xorg.conf file and maybe someone will have an answer for me.  Otherwise though, it's spitting out good results on glxgears, and glxgears isn't reporting any errors.  Although, my current state with Beryl is that it crashes my xserver after a few seconds of the load screen being up.

Anyways, here it is:

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load 	"dbe"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Driver		"radeon"
	BusID		"PCI:0:16:0"
	Option "DRI" "true"
	Option "EnablePageFlip" "true"
	Option "backingstore" "true"
	Option "AllowGLXWithComposite" "true"
	Option "RenderAccel" "true"
	Option "XAANoOffscreenPixmaps" "true"
	Option "AGPMode" "4"	
	Option "GARTSize" "64"
	Option "AccelMethode" "EXA"
	Option "SubPixelOrder" "NONE"
	Option "DynamicClocks" "true"
	Option "bioshotkeys" "true"	
EndSection

Section "Monitor"
	Identifier	"Color LCD"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Monitor		"Color LCD"
	DefaultDepth	24
	Option "AddARGBGLXVisuals" "True"

	SubSection "Display"
		Depth		1
		Modes		"1280x854"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x854"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x854"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x854"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x854"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x854"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
	Option		"AIGLX"	"true"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
    Option "Composite" "true"
EndSection

```

thanks in advance

---

### Post by fuoco on 2006-11-04
> **bogoliubov said:**
> I guess you already knew this, but you can always add the therm_adt7460 module to /etc/modules. That way, it'll start when you boot the computer.

As for the problem with hardware acceleration, have a look at your xorg.conf and compare with what was written on earlier pages in this thread. But perhaps you've already tried this. In that case, I don't know what else to do. Perhaps check the output of glxinfo and see if there is something that won't work.

Yeah, thx. Here is the output of glxinfo, I don't see anything strange:

```
name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x4b
display: :0  screen: 0
direct rendering: Yes
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
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R300 20060815 AGP 4x TCL
OpenGL version string: 1.3 Mesa 6.5.1
OpenGL extensions:
    GL_ARB_fragment_program, GL_ARB_imaging, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_MESAX_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_gpu_program_parameters, 
    GL_EXT_histogram, GL_EXT_packed_pixels, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

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
```

and xorg.conf:

```
Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection


Section "Device"
        Identifier      "ATI Technologies, Inc. M11 NV [FireGL Mobility T2e]"
        Driver          "ati"
        BusID           "PCI:0:16:0"
        Option          "UseFBDev"              "true"
        Option          "AGPFastWrite"          "yes"
        Option          "AGPMode"               "4"
        Option          "ColorTiling"           "on"
        Option          "EnablePageFlip"        "true"
        Option          "AccelMethod"           "EXA"
        Option          "RenderAccel"           "true"
        Option          "DynamicClocks"         "on"
EndSection


Section "DRI"
        Mode    0666
EndSection
```

from glxgears I get:

```
libGL warning: 3D driver claims to not support visual 0x4b
*********************************WARN_ONCE*********************************
File r300_maos.c function r300EmitArrays line 546
Cannot handle offset 80302000 with stride 3, comp 3
***************************************************************************
Try R300_SPAN_DISABLE_LOCKING env var if this hangs.
```

Thanks...

---

### Post by ADBlues on 2006-11-04
> **bogoliubov said:**
> I guess you already knew this, but you can always add the therm_adt7460 module to /etc/modules. That way, it'll start when you boot the computer.

As for the problem with hardware acceleration, have a look at your xorg.conf and compare with what was written on earlier pages in this thread. But perhaps you've already tried this. In that case, I don't know what else to do. Perhaps check the output of glxinfo and see if there is something that won't work.

My thermal control module already start on boot.
As per the acceleration, I just realise that the number of FPS I got is extremely low, about 35.
So I guess there is a problem.

I've already tried the settings for xorg.conf described above but with no success.
There are no evident errors in the xorg log but I got this one while running glxgears:

```

libGL warning: 3D driver claims to not support visual 0x4b
*********************************WARN_ONCE*********************************
File r300_maos.c function r300EmitArrays line 546
Cannot handle offset bc302000 with stride 3, comp 3
libGL warning: 3D driver claims to not support visual 0x4b
*********************************WARN_ONCE*********************************
File r300_maos.c function r300EmitArrays line 546
Cannot handle offset bc302000 with stride 3, comp 3
******************************************************

```

And I also had success in capturing this error before the screen goes away when I launch compiz:

```

compiz:
compiz.real: SmcOpenConnection failed: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

```

Any hint?

---

### Post by ADBlues on 2006-11-04
> **cloudaj said:**
> Alright, so now that i've been messing with this all night, i've finally realized that for some reason, direct rendering is being reported as not working on my machine.  Woohoo wasting my time!  

However, I am not sure exactly why its not enabled.  I'll post my Xorg.conf file and maybe someone will have an answer for me.  Otherwise though, it's spitting out good results on glxgears, and glxgears isn't reporting any errors.  Although, my current state with Beryl is that it crashes my xserver after a few seconds of the load screen being up.

Anyways, here it is:

```

	Option "GARTSize" "64"

```


Hi, I've tested your conf on my machine and it appears that if you comment-out that line (Option "GARTSize" "64") you will have your acceleration activated.

If I activate this option on my machine, with this option activated I got 2000+ FPS but the gears spins slowly and everything but smoothly and teh acceleration is reported to be deactivated.

Without this option, the acceleration is reported to be active but the gears spins smoothly and the FPS drops to 35.

The mystery is getting deeper!

---

### Post by fuoco on 2006-11-04
> **ADBlues said:**
> Hi, I've tested your conf on my machine and it appears that if you comment-out that line (Option "GARTSize" "64") you will have your acceleration activated.

If I activate this option on my machine, with this option activated I got 2000+ FPS but the gears spins slowly and everything but smoothly and teh acceleration is reported to be deactivated.

Without this option, the acceleration is reported to be active but the gears spins smoothly and the FPS drops to 35.

The mystery is getting deeper!

I tried that GARTSize thing - well in fact it seems with it the DRI is not working and thus it uses software fallback, which appears to be faster that the results we currently get with DRI enabled. So it's no real mystery. In fact for me 64 doesn't make sense as there's only 32MB of memory on the card.

---

### Post by fuoco on 2006-11-04
If I may add, I think there's a strong possibility that this is all some bug in the drm/dri modules. We should try to get a newer version of Mesa (there seems to be a new release that didn't make it into edgy). I am not sure how to proceed with that though... Does anyone here know how to make such a package ?

---

### Post by cloudaj on 2006-11-04
with the GARTsize option, the card I have has 128 mb of ram, so 64 is perfectly acceptable.

---

### Post by fuoco on 2006-12-18
I'm bumping this because I'm very interested to know if anyone has any news about the old problems we had with beryl/compiz and 3d in general. Especially ADBlues, as we had the same problem with very low fps in glxgears.

I have managed to compile manually newer mesa drivers and I now get 900 fps. But in planet penguin racer I only get 3 fps. I haven't yet tested beryl or compiz...

Please write back your latest results with these issues. Thanks.

---

### Post by siman on 2006-12-21
I installed the xorgserver-patch and beryl via the repos above on my powerbook g4 with mobility 9000.. a few weeks ago.

Beryl is runnig rather smoothly and pretty stable.

Today I installed beryl on my desktop 386 and they have version 0.3.1 while on ppc it's still 0.1.1 or smth like that... anyone know when updates happen or who I can contact about that? Is there a problem, or should we get newer version of beryl easily?

---

### Post by sciurus on 2006-12-21
I still have problems  (the patched Xorg doesn't help) on a 1.33ghz powerbook.

[https://bugs.launchpad.net/distros/ubuntu/+source/xorg-server/+bug/76689](https://bugs.launchpad.net/distros/ubuntu/+source/xorg-server/+bug/76689)

[http://webdrive.service.emory.edu/users/bpitts/linux/compiz.png](http://webdrive.service.emory.edu/users/bpitts/linux/compiz.png)

---

### Post by trash on 2007-03-13
> **eidex said:**
> sorry for the delay, here is my xorg.conf! 

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# ......
Section "Device"
	Identifier	"ATI Technologies, Inc. M9+ 5C63 [Radeon Mobility 9000 (AGP)]"
	Driver		"radeon"
	BusID		"PCI:0:16:0"
#	Option 		"AGPMode" "4"
#	Option		"UseFBDev"		"true"
#	Option      	"XAANoOffscreenPixmaps" "true"
#	Option      	"DRI"     "true"
#	Option      	"EnablePageFlip" "On"
#	Option      	"CloneMode" "1024x768"
	
        Option          "XAANoOffscreenPixmaps"         
        Option          "AccelMethod"                   "XAA"   
        Option          "AGPMode"                       "4"    
        Option          "AGPFastWrite"                  "True"
        Option          "EnablePageFlip"                "True"  # Artefakte?
        Option          "ColorTiling"                   "1"     
        Option          "UseInternalAGPGART"            "no"    
        Option          "backingstore"                  "true"
        Option          "AllowGLXWithComposite"         "true"
        Option          "RenderAccel"                   "true"
EndSection....


```

I tried it on my g3 ibook ati 9000 i think, it rendered the machine unbootable.... i had to use a livecd to edit xorg back to normal... just a warning for other users.. such a drag this is still so difficult to get working.

---


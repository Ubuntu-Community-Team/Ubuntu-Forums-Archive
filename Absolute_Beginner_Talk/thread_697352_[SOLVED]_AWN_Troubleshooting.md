---
title: "[SOLVED] AWN Troubleshooting"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by zyvx on 2008-02-15
I recently attempted to install AWN but it is not working properly. I'm running gutsy gibbon and I have a couple days of linux experience. I found numerous guides on how to install it but none of them worked for me. Everything seems to install fine and I can even open up the manager but i can never see the dock, even though it says it's running. The monitor also shows all of the applets and their pythons are running. I think my problem stems from the startup because whenever i try to open it I get a rectangular flash in the upper-left corner but the dock never shows. And yes i made sure it wasn't auto hiding.

---

### Post by ashmew2 on 2008-02-15
Under System > Preferences > Appearance > Visual Effects , what is it set to ? none or extra ? and what graphic card are you using ? 

AWN requires you to be running fancy eye candy like Compiz/Beryl first.

---

### Post by zyvx on 2008-02-15
Right now its on none and when i try to switch it it says the composite extension is not available. I am almost positive that I installed Compiz tho as i have the manager as well. My card is an ATI RadeonExpress so it blows.

---

### Post by ashmew2 on 2008-02-15
AWN cant be run with "None"
You have to be running Beryl/Compiz if you want to run AWN.

Post the exact message it gives you , I may be able to help :)

---

### Post by zyvx on 2008-02-15
the composite extension is not available" and i can't even click ok to close it. It seems that compiz isn't running maybe but doesn't it come w/ gutsy?

I just typed compiz into the terminal and it spat out this:

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

so i think i need a new driver for the card where would i be able to do this?

---

### Post by WakkiTabakki on 2008-02-15
The missing composite extension is probably due to having the wrong video driver installed.

Whats the output of:
```
user@Computer:~$ glxinfo
```

(please, post result within QUOTE-tags :P)


/N

---

### Post by zyvx on 2008-02-15
Sry about that. here it is:

```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
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
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6473 (8.37.6)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array, 
    GL_S3_s3tc, GL_ARB_depth_texture, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_multisample, GL_ARB_occlusion_query, GL_ARB_point_parameters, 
    GL_ARB_point_sprite, GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_blend, 
    GL_ARB_vertex_buffer_object, GL_ARB_pixel_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_ARB_draw_buffers, GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, 
    GL_ATI_fragment_shader, GL_ATI_separate_stencil, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_ATI_vertex_streams, 
    GL_ATIX_texture_env_combine3, GL_ATIX_texture_env_route, 
    GL_ATIX_vertex_shader_output_point_size, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_texgen_reflection, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_EXT_vertex_shader, GL_HP_occlusion_test, GL_NV_blend_square, 
    GL_NV_occlusion_query, GL_NV_texgen_reflection, GL_SGI_color_matrix, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x41 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x43 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x44 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x45 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x46 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x47 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x48 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x49 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x4a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x52 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None

```

---

### Post by ashmew2 on 2008-02-15
Compiz comes with Gutsy by default. You can use Envy to first remove your ATi Driver (if you have it installed) and then Install it again. I think after that it should work.

To get Envy , do :

```
wget  http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.10-0ubuntu2_all.deb
```

Then go to a tty (CTRL ALT F1) , Type :
```

envy -t
```

And Remove the ATi Driver and then once thats done , restart your computer and INSTALL ATI Driver.That should install the perfect Driver you need. Try running Compiz after that and tell us the output.

---

### Post by ashmew2 on 2008-02-15
Do all this after installing the Driver with Envy

```
sudo gedit /etc/X11/xorg.conf
```

Put 1 instead of 0 in the last section so it looks like this:

EndSection
Section "Extensions"
Option "Composite" "1"
EndSection


Then try again.. if it doesn't work... then do:

sudo apt-get install xserver-xgl

Restart X by doing 
```

sudo /etc/init.d/gdm restart
```

Found it off here  : [http://ubuntuforums.org/showthread.php?t=576624](http://ubuntuforums.org/showthread.php?t=576624)

---

### Post by zyvx on 2008-02-15
alright so I got emerald up and running but now i have a few other issues. 
1.) AWN is running but i cannot d/l the applets through synaptic 
2.) I have a bunch of vertical lines on either side of the dock that I want to rid myself of.
3.) Is there a way to have emerald activated (i.e. have awn run) but use metacity for themes, because the switch really messed alot of my visuals up. My custom cursor is ignored on the desktop, and none of the settings seem to do anything in emerald. (i.e. trying to switch the sides of the buttons.) Basically i'm willing to try and get everything to work the way i want but if it's easier I would rather disable emerald themes as long as I can have a dock.

---

### Post by ashmew2 on 2008-02-15
Which Applets do you want to download/install ??
Have you tried : 
```

sudo apt-get install awn-core-applets
```

Regarding the lines , I think it has something to do with the applets. Try running AWN from the terminal and post the output , It might be useful in knowing what is causing the error.

```
avant-window-navigator &
```


I dont think you can run AWN with Metacity as the Window Manager . Could you exemplify yourself a bit more ?

---

### Post by zyvx on 2008-02-16
```
dan@dan-laptop:~$ sudo apt-get install awn-core-applets
[sudo] password for dan:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package awn-core-applets

```

Weird this is i don't have any of the applets stored anymore (I  thought) but awn says nothing about applets that I can remove.

```
dan@dan-laptop:~$ avant-window-navigator &
[1] 11055
dan@dan-laptop:~$ Screen is composited.
APPLET : /usr/lib/awn/applets/awn-system-monitor.desktop
APPLET : /usr/lib/awn/applets/calendar.desktop
APPLET : /usr/lib/awn/applets/awnterm.desktop
APPLET : /usr/local/lib/awn/applets/taskman.desktop
APPLET : /usr/lib/awn/applets/media-control.desktop

** (awn-applet-activation:11057): WARNING **: This desktop file does not exist /usr/lib/awn/applets/awn-system-monitor.desktop


** (awn-applet-activation:11061): WARNING **: This desktop file does not exist /usr/lib/awn/applets/awnterm.desktop

APPLET : /usr/lib/awn/applets/weather.desktop
APPLET : /usr/lib/awn/applets/trasher.desktop

** (awn-applet-activation:11059): WARNING **: This desktop file does not exist /usr/lib/awn/applets/calendar.desktop

APPLET : /usr/lib/awn/applets/plugger.desktop

** (awn-applet-activation:11067): WARNING **: This desktop file does not exist /usr/lib/awn/applets/trasher.desktop

APPLET : /usr/lib/awn/applets/separator.desktop

** (awn-applet-activation:11063): WARNING **: This desktop file does not exist /usr/lib/awn/applets/media-control.desktop


** (awn-applet-activation:11071): WARNING **: This desktop file does not exist /usr/lib/awn/applets/separator.desktop


** (awn-applet-activation:11069): WARNING **: This desktop file does not exist /usr/lib/awn/applets/plugger.desktop


** (awn-applet-activation:11065): WARNING **: This desktop file does not exist /usr/lib/awn/applets/weather.desktop
```

---

### Post by ashmew2 on 2008-02-17
Go in the Preferences of the AWN Dock and check whether Shadows is enabled. If it is , try disabling it and see if the lines are still there.If they are , try doing this :

```

sudo gedit /etc/apt/sources.list
```

When the file opens , add these to the end of the file :

```

deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
```

Then do :
```

wget http://download.tuxfamily.org/syzygy42/reacocard.asc
sudo apt-key add reacocard.asc
rm reacocard.asc
sudo apt-get update
```


Followed by :

```
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
```

Remeber to execute one line at a time. I dont know if you did this alreayd . Post back and let me know !

---

### Post by zyvx on 2008-02-17
I had already had that first part in sources.list. Everything seemed to be going fine until the last line. 

```
dan@dan-laptop:~$ sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
[sudo] password for dan:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
awn-core-applets-bzr is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  avant-window-navigator-bzr: Depends: libawn-bzr but it is not going to be installed
                              Depends: libawn-bzr (= 0.2.0-bzr158-1) but it is not going to be installed
  awn-core-applets-bzr: Depends: libawn-bzr but it is not going to be installed
                        Depends: libawn-bzr but it is not going to be installed
                        Depends: python-libawn-bzr but it is not going to be installed
  libawn-bzr-dev: Depends: libawn-bzr (= 0.2.0-bzr158-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

I've seen this before but I have no idea what it means but i decided to try what it suggested.

```
dan@dan-laptop:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

``` 

Figured I just had to sudo it.

```
dan@dan-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libawn-bzr python-libawn-bzr
The following NEW packages will be installed:
  libawn-bzr python-libawn-bzr
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/91.6kB of archives.
After unpacking 283kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 100470 files and directories currently installed.)
Unpacking libawn-bzr (from .../libawn-bzr_0.2.0-bzr158-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libawn-bzr_0.2.0-bzr158-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libawn.so.0.0.1', which is also in package libawn0
Unpacking python-libawn-bzr (from .../python-libawn-bzr_0.2.0-bzr158-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/python-libawn-bzr_0.2.0-bzr158-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/python2.5/site-packages/awn/awn.so', which is also in package python-awn
Errors were encountered while processing:
 /var/cache/apt/archives/libawn-bzr_0.2.0-bzr158-1_i386.deb
 /var/cache/apt/archives/python-libawn-bzr_0.2.0-bzr158-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

So I'm lost again. Does this mean that the files are corrupted? O, and the lines went away before I did any of this (I might have just needed a restart) But my applets package is still broken and I can't really install anything else.

---

### Post by zyvx on 2008-02-18
Figured out what my problems were thanks for all your help!

---


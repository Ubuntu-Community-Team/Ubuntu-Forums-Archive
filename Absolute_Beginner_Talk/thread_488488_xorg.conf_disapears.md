---
title: "xorg.conf disapears"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by trotos on 2007-06-30
Hello to all

I'm new to ubuntu and need a few answers.

I used the [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide) installation the method 2 manual installation, not using sudo apt-get

All is going well but...

during the package installation:
[PHP]sudo dpkg -i xorg-driver-fglrx_8.38.6-1*.deb \
fglrx-kernel-source_8.38.6-1*.deb \
fglrx-amdcccle_8.38.6-1*.deb[/PHP]
told me that i needed some libraries...I opened the Synaptic Package Manager find them and installed them (the libraries were:
```
ia32-libs
ia32-libs-gtk
ia32-libs-sdl
```
then I sudo the 
[PHP]sudo dpkg -i xorg-driver-fglrx_8.38.6-1*.deb \
fglrx-kernel-source_8.38.6-1*.deb \
fglrx-amdcccle_8.38.6-1*.deb[/PHP]
again and worked

compiling of kernell went smoothly

but when I reached the
[PHP]aticonfig --initial[/PHP] then there was this message:
Found fglrx primary device section
Nothing to do, terminating.

and
[PHP]sudo aticonfig --overlay-type=Xv[/PHP] gave messages as :1.

Using /etc/X11/xorg.conf
```
Saved back-up to /etc/X11/xorg.conf.fglrx-4
*** glibc detected *** aticonfig: munmap_chunk(): invalid pointer: 0x00007fffadae4a2b ***
======= Backtrace: =========
/lib/libc.so.6(cfree+0x1b6)[0x2b20fde06396]
aticonfig[0x40a78d]
aticonfig[0x40a6e9]
aticonfig[0x40d963]
aticonfig(XOpenDisplay+0x2b5)[0x402505]
aticonfig(XOpenDisplay+0x139)[0x402389]
/lib/libc.so.6(__libc_start_main+0xf4)[0x2b20fddb08e4]
aticonfig(XOpenDisplay+0x5a)[0x4022aa]
======= Memory map: ========
00400000-00423000 r-xp 00000000 08:27 136780                             /usr/bin/aticonfig
00522000-00529000 rw-p 00022000 08:27 136780                             /usr/bin/aticonfig
00529000-0054a000 rw-p 00529000 00:00 0                                  [heap]
2b20fcfc5000-2b20fcfe1000 r-xp 00000000 08:27 1013843                    /lib/ld-2.5.so
2b20fcfe1000-2b20fcfe5000 rw-p 2b20fcfe1000 00:00 0 
2b20fd1e0000-2b20fd1e2000 rw-p 0001b000 08:27 1013843                    /lib/ld-2.5.so
2b20fd1e2000-2b20fd1e8000 r-xp 00000000 08:27 132368                     /usr/lib/libXrandr.so.2.1.0
2b20fd1e8000-2b20fd3e8000 ---p 00006000 08:27 132368                     /usr/lib/libXrandr.so.2.1.0
2b20fd3e8000-2b20fd3e9000 rw-p 00006000 08:27 132368                     /usr/lib/libXrandr.so.2.1.0
2b20fd3e9000-2b20fd3f2000 r-xp 00000000 08:27 132370                     /usr/lib/libXrender.so.1.3.0
2b20fd3f2000-2b20fd5f1000 ---p 00009000 08:27 132370                     /usr/lib/libXrender.so.1.3.0
2b20fd5f1000-2b20fd5f2000 rw-p 00008000 08:27 132370                     /usr/lib/libXrender.so.1.3.0
2b20fd5f2000-2b20fd602000 r-xp 00000000 08:27 132348                     /usr/lib/libXext.so.6.4.0
2b20fd602000-2b20fd802000 ---p 00010000 08:27 132348                     /usr/lib/libXext.so.6.4.0
2b20fd802000-2b20fd803000 rw-p 00010000 08:27 132348                     /usr/lib/libXext.so.6.4.0
2b20fd803000-2b20fd909000 r-xp 00000000 08:27 132327                     /usr/lib/libX11.so.6.2.0
2b20fd909000-2b20fdb09000 ---p 00106000 08:27 132327                     /usr/lib/libX11.so.6.2.0
2b20fdb09000-2b20fdb10000 rw-p 00106000 08:27 132327                     /usr/lib/libX11.so.6.2.0
2b20fdb10000-2b20fdb11000 rw-p 2b20fdb10000 00:00 0 
2b20fdb11000-2b20fdb92000 r-xp 00000000 08:27 1013892                    /lib/libm-2.5.so
2b20fdb92000-2b20fdd91000 ---p 00081000 08:27 1013892                    /lib/libm-2.5.so
2b20fdd91000-2b20fdd93000 rw-p 00080000 08:27 1013892                    /lib/libm-2.5.so
2b20fdd93000-2b20fdeda000 r-xp 00000000 08:27 1013861                    /lib/libc-2.5.so
2b20fdeda000-2b20fe0da000 ---p 00147000 08:27 1013861                    /lib/libc-2.5.so
2b20fe0da000-2b20fe0dd000 r--p 00147000 08:27 1013861                    /lib/libc-2.5.so
2b20fe0dd000-2b20fe0df000 rw-p 0014a000 08:27 1013861                    /lib/libc-2.5.so
2b20fe0df000-2b20fe0e4000 rw-p 2b20fe0df000 00:00 0 
2b20fe0e4000-2b20fe0e6000 r-xp 00000000 08:27 132333                     /usr/lib/libXau.so.6.0.0
2b20fe0e6000-2b20fe2e5000 ---p 00002000 08:27 132333                     /usr/lib/libXau.so.6.0.0
2b20fe2e5000-2b20fe2e6000 rw-p 00001000 08:27 132333                     /usr/lib/libXau.so.6.0.0
2b20fe2e6000-2b20fe2e7000 rw-p 2b20fe2e6000 00:00 0 
2b20fe2e7000-2b20fe2ec000 r-xp 00000000 08:27 132344                     /usr/lib/libXdmcp.so.6.0.0
2b20fe2ec000-2b20fe4eb000 ---p 00005000 08:27 132344                     /usr/lib/libXdmcp.so.6.0.0
2b20fe4eb000-2b20fe4ec000 rw-p 00004000 08:27 132344                     /usr/lib/libXdmcp.so.6.0.0
2b20fe4ec000-2b20fe4ee000 r-xp 00000000 08:27 1013880                    /lib/libdl-2.5.so
2b20fe4ee000-2b20fe6ee000 ---p 00002000 08:27 1013880                    /lib/libdl-2.5.so
2b20fe6ee000-2b20fe6f0000 rw-p 00002000 08:27 1013880                    /lib/libdl-2.5.so
2b20fe6f0000-2b20fe6f2000 rw-p 2b20fe6f0000 00:00 0 
2b20fe6f2000-2b20fe6ff000 r-xp 00000000 08:27 1013886                    /lib/libgcc_s.so.1
2b20fe6ff000-2b20fe8ff000 ---p 0000d000 08:27 1013886                    /lib/libgcc_s.so.1
2b20fe8ff000-2b20fe900000 rw-p 0000d000 08:27 1013886                    /lib/libgcc_s.so.1
7fffadad0000-7fffadae5000 rw-p 7fffadad0000 00:00 0                      [stack]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vdso]
Aborted (core dumped)
```

OR                                                                      2. 

```
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-5
*** glibc detected *** aticonfig: munmap_chunk(): invalid pointer: 0x00007fff91fdaa2b ***
======= Backtrace: =========
/lib/libc.so.6(cfree+0x1b6)[0x2b4e19910396]
aticonfig[0x40a78d]
aticonfig[0x40a6e9]
aticonfig[0x40d963]
aticonfig(XOpenDisplay+0x2b5)[0x402505]
aticonfig(XOpenDisplay+0x139)[0x402389]
/lib/libc.so.6(__libc_start_main+0xf4)[0x2b4e198ba8e4]
aticonfig(XOpenDisplay+0x5a)[0x4022aa]
======= Memory map: ========
00400000-00423000 r-xp 00000000 08:27 136780                             /usr/bin/aticonfig
00522000-00529000 rw-p 00022000 08:27 136780                             /usr/bin/aticonfig
00529000-0054a000 rw-p 00529000 00:00 0                                  [heap]
2b4e18acf000-2b4e18aeb000 r-xp 00000000 08:27 1013843                    /lib/ld-2.5.so
2b4e18aeb000-2b4e18aef000 rw-p 2b4e18aeb000 00:00 0 
2b4e18cea000-2b4e18cec000 rw-p 0001b000 08:27 1013843                    /lib/ld-2.5.so
2b4e18cec000-2b4e18cf2000 r-xp 00000000 08:27 132368                     /usr/lib/libXrandr.so.2.1.0
2b4e18cf2000-2b4e18ef2000 ---p 00006000 08:27 132368                     /usr/lib/libXrandr.so.2.1.0
2b4e18ef2000-2b4e18ef3000 rw-p 00006000 08:27 132368                     /usr/lib/libXrandr.so.2.1.0
2b4e18ef3000-2b4e18efc000 r-xp 00000000 08:27 132370                     /usr/lib/libXrender.so.1.3.0
2b4e18efc000-2b4e190fb000 ---p 00009000 08:27 132370                     /usr/lib/libXrender.so.1.3.0
2b4e190fb000-2b4e190fc000 rw-p 00008000 08:27 132370                     /usr/lib/libXrender.so.1.3.0
2b4e190fc000-2b4e1910c000 r-xp 00000000 08:27 132348                     /usr/lib/libXext.so.6.4.0
2b4e1910c000-2b4e1930c000 ---p 00010000 08:27 132348                     /usr/lib/libXext.so.6.4.0
2b4e1930c000-2b4e1930d000 rw-p 00010000 08:27 132348                     /usr/lib/libXext.so.6.4.0
2b4e1930d000-2b4e19413000 r-xp 00000000 08:27 132327                     /usr/lib/libX11.so.6.2.0
2b4e19413000-2b4e19613000 ---p 00106000 08:27 132327                     /usr/lib/libX11.so.6.2.0
2b4e19613000-2b4e1961a000 rw-p 00106000 08:27 132327                     /usr/lib/libX11.so.6.2.0
2b4e1961a000-2b4e1961b000 rw-p 2b4e1961a000 00:00 0 
2b4e1961b000-2b4e1969c000 r-xp 00000000 08:27 1013892                    /lib/libm-2.5.so
2b4e1969c000-2b4e1989b000 ---p 00081000 08:27 1013892                    /lib/libm-2.5.so
2b4e1989b000-2b4e1989d000 rw-p 00080000 08:27 1013892                    /lib/libm-2.5.so
2b4e1989d000-2b4e199e4000 r-xp 00000000 08:27 1013861                    /lib/libc-2.5.so
2b4e199e4000-2b4e19be4000 ---p 00147000 08:27 1013861                    /lib/libc-2.5.so
2b4e19be4000-2b4e19be7000 r--p 00147000 08:27 1013861                    /lib/libc-2.5.so
2b4e19be7000-2b4e19be9000 rw-p 0014a000 08:27 1013861                    /lib/libc-2.5.so
2b4e19be9000-2b4e19bee000 rw-p 2b4e19be9000 00:00 0 
2b4e19bee000-2b4e19bf0000 r-xp 00000000 08:27 132333                     /usr/lib/libXau.so.6.0.0
2b4e19bf0000-2b4e19def000 ---p 00002000 08:27 132333                     /usr/lib/libXau.so.6.0.0
2b4e19def000-2b4e19df0000 rw-p 00001000 08:27 132333                     /usr/lib/libXau.so.6.0.0
2b4e19df0000-2b4e19df1000 rw-p 2b4e19df0000 00:00 0 
2b4e19df1000-2b4e19df6000 r-xp 00000000 08:27 132344                     /usr/lib/libXdmcp.so.6.0.0
2b4e19df6000-2b4e19ff5000 ---p 00005000 08:27 132344                     /usr/lib/libXdmcp.so.6.0.0
2b4e19ff5000-2b4e19ff6000 rw-p 00004000 08:27 132344                     /usr/lib/libXdmcp.so.6.0.0
2b4e19ff6000-2b4e19ff8000 r-xp 00000000 08:27 1013880                    /lib/libdl-2.5.so
2b4e19ff8000-2b4e1a1f8000 ---p 00002000 08:27 1013880                    /lib/libdl-2.5.so
2b4e1a1f8000-2b4e1a1fa000 rw-p 00002000 08:27 1013880                    /lib/libdl-2.5.so
2b4e1a1fa000-2b4e1a1fc000 rw-p 2b4e1a1fa000 00:00 0 
2b4e1a1fc000-2b4e1a209000 r-xp 00000000 08:27 1013886                    /lib/libgcc_s.so.1
2b4e1a209000-2b4e1a409000 ---p 0000d000 08:27 1013886                    /lib/libgcc_s.so.1
2b4e1a409000-2b4e1a40a000 rw-p 0000d000 08:27 1013886                    /lib/libgcc_s.so.1
7fff91fc6000-7fff91fdb000 rw-p 7fff91fc6000 00:00 0                      [stack]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vdso]
Aborted (core dumped)
```


so what it does is rename the xorg.config file (probably to do any changes needed) but never writes it back.
and the fglrxinfo command shows the mesa driver.

Then at the applications tab, upper menu, the catalyst control center is there but never opens

Another thing is that the temperature of the card goes to 67 C, when at winXP stays below 60 C.

I got problems as you understand

Any help will be welcomed.

By the way how can i revert any driver installation to an old one and remove any files-settings-from the failed installation.

Thank You

---

### Post by trotos on 2007-07-01
Maybe I forgot to mention that I got a x1800xl ati card

My brains have been melt from reading, searching, trying, I had destroyed the xorg.config about 5 times, but I GOT THE Solution to my problem. Via Synaptic manager I uninstalled everything regarding ati drivers and then I used the excellent [ENVY]("http://albertomilone.com/nvidia_scripts1.html") utility (points to author) that automate everything.

So at the xgl session using the fglrxinfo command i get the 
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1800 Series
OpenGL version string: 2.0.6474 (8.38.6)
```

and using the glxinfo i got the 

```
name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No
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
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1800 Series
OpenGL version string: 1.2 (2.0.6474 (8.38.6))
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_transpose_matrix, GL_EXT_abgr, 
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
```

So fglrxinfo is correct.
But what about glxinfo? I can not interpret it. PLEASE HELP ME ON THAT.

The problem that I got is at the xgl session using the 
```
glxinfo | grep direct
``` command

I get the crappy
```

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No
```

thousands of posts about that one  the only thing I found is [this]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL") link:

But I got a new Question:

How do I remove the old XGL SESSION? Is it necessary?

and still some problems persist...

Then at the applications tab, upper menu, the catalyst control center is there but never opens

Another thing is that the temperature of the card goes to 67 C, when at winXP stays below 60 C.

---

### Post by trotos on 2007-07-06
Still have problems with

glxinfo | grep direct   command

Still the same: Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No

AND Beryl fails to load, ati control center also (the link is there), x1800xl reaches 67 oC.

Help me please

---

### Post by Viewtifulj on 2007-07-06
same card. almost the same problem. expcept for that mine wouldnt even load to the boot screen. I thought i was working properly for a second there, but alas, it was not.  I mean, the system booted up fine, but after that initial screen with Ubuntu and the orange bar the thing would go to a black screen.

---

### Post by trotos on 2007-07-07
I had the same thing, so I did a few things in console mode, no X window interface. I "sudo apt-get" the application called envy. and followed their instraction for removing the old drivers and then installing the latest ones. Then created a new xorg session...and then the problems I mention. the Xlib message error and the beryl could not load.

---

### Post by trotos on 2007-07-09
so nothing at all?

---

### Post by Jolly-Swagman on 2007-07-09
There are new ATI drivers now available here at following link,,,,
[http://ati.amd.com/support/drivers/linux/linux-radeon.htm](http://ati.amd.com/support/drivers/linux/linux-radeon.htm)

To check ver of  Xfree86 if you have on your system see attached file and run that will give you an output if you have them installed

Jolly Swagman

---

### Post by lordram on 2007-07-20
Try installing "libstdc++5" that works with my debian sid :)

---

### Post by alienexplorers on 2007-07-20
Remove your ATI drivers and go to:
> [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
let the Envy script load your drivers.  When I was using an old ATI card it worked perfectly.  Give it a go.

---

### Post by trotos on 2007-08-26
It's been a while since I've tried anything on my problem but I'm half way there...

I believe that the ATI drivers have been configured correctly

What I did was:
Installing ati driver using the ENVY script, by using the manual way.
I had already included from the manual way the following lines at the xorg.config file:
```
Section "Extensions"
        Option  "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection
```

and also using the gksu gedit /etc/default/linux-restricted-modules-common

I add the following lines:

```
DISABLED_MODULES="fglrx"
```

and then I run the ENVY script.

So. creation of an xglx section:

gksudo gedit /usr/bin/startxgl

insert the exact lines:

```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
sleep 4
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session
```

MADE IT EXECUTABLE ( I cannot remember the lines but you can do it by right-clicking the Icon of startxgl)

Then created a file:
gksudo gedit /usr/share/xsessions/xgl.desktop

with the lines:

```
[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Comment=Start an Xgl Session
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application
```

To create a session.

Then I reboot the system and selected the xgl session.

on a terminal the after the commands

 fglrxinfo:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1800 Series
OpenGL version string: 2.0.6650 (8.39.4)

```

 glxinfo

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
OpenGL renderer string: Radeon X1800 Series
OpenGL version string: 2.0.6650 (8.39.4)
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
    GL_ARB_draw_buffers, GL_ATI_draw_buffers, GL_ATI_element_array, 
    GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, GL_ATI_map_object_buffer, 
    GL_ATI_separate_stencil, GL_ATI_shader_texture_lod, 
    GL_ATI_texture_compression_3dc, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_float, GL_ATI_texture_mirror_once, 
    GL_ATI_vertex_array_object, GL_ATI_vertex_attrib_array_object, 
    GL_ATI_vertex_streams, GL_ATIX_texture_env_combine3, 
    GL_ATIX_texture_env_route, GL_ATIX_vertex_shader_output_point_size, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
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
0x33 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x34 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x35 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x36 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x37 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x38 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x39 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x40 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x41 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x42 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None

```

 and glxgears give me an output of:

```
trotos@stupid:~$ glxgears41956 frames in 5.0 seconds = 8391.195 FPS
77235 frames in 5.0 seconds = 15446.997 FPS
59278 frames in 5.0 seconds = 11855.544 FPS
76730 frames in 5.0 seconds = 15345.944 FPS
77534 frames in 5.0 seconds = 15506.762 FPS
77537 frames in 5.0 seconds = 15507.220 FPS
76418 frames in 5.0 seconds = 15283.489 FPS
74802 frames in 5.0 seconds = 14960.389 FPS
77282 frames in 5.0 seconds = 15456.208 FPS
75394 frames in 5.0 seconds = 15078.610 FPS

``` 

So I believe that ATI driver is properly installed.

Then I installed the compiz-fusion from the reposite packages...standard procedure

So I thought I was ready....

I entered:
  compiz --replace or compiz --replace --indirect-rendering 
and end up with:
```
trotos@stupid:~$ compiz --replace 
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.
trotos@stupid:~$ compiz --replace --indirect-rendering 
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

```

as for the replies...

@lordram

libstdc++5 is already installed

@alienexplorers

that's the way I'm doing it, although there are various reports that reporting ENVY script of messing with the OS.

SO WHAT ABOUT THIS NEW ERROR???

---

### Post by trotos on 2007-08-26
forgot to say that when I set up the following xgl session to boot from, then every time system freezes at the point where panels are showing up. The no mouse movement, no responding to the keyboard...nothing only thing I can do is ctrl+shift+backspace

the files for this case are as listed:

startxgl.sh

```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session
```

AND

xgl.desktop

```
[Desktop Entry]
Encoding=UTF-8
Name=Xgl
[COLOR="Blue"]Exec=/usr/local/bin/startxgl.sh[/COLOR]
Icon=
Type=Application
```

AND YOU MIGHT WONDER THAT IN EACH CASE THE STARTXGL.SH IS located in different folder

---


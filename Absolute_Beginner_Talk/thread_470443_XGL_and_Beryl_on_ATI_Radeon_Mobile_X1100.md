---
title: "XGL and Beryl on ATI Radeon Mobile X1100"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by tll_2k on 2007-06-11
I'm trying to get ubuntu and beryl up and running on my brother's Acer Aspire 5050 laptop. It has an ATI Radeon Mobility X1100 graphics card. I use these guides:

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide")

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL")

I tried using this one first, but i couldn't get my shutdown and restart buttons to show up, even with its fix:

[http://ubuntuforums.org/showthread.php?t=399643]("http://ubuntuforums.org/showthread.php?t=399643")

Whenever I first booted into the XGL session, it worked fine. After i restarted, though, it messed up. heres what it looks like:

[IMG]http://i17.photobucket.com/albums/b53/tll_2k/problem.png[/IMG]

i can boot just fine into a non xgl session, but I'd really like to have beryl working on this computer. In a non XGL session, fglrxinfo:

```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

```
And glxinfo:

```
name of display: :0.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0  screen: 0
direct rendering: No
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
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None

```

I tried reinstalling the ati drivers. It worked until I logged off and back on, then it did the same thing...

Thanks in advance
       Tyler

---

### Post by luckyd on 2007-06-11
Why don't you upgrade to feisty, which has  AIGLX built in?

---

### Post by timcredible on 2007-06-11
i got beryl working on an ati x1300, but it was a pain.  but i would never, ever, buy an ati card for my home - nvidia is soooo much easier in linux.  i would recommend just going through the how-tos until you get it working, and then only buy nvidia in the future.

---

### Post by cempluk on 2007-07-20
i have the same problem is there any solution for this?

Thanks

---

### Post by Mornedhel on 2007-07-20
I had trouble too installing Beryl on my Acer with an ATI X1400, until I followed the walkthrough on the Beryl website... It works perfectly well now, even the unsupported plugins.

---

### Post by cpangratzbg on 2007-07-29
Try to disable the composite extension in the xorg.conf



Section "Extensions"
	Option		"Composite"	"0"
EndSection

---

### Post by SirPerigrin on 2007-08-18
The fglrx drivers that come with ubuntu are the problem most likely. I have an X300 and this wiki worked for me. [http://www.howforge.com/how-to-setup-fglrx-for-ubuntu-feisty](http://www.howforge.com/how-to-setup-fglrx-for-ubuntu-feisty) . Not sure if this will get beryl to run in on AIGLX, but it will get it to run on XGL. Which atm is better than what you have now as you dont even have Direct Rendering.

---


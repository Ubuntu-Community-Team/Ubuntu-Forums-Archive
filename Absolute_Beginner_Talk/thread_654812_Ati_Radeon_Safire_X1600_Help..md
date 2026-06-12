---
title: "Ati Radeon Safire X1600 Help."
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by microcronz on 2007-12-31
Does anyone have a manual or can help me install my graphics card. It is a ATI RADEON SAFIRE X1600. Im running ububtu 7.10. I re-installed ubuntu.

---

### Post by espressopigeon on 2007-12-31
So you actually need to put the card into your PC or are you looking for drivers?

---

### Post by Don1500 on 2007-12-31
Check here:
[http://ubuntuforums.org/showpost.php?p=4047910&postcount=6](http://ubuntuforums.org/showpost.php?p=4047910&postcount=6)

---

### Post by kellemes on 2007-12-31
> **microcronz said:**
> Does anyone have a manual or can help me install my graphics card. It is a ATI RADEON SAFIRE X1600. Im running ububtu 7.10. I re-installed ubuntu.


If you start the restricted driver manager you can install the driver, in my case it worked without having to tweak.. I have a x1650

---

### Post by microcronz on 2007-12-31
OK done.  I added the ATI restricted driver.  How do I make sure it is working correctly?

---

### Post by The Tronyx on 2007-12-31
> **microcronz said:**
> OK done.  I added the ATI restricted driver.  How do I make sure it is working correctly?

enter glxinfo into a terminal and post the output

---

### Post by microcronz on 2007-12-31
chris@chris-desktop:~$ glxinfo
name of display: :0.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
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
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
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
0x22 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x23 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 None
0x24 16 tc  0 24  0 r  y  .  5  6  5  8  0 16  8 16 16 16 16  0 0 None
0x25 16 tc  0 24  0 r  .  .  5  6  5  8  0 16  8 16 16 16 16  0 0 None
0x3d 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
chris@chris-desktop:~$ 
chris@chris-desktop:~$

---

### Post by The Tronyx on 2007-12-31
> **microcronz said:**
> chris@chris-desktop:~$ glx info
bash: glx: command not found

glxinfo not glx info

---

### Post by The Tronyx on 2007-12-31
> 
Xlib: extension "XFree86-DRI" missing on display ":0.0".

Looks wrong.  Can you tell me what fglrxinfo returns?

---

### Post by microcronz on 2007-12-31
chris@chris-desktop:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

---

### Post by kellemes on 2007-12-31
Post your /var/log/Xorg.0.log
withing the [CODE]-tags please..

---

### Post by The Tronyx on 2007-12-31
> **microcronz said:**
> chris@chris-desktop:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

That tells you that you did not properly install the ATI drivers or rather they did not apply correctly.  I have the same video card and here is my info.

> 
tronyx@wrekx:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 2.0.6958 Release

tronyx@wrekx:~$ 


You may need to manually install it, let me find the link I have used.  In the mean time it might be best to disable the restricted drivers.

Edit: See if this gives you something to work with.
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Installation](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Installation)

---

### Post by yaknowwat on 2007-12-31
Open the system manager and check if Xgl is running.

I would get that with an my ATI card until I removed Xgl.

if Xgl is running go in the Synaptic package manager and remove it.

After that Kill Xgl in the process manager.

Before doing any of that Make sure you DO NOT have compiz or have it enabled.

ATI + Xgl =/= mix

also your performance will shoot up about 3x times if you remove Xgl (if you have it)

---

### Post by kellemes on 2007-12-31
> **yaknowwat said:**
> 
ATI + Xgl =/= mix


You can get crap when you have XGL installed without using a composite manager.. simply install a composite manager does fix the issues you may have.
Anyway, the newer fglrx-drivers support AIGLX, so XGL isn't needed anymore.. works at my end.

---

### Post by barisurum on 2008-01-04
I have an x1650. First I installed the driver with restricted manager, it worked, but system used to crash often. So I used envy to install the driver manually, and I used the driver 8.40. It seems to work without problems so far. And direct rendering is available. install and use envy, maybe will help.

---


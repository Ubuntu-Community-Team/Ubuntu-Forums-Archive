---
title: "New User"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by mellamopobrede on 2007-08-16
I just installed Ubuntu 7.04 on my desktop AMD Sempron +3100 1.5 GB RAM and ATI Radeon X1600.  I updated and installed the graphics driver using Envy, but my computer just randomly freezes.  I cant use the mouse or the keyboard and the only way to log back in is to do a hard reset.  Anyone have any ideas? Thanks :)

---

### Post by Hobo Joe on 2007-08-16
Do you have Beryl or something similar?

---

### Post by mellamopobrede on 2007-08-16
I do not yet.

---

### Post by Hobo Joe on 2007-08-16
Paste the output of:
```

glxinfo

```

---

### Post by mellamopobrede on 2007-08-16
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
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
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

---

### Post by bodhi.zazen on 2007-08-16
See if this wiki helps : [http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

---

### Post by Hobo Joe on 2007-08-16
You're drivers are not installed properly. What graphics card are you using?

And you say you used Envy, but what driver version did you install?

---

### Post by overdrank on 2007-08-16
HI this thread has help some and I hope it will help you
[http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)
Good luck!

---

### Post by mellamopobrede on 2007-08-16
envy_0.9.7-0ubuntu8_all.deb

This was the version that i used.

---

### Post by mellamopobrede on 2007-08-16
Also my graphics card is ATI Radeon X1600 512 MB

---

### Post by Hobo Joe on 2007-08-16
> **mellamopobrede said:**
> envy_0.9.7-0ubuntu8_all.deb

This was the version that i used.

You misunderstand me, when I say which version, I mean when you ran envy, what manufacturer did you pick, and what driver version?

---

### Post by mellamopobrede on 2007-08-16
I definitely picked the ATI version

Envy 0.9.7

---

### Post by mellamopobrede on 2007-08-16
Should i install my driver using a method other than Envy?

---


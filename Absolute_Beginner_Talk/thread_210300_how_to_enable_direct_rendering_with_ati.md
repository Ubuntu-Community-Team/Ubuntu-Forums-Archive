---
title: "how to enable direct rendering with ati?"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by j2000 on 2006-07-06
Im linux newbie...
I have Ati Radeon 9250.
Installed latest driver, but it does not have direct rendering.
So i cant play 3d games,such as Wolfenstein Enemy Territory...and glxgears diag is slow...
Also wanna enable hardware acceleration...
What should i do?
Please help :(

---

### Post by Albi on 2006-07-06
do fglrxinfo and see if it shows the correct output

---

### Post by j2000 on 2006-07-07
name of display: :0.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
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
0x23 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  1 0 None
0x24 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  1 0 None
0x25 16 tc  0 24  0 r  y  .  5  6  5  8  0 16  8 16 16 16 16  1 0 None
0x26 16 tc  0 24  0 r  .  .  5  6  5  8  0 16  8 16 16 16 16  1 0 None
0x27 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  1 0 None
0x28 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  1 0 None
0x29 16 dc  0 24  0 r  y  .  5  6  5  8  0 16  8 16 16 16 16  1 0 None
0x2a 16 dc  0 24  0 r  .  .  5  6  5  8  0 16  8 16 16 16 16  1 0 None

It all seems to be OK.

on Suse, i could enable Direct rendering during new installation, so there has to be a chance to change it on the fly...
but how?

---

### Post by j2000 on 2006-07-07
sry, this glxinfo was from PC with Ati Rage 3d 2x. But theres no difference...the problem exist on both-

---

### Post by richbarna on 2006-07-07
Take a look at this:-
[http://www.ubuntuforums.org/showthread.php?t=143283&highlight=mesa+dri+ati](http://www.ubuntuforums.org/showthread.php?t=143283&highlight=mesa+dri+ati)

I found it by using the "Forum search" with mesa + dri + ati ;)

---


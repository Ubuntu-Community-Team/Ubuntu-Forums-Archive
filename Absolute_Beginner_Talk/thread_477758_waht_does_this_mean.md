---
title: "waht does this mean"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by pardesi on 2007-06-18
when i typed
```
compiz --replace
```

i get

```
pardesi@pardesi-desktop:~$ compiz --replace
/usr/bin/compiz.real: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real: Failed to manage screen: 0
/usr/bin/compiz.real: No manageable screens found on display :0.0
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```
and nothing else

---

### Post by yabbadabbadont on 2007-06-18
It most likely means that either your video card is not new enough to support XGL/composite or you don't have the correct video drivers installed (or enabled).  Please post the output when you run the "glxinfo" command in a terminal window.

---

### Post by pardesi on 2007-06-19
here is it 

```
pardesi@pardesi-desktop:~$ glxinfo
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
0x3d 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
pardesi@pardesi-desktop:~$ 


```

---

### Post by yabbadabbadont on 2007-06-19
Well, the extension that the error message claims is missiing is clearly listed as being available in your glxinfo output...  however, it looks like it is being provided through software rendering using the Mesa libraries.  That should work, but be extremely slow.  Make sure that you have the hardware accelerated video drivers installed for your card.  Either the ATI or Nvidia proprietary drivers.  (assuming you have either an ATI or Nvidia card)

Edit: From the output, it looks like you have an ATI card.

---

### Post by pardesi on 2007-06-19
so how do i install Xfree86-DRI ...

---

### Post by yabbadabbadont on 2007-06-19
Sorry.  I can't help you with ATI.  I've only ever messed with nvidia.  However, you might try using these:  [http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

Edit: Those appear to only be for dapper and edgy.  Sorry.

---

### Post by pardesi on 2007-06-19
thanks everything is fine now ....i just need to install beryl

---


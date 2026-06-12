---
title: "Envy removed my Harware 3d Acceleration..."
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by timberdc on 2007-06-19
And replaced it with SGI/Mesa. Why would this happen? Is there a way to get hardware 3d back, short of removing my drivers? This is for an ATI x1600 Pro, btw.
Here is my glxinfo:

timber@dc1:~$ glxinfo
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
timber@dc1:~$ 


:(

---

### Post by starcraft.man on 2007-06-19
I don't understand... Envy only installs the drivers (it uninstalls only if you tell it to...) If you already had drivers in, why did you put Envy in and I assume install over it? If you didn't have any drivers installed before, then Envy picks the best one for your card. Please clarify.

---

### Post by timberdc on 2007-06-19
> **starcraft.man said:**
> I don't understand... Envy only installs the drivers (it uninstalls only if you tell it to...) If you already had drivers in, why did you put Envy in and I assume install over it? If you didn't have any drivers installed before, then Envy picks the best one for your card. Please clarify.

Well, I want to try Beryl, and I wanted to make sure that I had the latest drivers. It was suggested in another thread to try Envy. Envy overwrote my existing "restricted" drivers with these. I don't have any idea why. Envy ran an ATI installer script, so I'm not even sure were these came from. I'll re-run Envy I guess and see what happens.

---

### Post by timberdc on 2007-06-19
Reran Envy, and it correctly installed this time.

---

### Post by starcraft.man on 2007-06-19
> **timberdc said:**
> Reran Envy, and it correctly installed this time.

There you go. Kinda weird, might wanna report it to Al so he can have a look at it.

Sorry for not getting back sooner, was busy... >.>.

---

### Post by timberdc on 2007-06-20
> **starcraft.man said:**
> There you go. Kinda weird, might wanna report it to Al so he can have a look at it.

Sorry for not getting back sooner, was busy... >.>.

Thanks for replying!

---


---
title: "ati, aiglx, fglrx newbie questions"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by TedGarvin on 2007-11-01
Hello, I have a real newbie question. I'm using an ATI 9600XT, with 256MB. .  Should I be using AIGLX or XGL?  And which driver should I try to use?  3D games run extremely slow, but AWN and Compiz seem to run just fine.  I don't even know if I need help.  That's how lost I am.  Any help, or suggestions would be greatly appreciated.

---

### Post by Pumalite on 2007-11-01
Take a look in System>Administration>Restricted Drivers Manager

---

### Post by TedGarvin on 2007-11-02
> **Pumalite said:**
> Take a look in System>Administration>Restricted Drivers Manager
Thanks.  I can install the restricted driver.  My question was muddled. Let me try to clarify.   I'm running the SGI driver with Gutsy right now.  The output of glxinfo tells me I have direct rendering.  What driver should I run with my video card to make sure I'm getting hardware 3d acceleration on my desktop as well as in games?  Judging by my performance in games like "Assault Cube" or "Enemy Territory", It doesn't seem to be using the GPU correctly, if at all.

---

### Post by Pumalite on 2007-11-02
The Restricted Drivers Manager installs the latest driver available for your setup. So, that's all you get.

---

### Post by TedGarvin on 2007-11-02
ok, but when they (restricted drivers) are installed, I lose the accelerated desktop and the login screen color and position are off.  Do I then need to enable aiglx or something else?

---

### Post by Pumalite on 2007-11-02
Go to System>Preferences>Advanced Desktop Effects Settings.

---

### Post by TedGarvin on 2007-11-02
> **Pumalite said:**
> Go to System>Preferences>Advanced Desktop Effects Settings.

ok, I install the restricted drivers.  Go to System>Preferences>Advanced Desktop Effects Settings And what do I do from there?  Are you saying that all I need to do is turn them on from there?  
[edit] OK, I installed the restricted drivers.  No desktop acceleration, and I can't turn it on, but I tried and Assault Cube and it runs great.  There has to be a way to keep these drivers and run compiz.

---

### Post by TedGarvin on 2007-11-02
ok, I've installed XGL with the ati drivers. ( I think I did, I don't know how to check.)  I have the accelerated desktop back, but with I'm back to really poor performance with 3d games and my login screen still has the colors that are off and it is offset.  Any advice, or how-to pages anyone can help me out with.
Here is the output of glxinfo.  
```
name of display: :2.0
display: :2  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multitexture, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_point_sprite, GL_NV_texgen_reflection, GL_NV_texture_rectangle, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
 
```

And here is fglrxinfo
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.0.6958 Release

```

---

### Post by TedGarvin on 2007-11-03
ok, I couldn't get anything going, and I didn't find any guides that worked, so I gave up. :(   I used this guide [https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver") to revert back to the open source radeon driver.

---

### Post by overdrank on 2007-11-03
> **TedGarvin said:**
> ok, I couldn't get anything going, and I didn't find any guides that worked, so I gave up. :(   I used this guide [https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver") to revert back to the open source radeon driver.

Ok and with that guide do you get direct rendering? I used that guide yesterday on a ATI 9600 and had dri for the desktop effects.

---

### Post by TedGarvin on 2007-11-03
> **overdrank said:**
> Ok and with that guide do you get direct rendering? I used that guide yesterday on a ATI 9600 and had dri for the desktop effects.

Yes, I have direct rendering now.  Any full-screen 3d games run like shite (meaning really low frame rates. Llike 1 every few seconds or so.), but I have compiz and awn running fine.  The text on my browser is a little off, but It will do till I can figure out what to do next.  I don't think it's possible to run everything (compiz and 3d games) with Linux.  Or my 3d card may not be up to snuff to run Slune or Assault cube.  It's a riddle wrapped in an enigma. :)

---


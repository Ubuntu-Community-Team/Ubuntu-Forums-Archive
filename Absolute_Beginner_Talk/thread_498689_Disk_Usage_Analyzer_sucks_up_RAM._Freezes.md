---
title: "Disk Usage Analyzer sucks up RAM. Freezes"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by ZeroWing on 2007-07-11
Ubuntu's Disk Usage Analyzer has been sucking up RAM by the Gig. In around 30 minutes, it takes up 4 Gigs of RAM, plus 7.5 Gigs of Swap. That's a hell of a lot of memory usage, in my opinion. I don't know what caused this, because it worked fine about two months ago. How can I fix this?

 On an unrelated note, Feisty's composite extension is not working. My video card is Nvidia, with all the drivers installed. I've tried to enable it through xorg.conf, but that's not working. I'm trying to get AVN working, but there's a black box around it when it's ran, and I'm assuming that it's from the composite extension not working.

---

### Post by ZeroWing on 2007-07-11
Bump.

---

### Post by ZeroWing on 2007-07-12
GLXinfo for second problem:

 ```
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_framebuffer_sRGB
GLX version: 1.2
GLX extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_SGIX_fbconfig, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce FX 5200/PCI/SSE/3DNOW!
OpenGL version string: 1.2 (2.1.1 NVIDIA 100.14.11)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_imaging, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_window_pos, GL_ARB_vertex_program, GL_ARB_fragment_program, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_texture3D, GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, GL_EXT_texture_lod, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array, 
    GL_IBM_texture_mirrored_repeat, GL_NV_blend_square, 
    GL_NV_texgen_reflection, GL_NV_texture_rectangle, 
    GL_NV_texture_env_combine4, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 
    GL_SGIX_depth_texture, GL_SGIX_shadow

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

 Is says there is no direct rendering... That happens when your running XGL, right? How can I tell if I am? Is there any way of restoring direct rendering?

---

### Post by ZeroWing on 2007-07-12
Seems a little script I made was causing my second problem, but I still need help with the first one...

---

### Post by ZeroWing on 2007-07-12
Bump...

---

### Post by ZeroWing on 2007-07-13
Come on, guys!

---

### Post by ZeroWing on 2007-07-13
<anger>Bump.</anger>

---

### Post by twiceasworn on 2007-07-13
No need to get upset that no one is answering mate.  Anyhow, I would put my money on the fact that there is a memory leak in the program.  But really, I have never used the disk usage analyzer.  What do you need to use the program for exactly that you could not do some other way?

Personally I would just stop using that program as it seems that there is rather nasty bug with it.

---

### Post by ZeroWing on 2007-07-13
> **twiceasworn said:**
> No need to get upset that no one is answering mate.  Anyhow, I would put my money on the fact that there is a memory leak in the program.  But really, I have never used the disk usage analyzer.  What do you need to use the program for exactly that you could not do some other way?

Personally I would just stop using that program as it seems that there is rather nasty bug with it.

 Sorry. This is just a very annoying problem for me.

 I want to be able to see what files are taking a lot of space on my hard drive, so I can clean house a bit, and I don't know of any other program that will let me 'see' what my files are.

---


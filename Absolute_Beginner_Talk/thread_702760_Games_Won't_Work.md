---
title: "Games Won't Work"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by TristanXVX on 2008-02-20
I posted earlier but I think my problem is more general than my last post.

I can't play any 3D games, something with opengl or something isn't working I guess.


Sony Vaio VGN-N395E
Ubuntu 7.10
Intel GMA 950

---

### Post by MasterJS on 2008-02-20
What video card do you have? If you have an ATI, you might have installed XGL. If so, then that is your problem.

---

### Post by TristanXVX on 2008-02-20
It's integrated. Intel

---

### Post by MasterJS on 2008-02-20
Are you running compiz?

---

### Post by TristanXVX on 2008-02-20
Nope

---

### Post by steve-shinn on 2008-02-20
What happens when you type "glxgears" without the quotations in terminal ?

---

### Post by icechen1 on 2008-02-20
> **TristanXVX said:**
> Nope

what is the output of > glxinfo in a terminal (Application>Accessory>Terminal)?

---

### Post by TristanXVX on 2008-02-20
4138 frames in 5.1 seconds = 816.543 FPS
4553 frames in 5.1 seconds = 885.159 FPS
3720 frames in 5.1 seconds = 733.977 FPS

---

### Post by TristanXVX on 2008-02-20
glxinfo


name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_EXT_texture_from_pixmap
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_program, 
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_paletted_texture, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, 
    GL_EXT_texture_rectangle, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_fragment_program, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texgen_reflection, GL_NV_texture_rectangle, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow, GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x3d 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

---

### Post by MasterJS on 2008-02-20
See, if you noticed, you don't have direct rendering. This is the reason you can't run games. Do you have the proprietary drivers for your video card installed?

---

### Post by TristanXVX on 2008-02-20
I have no idea. The thread I made earlier was about direct rendering but it didn't really get any attention. How do I tell what drivers I have installed?

---

### Post by TristanXVX on 2008-02-20
up

---

### Post by TristanXVX on 2008-02-20
up

---

### Post by corevette on 2008-02-20
go to System -> Administrative -> Restricted Drivers Manager
see if there is an option to install your proprietary graphics card driver

if it's not there you might want to try installing envy (which will find a suitable graphics card driver for your graphics card)
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by TristanXVX on 2008-02-21
There were no drivers there other than my wireless. I'll try that program tomorrow, it says I need the live cd to install it?  Room mate is sleeping in there and I'd have to dig around to find it.

---

### Post by TristanXVX on 2008-02-21
It says "There was an error in the installation process. You can see the log file /var/log/envy-installer.log

---

### Post by TristanXVX on 2008-02-21
Up. Not being able to race a penguin down a mountain is ruining my day.

---

### Post by TristanXVX on 2008-02-21
top

---

### Post by TristanXVX on 2008-02-21
up

---

### Post by kool_kat_os on 2008-02-21
> **TristanXVX said:**
> top

i think the correct term is "bump" :)

---

### Post by TristanXVX on 2008-02-21
Won't let this die

---

### Post by TristanXVX on 2008-02-21
bump again

---

### Post by TristanXVX on 2008-02-22
up again

---


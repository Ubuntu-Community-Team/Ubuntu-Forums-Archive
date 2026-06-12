---
title: "(X)(L)ubuntu (MATE) 16.04 LTS testing"
date: 2015-11-03
forum: Apple Hardware Users
---

### Post by xeno74 on 2015-11-03
Hi All,

We started the 16.04 testing last week. Spectre660, zzd10h, and I successfully installed it on our PowerPC NG Amigas.

Link: [forum.hyperion-entertainment.biz]("http://forum.hyperion-entertainment.biz/viewtopic.php?f=35&t=3228")

Screenshots:

[[IMG]https://lh3.googleusercontent.com/-jO7cok2hK4g/VjM-7kFR5UI/AAAAAAAABjI/z2CQ0TtOrHY/w506-h380/ubuntu_MATE_16.04_PowerPC.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/7fsENUkFgWp")

[[IMG]https://lh3.googleusercontent.com/-dR625ttlfLs/VjNBy3-diHI/AAAAAAAABj8/Qnr_PVlq_mQ/w506-h380/ubuntu_MATE_16.04_LTS_Firefox_42.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/hbL2P6J1MB9")

[[IMG]https://lh3.googleusercontent.com/-wgT3s75w_TM/VjNUfC-C57I/AAAAAAAABks/0JpgdLawq5k/w506-h285/Ubuntu-Mate-16.04-Sam460ex.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/eTx9YUTzphW")

[[IMG]https://lh3.googleusercontent.com/-EltYVtSoV0M/VjXsxKYXTPI/AAAAAAAABlo/OaGJ86ULG_s/w506-h380/ubuntu_MATE_16.04_PowerPC_Firefox_42.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/Lh9jUYwyuoR")

I created update instructions for the AmigaONE X1000 last week. Link: [forum.hyperion-entertainment.biz]("http://forum.hyperion-entertainment.biz/viewtopic.php?f=35&t=3228&sid=3a1b6f19de6deb910336a6ff113f6f92")

[IMG]http://zzd10h.amiga-ng.org/X1000/Linux/X1000_16_04_Kernel43rc7.png[/IMG]

PLEASE test it on your PowerPC computer.

Cheers,

Christian

---

### Post by xeno74 on 2015-11-03
FYI: Nouveau & OpenGl working on PMAC G5 :-)

[QUOTE=Peter Saisanas]
Hi,
Just thought i should share some news that since installing mesa 11.0.4 from the sid repo (libg1-mesa-dri & dependencies), OpenGL is now working for nouveau and ppc.
Tested on PMAC 11.2 (G5 Quad + Quadro FX4500 config).
I wouldn't say it is blistering fast, just performance is on par with other nouveau supported hardware rendering. Not ideal, but its a great start to improve on. And yeah, i woudnt try be playing opengl games with nouveau, mesa & ppc for now... perhaps for a while.
Been using it for about a week or so.

Also, nouveau since kernel 4.3.0-rc6 can extract the vbios from openfirmware fcode rom correctly.
Mesa 11.0.4 runs stable enough on kernel 4.3.0 and 3.18.16 (perhaps slightly better). Can actually get gnome desktop running (slowly) with 3.18.16 for a minute before crashing...... I use xfce desktop, window compositing and transparancies seem to work well enough.

I believe since mesa 11.0.3, there has been a fix by developer Ilia Mirkin for "nv30: always go through translate module on big-endian".

Now Quadro FX4500 is a nv47 class gpu, but i guess nv30 seems to apply for this as well.

Tested with glxinfo & glxgears.

In glxgears getting about 380fps without vsync.

glxinfo log below:[/quote]

```
psaisanas@pmac-g5-quad:~$ glxinfo
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile,
    GLX_ARB_fbconfig_float, GLX_ARB_framebuffer_sRGB, GLX_ARB_multisample,
    GLX_EXT_create_context_es2_profile, GLX_EXT_framebuffer_sRGB,
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer,
    GLX_OML_swap_method, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, GLX_SGI_swap_control
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile,
    GLX_ARB_create_context_robustness, GLX_ARB_fbconfig_float,
    GLX_ARB_framebuffer_sRGB, GLX_ARB_get_proc_address, GLX_ARB_multisample,
    GLX_EXT_buffer_age, GLX_EXT_create_context_es2_profile,
    GLX_EXT_fbconfig_packed_float, GLX_EXT_framebuffer_sRGB,
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer,
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer,
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGIX_visual_select_group, GLX_SGI_make_current_read,
    GLX_SGI_swap_control, GLX_SGI_video_sync
GLX version: 1.4
GLX extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile,
    GLX_ARB_fbconfig_float, GLX_ARB_framebuffer_sRGB,
    GLX_ARB_get_proc_address, GLX_ARB_multisample,
    GLX_EXT_create_context_es2_profile, GLX_EXT_framebuffer_sRGB,
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer,
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer,
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGIX_visual_select_group, GLX_SGI_make_current_read,
    GLX_SGI_swap_control, GLX_SGI_video_sync
OpenGL vendor string: nouveau
OpenGL renderer string: Gallium 0.4 on NV47
OpenGL version string: 2.0 Mesa 11.0.4
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_AMD_shader_trinary_minmax, GL_ANGLE_texture_compression_dxt3,
    GL_ANGLE_texture_compression_dxt5, GL_APPLE_packed_pixels,
    GL_APPLE_vertex_array_object, GL_ARB_ES2_compatibility,
    GL_ARB_buffer_storage, GL_ARB_clear_buffer_object,
    GL_ARB_compressed_texture_pixel_storage, GL_ARB_copy_buffer,
    GL_ARB_debug_output, GL_ARB_depth_clamp, GL_ARB_depth_texture,
    GL_ARB_draw_buffers, GL_ARB_draw_elements_base_vertex,
    GL_ARB_explicit_attrib_location, GL_ARB_explicit_uniform_location,
    GL_ARB_fragment_coord_conventions, GL_ARB_fragment_program,
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader,
    GL_ARB_get_program_binary, GL_ARB_get_texture_sub_image,
    GL_ARB_half_float_pixel, GL_ARB_half_float_vertex,
    GL_ARB_internalformat_query, GL_ARB_invalidate_subdata,
    GL_ARB_map_buffer_alignment, GL_ARB_map_buffer_range, GL_ARB_multi_bind,
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query,
    GL_ARB_occlusion_query2, GL_ARB_pixel_buffer_object,
    GL_ARB_point_parameters, GL_ARB_point_sprite,
    GL_ARB_program_interface_query, GL_ARB_provoking_vertex,
    GL_ARB_robustness, GL_ARB_sampler_objects, GL_ARB_separate_shader_objects,
    GL_ARB_shader_objects, GL_ARB_shading_language_100, GL_ARB_shadow,
    GL_ARB_sync, GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirror_clamp_to_edge,
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two,
    GL_ARB_texture_rectangle, GL_ARB_texture_storage, GL_ARB_texture_swizzle,
    GL_ARB_timer_query, GL_ARB_transpose_matrix, GL_ARB_vertex_array_bgra,
    GL_ARB_vertex_array_object, GL_ARB_vertex_attrib_binding,
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader,
    GL_ARB_window_pos, GL_ATI_blend_equation_separate, GL_ATI_draw_buffers,
    GL_ATI_separate_stencil, GL_ATI_texture_env_combine3,
    GL_ATI_texture_mirror_once, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color,
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array,
    GL_EXT_copy_texture, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements,
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_object,
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels,
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters,
    GL_EXT_polygon_offset, GL_EXT_provoking_vertex, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap,
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D,
    GL_EXT_texture_compression_dxt1, GL_EXT_texture_compression_s3tc,
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_swizzle,
    GL_EXT_timer_query, GL_EXT_vertex_array, GL_EXT_vertex_array_bgra,
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip,
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate,
    GL_KHR_context_flush_control, GL_KHR_debug, GL_MESA_pack_invert,
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_conditional_render,
    GL_NV_depth_clamp, GL_NV_fog_distance, GL_NV_light_max_exponent,
    GL_NV_packed_depth_stencil, GL_NV_primitive_restart,
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4,
    GL_NV_texture_rectangle, GL_OES_EGL_image, GL_OES_read_format,
    GL_S3_s3tc, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

OpenGL ES profile version string: OpenGL ES 2.0 Mesa 11.0.4
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 1.0.16
OpenGL ES profile extensions:
    GL_ANGLE_texture_compression_dxt3, GL_ANGLE_texture_compression_dxt5,
    GL_APPLE_texture_max_level, GL_EXT_blend_minmax,
    GL_EXT_discard_framebuffer, GL_EXT_draw_buffers, GL_EXT_map_buffer_range,
    GL_EXT_multi_draw_arrays, GL_EXT_read_format_bgra,
    GL_EXT_separate_shader_objects, GL_EXT_texture_compression_dxt1,
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_format_BGRA8888,
    GL_EXT_texture_type_2_10_10_10_REV, GL_EXT_unpack_subimage,
    GL_KHR_context_flush_control, GL_NV_draw_buffers,
    GL_NV_fbo_color_attachments, GL_NV_read_buffer, GL_NV_read_depth,
    GL_NV_read_depth_stencil, GL_NV_read_stencil, GL_OES_EGL_image,
    GL_OES_EGL_image_external, GL_OES_EGL_sync, GL_OES_depth24,
    GL_OES_depth_texture, GL_OES_element_index_uint, GL_OES_fbo_render_mipmap,
    GL_OES_get_program_binary, GL_OES_mapbuffer, GL_OES_packed_depth_stencil,
    GL_OES_rgb8_rgba8, GL_OES_stencil8, GL_OES_surfaceless_context,
    GL_OES_texture_3D, GL_OES_texture_npot, GL_OES_vertex_array_object

96 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0 0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0 0 0 None
0x134 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0 0 0 None
0x135 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16 0 0 Slow
0x136 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0 0 0 None
0x137 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16 0 0 Slow
0x138 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0 0 0 None
0x139 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16 0 0 Slow
0x13a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0 0 0 None
0x13b 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16 0 0 Slow
0x13c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0 0 0 None
0x13d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16 0 0 Slow
0x13e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0 0 0 None
0x13f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16 0 0 Slow
0x140 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0 0 0 None
0x141 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16 0 0 Slow
0x142 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0 0 0 None
0x143 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16 0 0 Slow
0x144 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0 0 0 None
0x145 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16 0 0 Slow
0x146 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0 0 0 None
0x147 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16 0 0 Slow
0x148 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16 0 0 Slow
0x149 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16 0 0 Slow
0x14a 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0 0 0 None
0x14b 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0 0 0 Slow
0x14c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0 0 0 None
0x14d 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0 0 0 Slow
0x14e 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0 0 0 None
0x14f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0 0 0 Slow
0x150 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0 0 0 None
0x151 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0 0 0 Slow
0x152 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0 0 0 None
0x153 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0 0 0 Slow
0x154 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0 0 0 None
0x155 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0 0 0 Slow
0x156 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0 0 0 None
0x157 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0 0 0 Slow
0x158 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0 0 0 None
0x159 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0 0 0 Slow
0x15a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0 0 0 None
0x15b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0 0 0 Slow
0x15c 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0 0 0 None
0x15d 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0 0 0 Slow
0x15e 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0 0 0 None
0x15f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0 0 0 Slow
0x160 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0 0 0 None
0x161 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0 0 0 Slow
0x162 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0 0 0 None
0x163 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16 0 0 Slow
0x164 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0 0 0 None
0x165 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16 0 0 Slow
0x166 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0 0 0 None
0x167 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16 0 0 Slow
0x168 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0 0 0 None
0x169 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16 0 0 Slow
0x16a 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0 0 0 None
0x16b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16 0 0 Slow
0x16c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0 0 0 None
0x16d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16 0 0 Slow
0x16e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0 0 0 None
0x16f 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16 0 0 Slow
0x170 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0 0 0 None
0x171 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16 0 0 Slow
0x172 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0 0 0 None
0x173 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16 0 0 Slow
0x174 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0 0 0 None
0x175 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16 0 0 Slow
0x176 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16 0 0 Slow
0x177 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0 0 0 None
0x178 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16 0 0 Slow
0x179 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0 0 0 None
0x17a 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0 0 0 Slow
0x17b 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0 0 0 None
0x17c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0 0 0 Slow
0x17d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0 0 0 None
0x17e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0 0 0 Slow
0x17f 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0 0 0 None
0x180 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0 0 0 Slow
0x181 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0 0 0 None
0x182 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0 0 0 Slow
0x183 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0 0 0 None
0x184 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0 0 0 Slow
0x185 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0 0 0 None
0x186 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0 0 0 Slow
0x187 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0 0 0 None
0x188 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0 0 0 Slow
0x189 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0 0 0 None
0x18a 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0 0 0 Slow
0x18b 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0 0 0 None
0x18c 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0 0 0 Slow
0x18d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0 0 0 None
0x18e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0 0 0 Slow
0x18f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0 0 0 None
0x190 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0 0 0 Slow
0x0a3 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0 0 0 None

144 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x0a4 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0 0 0 None
0x0a5 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16 0 0 Slow
0x0a6 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0 0 0 None
0x0a7 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16 0 0 Slow
0x0a8 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0 0 0 None
0x0a9 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16 0 0 Slow
0x0aa 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0 0 0 None
0x0ab 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16 0 0 Slow
0x0ac 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0 0 0 None
0x0ad 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16 0 0 Slow
0x0ae 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0 0 0 None
0x0af 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16 0 0 Slow
0x0b0 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0 0 0 None
0x0b1 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16 0 0 Slow
0x0b2 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0 0 0 None
0x0b3 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16 0 0 Slow
0x0b4 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0 0 0 None
0x0b5 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16 0 0 Slow
0x0b6 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0 0 0 None
0x0b7 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16 0 0 Slow
0x0b8 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0 0 0 None
0x0b9 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16 0 0 Slow
0x0ba 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0 0 0 None
0x0bb 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16 0 0 Slow
0x0bc 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0 0 0 None
0x0bd 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0 0 0 Slow
0x0be 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0 0 0 None
0x0bf 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0 0 0 Slow
0x0c0 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0 0 0 None
0x0c1 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0 0 0 Slow
0x0c2 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0 0 0 None
0x0c3 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0 0 0 Slow
0x0c4 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0 0 0 None
0x0c5 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0 0 0 Slow
0x0c6 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0 0 0 None
0x0c7 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0 0 0 Slow
0x0c8 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0 0 0 None
0x0c9 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0 0 0 Slow
0x0ca 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0 0 0 None
0x0cb 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0 0 0 Slow
0x0cc 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0 0 0 None
0x0cd 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0 0 0 Slow
0x0ce 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0 0 0 None
0x0cf 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0 0 0 Slow
0x0d0 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0 0 0 None
0x0d1 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0 0 0 Slow
0x0d2 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0 0 0 None
0x0d3 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0 0 0 Slow
0x0d4  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0 0 0 None
0x0d5  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0 0 0 Slow
0x0d6  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0 0 0 None
0x0d7  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0 0 0 Slow
0x0d8  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0 0 0 None
0x0d9  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0 0 0 Slow
0x0da  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0 0 0 None
0x0db  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0 16 16 16  0 0 0 Slow
0x0dc  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0 0 0 None
0x0dd  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0 0 0 Slow
0x0de  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0 0 0 None
0x0df  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0 0 0 Slow
0x0e0  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0 0 0 None
0x0e1  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0 16 16 16  0 0 0 Slow
0x0e2  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0 0 0 None
0x0e3  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0 0 0 Slow
0x0e4  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0 0 0 None
0x0e5  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0 0 0 Slow
0x0e6  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0 0 0 None
0x0e7  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8 16 16 16  0 0 0 Slow
0x0e8  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0 0 0 None
0x0e9  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0 0 0 Slow
0x0ea  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0 0 0 None
0x0eb  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0 0 0 Slow
0x0ec 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0 0 0 None
0x0ed 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16 0 0 Slow
0x0ee 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0 0 0 None
0x0ef 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16 0 0 Slow
0x0f0 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0 0 0 None
0x0f1 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16 0 0 Slow
0x0f2 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0 0 0 None
0x0f3 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16 0 0 Slow
0x0f4 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0 0 0 None
0x0f5 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16 0 0 Slow
0x0f6 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0 0 0 None
0x0f7 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16 0 0 Slow
0x0f8 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0 0 0 None
0x0f9 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16 0 0 Slow
0x0fa 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0 0 0 None
0x0fb 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16 0 0 Slow
0x0fc 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0 0 0 None
0x0fd 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16 0 0 Slow
0x0fe 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0 0 0 None
0x0ff 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16 0 0 Slow
0x100 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0 0 0 None
0x101 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16 0 0 Slow
0x102 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0 0 0 None
0x103 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16 0 0 Slow
0x104 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0 0 0 None
0x105 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0 0 0 Slow
0x106 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0 0 0 None
0x107 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0 0 0 Slow
0x108 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0 0 0 None
0x109 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0 0 0 Slow
0x10a 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0 0 0 None
0x10b 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0 0 0 Slow
0x10c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0 0 0 None
0x10d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0 0 0 Slow
0x10e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0 0 0 None
0x10f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0 0 0 Slow
0x110 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0 0 0 None
0x111 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0 0 0 Slow
0x112 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0 0 0 None
0x113 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0 0 0 Slow
0x114 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0 0 0 None
0x115 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0 0 0 Slow
0x116 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0 0 0 None
0x117 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0 0 0 Slow
0x118 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0 0 0 None
0x119 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0 0 0 Slow
0x11a 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0 0 0 None
0x11b 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0 0 0 Slow
0x11c  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0 0 0 None
0x11d  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0 0 0 Slow
0x11e  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0 0 0 None
0x11f  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0 0 0 Slow
0x120  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0 0 0 None
0x121  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0 0 0 Slow
0x122  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0 0 0 None
0x123  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0 16 16 16  0 0 0 Slow
0x124  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0 0 0 None
0x125  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0 0 0 Slow
0x126  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0 0 0 None
0x127  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0 0 0 Slow
0x128  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0 0 0 None
0x129  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0 16 16 16  0 0 0 Slow
0x12a  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0 0 0 None
0x12b  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0 0 0 Slow
0x12c  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0 0 0 None
0x12d  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0 0 0 Slow
0x12e  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0 0 0 None
0x12f  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8 16 16 16  0 0 0 Slow
0x130  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0 0 0 None
0x131  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0 0 0 Slow
0x132  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0 0 0 None
0x133  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0 0 0 Slow 

```

---

### Post by luigiburdo on 2015-11-05
Letz hope ... Christian,
for now 16.04 dont work on quad in my configuration

---

### Post by Roger-H on 2015-11-05
Where can I get the ISO for this?

---

### Post by abtabt on 2015-11-06
> **Roger-H said:**
> Where can I get the ISO for this?

no iso 16.04

 download 15.10 final

[https://ubuntu-mate.org/wily/](https://ubuntu-mate.org/wily/)

and upgrade from installed 15.10 see first post with link 

Imac 500Mhz   running  with 16.04

---

### Post by xeno74 on 2015-11-09
Compiz works again on ubuntu MATE 16.04 LTS PowerPC!&#65279;

[[IMG]https://lh3.googleusercontent.com/-U17u5VaNzEw/VkC2R95_zFI/AAAAAAAABnU/_vXfpAnR23U/w506-h380/ubuntu_MATE_16.04_LTS_PowerPC_Compiz.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/GmKTjDw95fr")

---

### Post by rican-linux on 2015-11-09
It looks like the Mesa devs have some of the PPC bugs fixed in version 11.0.3 see **[release notes]("http://www.mesa3d.org/relnotes/11.0.3.html")**.

16.04 is running with **[version 11.0.4]("https://launchpad.net/ubuntu/xenial/+source/mesa")**

I am loading Debian and Sid then trying Xenial on my iBook to test.

---

### Post by Roger-H on 2015-11-09
If you have a PowerPC that cannot boot the Ubuntu MATE 15.10 live image, what is the easiest way to install that and upgrade to the 16.04 alpha?

---

### Post by abtabt on 2015-11-10
> **Roger-H said:**
> If you have a PowerPC that cannot boot the Ubuntu MATE 15.10 live image, what is the easiest way to install that and upgrade to the 16.04 alpha?

USB or FW disk  


[https://ubuntu-mate.org/xenial/](https://ubuntu-mate.org/xenial/)

[http://cdimage.ubuntu.com/ubuntu-mate/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-mate/daily-live/current/)

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

---

### Post by xeno74 on 2015-11-10
FYI: Midori 0.5.11 is available for ubuntu MATE 16.04 LTS PowerPC. I love this WebKit web browser.&#65279;

[[IMG]https://lh3.googleusercontent.com/-s36BZeM4A0E/VkIADCsf_pI/AAAAAAAABoA/ldsXxVxE6Qc/w506-h380/Midori_0.5.11_ubuntu_MATE_16.04_PowerPC.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/6ZXfz8K5nxw")

---

### Post by rican-linux on 2015-11-11
I running Xenial on my iBook G4. Sadly I do not have 3D acceleration. I am still getting the r300 driver error

```
rican-linux@lubuntu-ppc:~$ LIBGL_DEBUG=verbose glxinfo |grep render
libGL: OpenDriver: trying /usr/lib/powerpc-linux-gnu/dri/tls/r300_dri.so
libGL: OpenDriver: trying /usr/lib/powerpc-linux-gnu/dri/r300_dri.so
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: r300
libGL: OpenDriver: trying /usr/lib/powerpc-linux-gnu/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/powerpc-linux-gnu/dri/swrast_dri.so
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
Error: couldn't find RGB GLX visual or fbconfig

```

---

### Post by Roger-H on 2015-11-11
I didn't have any luck with the 16.04 live image on my iMac G4, either. During the boot process it just stops, even with the video=ofonly flag (which is how I am able to run the Lubuntu 14.04.2 live image).

---

### Post by abtabt on 2015-11-11
> **Roger-H said:**
> I didn't have any luck with the 16.04 live image on my iMac G4, either. During the boot process it just stops, even with the video=ofonly flag (which is how I am able to run the Lubuntu 14.04.2 live image).

have you more info about imac g4  ?

its more than one model 

[http://www.everymac.com/systems/apple/imac/index-imac.html](http://www.everymac.com/systems/apple/imac/index-imac.html)

 i have not use video=ofonly for a longtime, I use at boot      live nomodeset video=offb:off single        and  cd stop spinning REURN key then 
type modprobe nvidiafb  And if you get ok then you have promt        etc 

i have use this from 12.04 to 15.10 Lubuntu ,Ubutu-mate 

now tested daily ubuntu-mate 16.04 20151111

---

### Post by xeno74 on 2015-11-21
ubuntu MATE 16.04 LTS PowerPC with the RC1 of kernel 4.4. :-)&#65279;

[[IMG]https://lh3.googleusercontent.com/-OubiYNODQec/VlCLVjAymrI/AAAAAAAABrM/S0hZAkZkIMA/w506-h380/ubuntu_MATE_16.04_LTS_PowerPC_kernel_4.4-rc1.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/Kjh2LPPa4KV")

---

### Post by xeno74 on 2015-11-23
ubuntu MATE 16.04 LTS PowerPC with the kernel 4.4 RC2 and E-UAE JIT PowerPC:

[[IMG]https://lh3.googleusercontent.com/-AaBlWsYQccU/VlLetSHL7LI/AAAAAAAABr8/SpUgV9ztB3I/w506-h380/ubuntu_MATE_16.04_LTS_PowerPC_kernel_4.4-rc2_E-UAE_JIT.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/1tQcbQ5rVDE")

---

### Post by luigiburdo on 2015-11-24
Here on quad ... black screen 
will investigate better on 16.04

---

### Post by xeno74 on 2015-12-03
FYI:

YouTube video about ubuntu MATE 15.10 on an Apple Power Mac G5.

Link: [https://youtu.be/NJu_KmN3MSI](https://youtu.be/NJu_KmN3MSI)

-- Christian

---

### Post by xeno74 on 2015-12-08
ubuntu MATE 16.04 LTS PowerPC with kernel 4.4-rc4 :-)&#65279;

[[IMG]https://lh3.googleusercontent.com/-zHxMcZXLRR0/VmXHSIHY02I/AAAAAAAABuQ/w950ft2vQGU/w506-h380/kernel_4.4-rc4-2_ubuntu_MATE_16.04_LTS_PowerPC.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/F3MfUVaErB5")

**PLEASE** test ubuntu MATE 16.04 LTS PowerPC!

---

### Post by luigiburdo on 2015-12-08
On Quad G5 the 16.04 working as the 15.10 only FB and no audio . i will make a new kernel build with last release hope something will change .
Lets hope in X5000

---

### Post by este.el.paz on 2015-12-08
> **abtabt said:**
> 
 i have not use video=ofonly for a longtime, I use at boot      live nomodeset video=offb:off single        and  cd stop spinning REURN key then 
type modprobe nvidiafb  And if you get ok then you have promt        etc 
now tested daily ubuntu-mate 16.04 20151111

Folks:

I'm with Luigiburdo & Roger-H on this one . . . downloaded the daily of U-MATE 16.04 on my PowerMac 3,1 Sawtooth, now with upgraded cpu running 800 MHz . . . .  I tried the boot params that worked for 14.04 "live-nosplash-powerpc videofb:1024x768-32@60"  as well as trying abtabt's suggestions . . . .  Each time ***huge*** list of SQUASHFS errors and a bunch of I/O errors . . . .  I think I tried yesterday's daily and then zsync'd it again today . . . yesterday's got me to a beautiful black screen that occasionally "pulsed" or, um "throbbed" . . . depending on which word you like better . . . .  Today just gave me a verbose log that basically . . . "crashed."  Trying abtabt's boot params "live nomodeset video=offb:off single"  [just like that, no hyphens] . . . brought me the same long list of errors, the cd didn't stop spinning . . . no chance to hit RETURN and try to "modprobe radeonfb" . . . probably, in my case . . . with the ATI RAGE video card, seemed to work with "radeon" . . . .

e.

---

### Post by luigiburdo on 2015-12-09
Gianluca Renzi one of the guy who make the permedia2 drivers for Apus machine confirmed that on debian sid all issue was resolve in ppc side . he have a quad with radeonhd . now on sid last mesa are working too on g5 abd look like without issue.
many issue was resoved from kernel 4.3 and up... we have to hope that mate swap soon to new kernel. right now is 4.2.2x.

---

### Post by xeno74 on 2015-12-09
> **luigiburdo said:**
> Gianluca Renzi one of the guy who make the permedia2 drivers for Apus machine confirmed that on debian sid all issue was resolve in ppc side . he have a quad with radeonhd . now on sid last mesa are working too on g5 abd look like without issue.
many issue was resoved from kernel 4.3 and up... we have to hope that mate swap soon to new kernel. right now is 4.2.2x.

Hi all,

I have replaced the **unofficial Mesa 10.0.4** ([http://www.supertuxkart-amiga.de/amiga/mesalib-unofficial.html](http://www.supertuxkart-amiga.de/amiga/mesalib-unofficial.html)) with the **official Mesa 11.0.6** on **ubuntu MATE 16.04 PowerPC** and on **Debian Sid PowerPC** today.

With **32-bit** there _isn't_ 3D acceleration available:

```

OpenGL
Vendor                                Unknown
Renderer                            Unknown
Version                               Unknown
Direct Rendering                No 

```

I added **DefaultDepth    16** to the section **Screen** in the **xorg.conf**.

After that it works but unfortunately with _wrong colors_ and it _isn't as fast as_ the unofficial Mesa 10.0.4. 

```

OpenGL
Vendor                                Xorg
Renderer                            Gallium 0.4 on AMD BARTS (DRM 2.43.0)
Version                               3.0 Mesa 11.0.6
Direct Rendering                Yes

```

Cheers,

Christian

---

### Post by luigiburdo on 2015-12-10
dho christian :-(
i hope they fixed the quad g5 issue... and not only write to me that is something fixed and is not fixed like as supposed to do

---

### Post by Peter_Saisanas on 2015-12-11
I'll take the bait!

G5 Quad
Quadro FX4500
Custom Kernel (4.4.0-rc2)
Debian Stretch (Testing repo)
Mesa 11.0.6

KMS is working with nouveau and nv47 class GPU.
2D H/W accel is working with nouveau & Xorg 1:7.7+12.
3D H/W accel is working with nouveau & mesa 11.0.6.

Granted, im running Debian, but theres no reason why the same config cant be made to work under Ubuntu.

Don't pass kernel options without understanding what they do or what the reprecussions are of applying them.
Just because mesa doesnt work on someones oddball config, doesnt mean it doesnt work for anyone else.
Dont make a blanket statement like that without being 100% sure you know what you are talking about.

Screenshot below with glxgears, extreme tux racer and chromium bsu running at the same time with firefox & xfce compositing desktop

Proof you say?

```
psaisanas@pmac-g5-quad:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_fbconfig_float, GLX_ARB_framebuffer_sRGB, GLX_ARB_multisample, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, GLX_SGI_swap_control
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_fbconfig_float, 
    GLX_ARB_framebuffer_sRGB, GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_buffer_age, GLX_EXT_create_context_es2_profile, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync
GLX version: 1.4
GLX extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_fbconfig_float, GLX_ARB_framebuffer_sRGB, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, 
    GLX_EXT_create_context_es2_profile, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync
OpenGL vendor string: nouveau
OpenGL renderer string: Gallium 0.4 on NV47
OpenGL version string: 2.0 Mesa 11.0.6
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_AMD_shader_trinary_minmax, GL_ANGLE_texture_compression_dxt3, 
    GL_ANGLE_texture_compression_dxt5, GL_APPLE_packed_pixels, 
    GL_APPLE_vertex_array_object, GL_ARB_ES2_compatibility, 
    GL_ARB_buffer_storage, GL_ARB_clear_buffer_object, 
    GL_ARB_compressed_texture_pixel_storage, GL_ARB_copy_buffer, 
    GL_ARB_debug_output, GL_ARB_depth_clamp, GL_ARB_depth_texture, 
    GL_ARB_draw_buffers, GL_ARB_draw_elements_base_vertex, 
    GL_ARB_explicit_attrib_location, GL_ARB_explicit_uniform_location, 
    GL_ARB_fragment_coord_conventions, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_get_program_binary, GL_ARB_get_texture_sub_image, 
    GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, 
    GL_ARB_internalformat_query, GL_ARB_invalidate_subdata, 
    GL_ARB_map_buffer_alignment, GL_ARB_map_buffer_range, GL_ARB_multi_bind, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_occlusion_query2, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_program_interface_query, GL_ARB_provoking_vertex, 
    GL_ARB_robustness, GL_ARB_sampler_objects, GL_ARB_separate_shader_objects, 
    GL_ARB_shader_objects, GL_ARB_shading_language_100, GL_ARB_shadow, 
    GL_ARB_sync, GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirror_clamp_to_edge, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_texture_storage, GL_ARB_texture_swizzle, 
    GL_ARB_timer_query, GL_ARB_transpose_matrix, GL_ARB_vertex_array_bgra, 
    GL_ARB_vertex_array_object, GL_ARB_vertex_attrib_binding, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_ATI_blend_equation_separate, GL_ATI_draw_buffers, 
    GL_ATI_separate_stencil, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_copy_texture, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_object, 
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_provoking_vertex, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_compression_dxt1, GL_EXT_texture_compression_s3tc, 
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_swizzle, 
    GL_EXT_timer_query, GL_EXT_vertex_array, GL_EXT_vertex_array_bgra, 
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_KHR_context_flush_control, GL_KHR_debug, GL_MESA_pack_invert, 
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_conditional_render, 
    GL_NV_depth_clamp, GL_NV_fog_distance, GL_NV_light_max_exponent, 
    GL_NV_packed_depth_stencil, GL_NV_primitive_restart, 
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, 
    GL_NV_texture_rectangle, GL_OES_EGL_image, GL_OES_read_format, 
    GL_S3_s3tc, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

OpenGL ES profile version string: OpenGL ES 2.0 Mesa 11.0.6
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 1.0.16
OpenGL ES profile extensions:
    GL_ANGLE_texture_compression_dxt3, GL_ANGLE_texture_compression_dxt5, 
    GL_APPLE_texture_max_level, GL_EXT_blend_minmax, 
    GL_EXT_discard_framebuffer, GL_EXT_draw_buffers, GL_EXT_map_buffer_range, 
    GL_EXT_multi_draw_arrays, GL_EXT_read_format_bgra, 
    GL_EXT_separate_shader_objects, GL_EXT_texture_compression_dxt1, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_format_BGRA8888, 
    GL_EXT_texture_type_2_10_10_10_REV, GL_EXT_unpack_subimage, 
    GL_KHR_context_flush_control, GL_NV_draw_buffers, 
    GL_NV_fbo_color_attachments, GL_NV_read_buffer, GL_NV_read_depth, 
    GL_NV_read_depth_stencil, GL_NV_read_stencil, GL_OES_EGL_image, 
    GL_OES_EGL_image_external, GL_OES_EGL_sync, GL_OES_depth24, 
    GL_OES_depth_texture, GL_OES_element_index_uint, GL_OES_fbo_render_mipmap, 
    GL_OES_get_program_binary, GL_OES_mapbuffer, GL_OES_packed_depth_stencil, 
    GL_OES_rgb8_rgba8, GL_OES_stencil8, GL_OES_surfaceless_context, 
    GL_OES_texture_3D, GL_OES_texture_npot, GL_OES_vertex_array_object

96 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x134 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x135 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x136 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x137 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x138 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x139 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x13a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x13b 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x13c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x13d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x13e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x13f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x140 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x141 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x142 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x143 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x144 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x145 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x146 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x147 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x148 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x149 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x14a 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x14b 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x14c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x14d 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x14e 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x14f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x150 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x151 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x152 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x153 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x154 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x155 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x156 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x157 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x158 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x159 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x15a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x15b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x15c 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x15d 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x15e 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x15f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x160 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x161 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x162 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x163 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x164 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x165 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x166 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x167 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x168 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x169 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x16a 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x16b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x16c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x16d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x16e 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x16f 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x170 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x171 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x172 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x173 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x174 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x175 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x176 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x177 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x178 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x179 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x17a 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x17b 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x17c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x17d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x17e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x17f 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x180 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x181 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x182 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x183 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x184 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x185 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x186 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x187 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x188 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x189 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x18a 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x18b 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x18c 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x18d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x18e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x18f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x190 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0a3 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None

144 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x0a4 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a5 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0a6 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a7 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0a8 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a9 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0aa 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x0ab 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x0ac 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x0ad 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x0ae 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x0af 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x0b0 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0b1 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0b2 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0b3 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0b4 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0b5 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0b6 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0b7 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0b8 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0b9 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0ba 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0bb 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0bc 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0bd 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0be 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0bf 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0c0 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0c1 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0c2 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0c3 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0c4 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0c5 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0c6 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0c7 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0c8 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0c9 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0ca 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0cb 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0cc 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0cd 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0ce 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0cf 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0d0 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0d1 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0d2 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0d3 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0d4  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0d5  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0d6  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0d7  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0d8  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0d9  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0da  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0db  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0dc  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0dd  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0de  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0df  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0e0  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0e1  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0e2  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0e3  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0e4  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0e5  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0e6  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0e7  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0e8  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0e9  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0ea  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0eb  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0ec 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0ed 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0ee 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0ef 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0f0 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0f1 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0f2 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x0f3 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x0f4 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x0f5 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x0f6 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0  0  0  0  0  0 0 None
0x0f7 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 16  0 16 16 16 16  0 0 Slow
0x0f8 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0f9 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0fa 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0fb 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0fc 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0fd 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0fe 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0ff 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x100 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x101 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x102 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x103 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x104 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x105 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x106 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x107 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x108 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x109 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x10a 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x10b 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x10c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x10d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x10e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0  0  0  0  0  0 0 None
0x10f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x110 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x111 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x112 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x113 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x114 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x115 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x116 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x117 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x118 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x119 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x11a 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x11b 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x11c  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x11d  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x11e  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x11f  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x120  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x121  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x122  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x123  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x124  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x125  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x126  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x127  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x128  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x129  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x12a  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x12b  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x12c  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x12d  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x12e  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x12f  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x130  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x131  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x132  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x133  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow

```

[ATTACH=CONFIG]266090[/ATTACH]

---

### Post by xeno74 on 2015-12-11
> **Peter_Saisanas said:**
> 

KMS is working with nouveau and nv47 class GPU.
2D H/W accel is working with nouveau & Xorg 1:7.7+12.
3D H/W accel is working with nouveau & mesa 11.0.6.



Hi Peter,

Could you please post your kernel config? I have wrong colors with my Radeon HD graphics card. Any hints because of the wrong colors?

Thanks,

Christian

---

### Post by Peter_Saisanas on 2015-12-11
Hi Christian, I doubt there are many surprises with my kernel config. However i have set it up specifically for a the pmac 11.2 machines and what works with nouveau.

```
#
# Automatically generated file; DO NOT EDIT.
# Linux/powerpc 4.4.0-rc2-powerpc64 Kernel Configuration
#
CONFIG_PPC64=y

#
# Processor support
#
CONFIG_PPC_BOOK3S_64=y
# CONFIG_PPC_BOOK3E_64 is not set
# CONFIG_GENERIC_CPU is not set
# CONFIG_CELL_CPU is not set
CONFIG_POWER4_CPU=y
# CONFIG_POWER5_CPU is not set
# CONFIG_POWER6_CPU is not set
# CONFIG_POWER7_CPU is not set
# CONFIG_POWER8_CPU is not set
CONFIG_PPC_BOOK3S=y
CONFIG_PPC_FPU=y
CONFIG_ALTIVEC=y
CONFIG_VSX=y
# CONFIG_PPC_ICSWX is not set
CONFIG_PPC_STD_MMU=y
CONFIG_PPC_STD_MMU_64=y
CONFIG_PPC_MM_SLICES=y
CONFIG_PPC_HAVE_PMU_SUPPORT=y
CONFIG_PPC_PERF_CTRS=y
CONFIG_SMP=y
CONFIG_NR_CPUS=4
# CONFIG_PPC_DOORBELL is not set
CONFIG_VDSO32=y
CONFIG_CPU_BIG_ENDIAN=y
# CONFIG_CPU_LITTLE_ENDIAN is not set
CONFIG_64BIT=y
CONFIG_WORD_SIZE=64
CONFIG_ARCH_PHYS_ADDR_T_64BIT=y
CONFIG_ARCH_DMA_ADDR_T_64BIT=y
CONFIG_MMU=y
CONFIG_HAVE_SETUP_PER_CPU_AREA=y
CONFIG_NEED_PER_CPU_EMBED_FIRST_CHUNK=y
CONFIG_NR_IRQS=512
CONFIG_STACKTRACE_SUPPORT=y
CONFIG_HAVE_LATENCYTOP_SUPPORT=y
CONFIG_TRACE_IRQFLAGS_SUPPORT=y
CONFIG_LOCKDEP_SUPPORT=y
CONFIG_RWSEM_XCHGADD_ALGORITHM=y
CONFIG_ARCH_HAS_ILOG2_U32=y
CONFIG_ARCH_HAS_ILOG2_U64=y
CONFIG_GENERIC_HWEIGHT=y
CONFIG_ARCH_HAS_DMA_SET_COHERENT_MASK=y
CONFIG_PPC=y
# CONFIG_GENERIC_CSUM is not set
CONFIG_EARLY_PRINTK=y
CONFIG_PANIC_TIMEOUT=180
CONFIG_COMPAT=y
CONFIG_SYSVIPC_COMPAT=y
CONFIG_SCHED_OMIT_FRAME_POINTER=y
CONFIG_ARCH_MAY_HAVE_PC_FDC=y
# CONFIG_PPC_UDBG_16550 is not set
CONFIG_GENERIC_TBSYNC=y
CONFIG_AUDIT_ARCH=y
CONFIG_GENERIC_BUG=y
# CONFIG_EPAPR_BOOT is not set
# CONFIG_DEFAULT_UIMAGE is not set
CONFIG_ARCH_HIBERNATION_POSSIBLE=y
# CONFIG_PPC_DCR_NATIVE is not set
# CONFIG_PPC_DCR_MMIO is not set
# CONFIG_PPC_OF_PLATFORM_PCI is not set
CONFIG_ARCH_SUPPORTS_DEBUG_PAGEALLOC=y
CONFIG_ARCH_SUPPORTS_UPROBES=y
CONFIG_PPC_EMULATE_SSTEP=y
CONFIG_ZONE_DMA32=y
CONFIG_PGTABLE_LEVELS=4
CONFIG_DEFCONFIG_LIST="/lib/modules/$UNAME_RELEASE/.config"
CONFIG_IRQ_WORK=y

#
# General setup
#
CONFIG_INIT_ENV_ARG_LIMIT=32
CONFIG_CROSS_COMPILE=""
# CONFIG_COMPILE_TEST is not set
CONFIG_LOCALVERSION=""
# CONFIG_LOCALVERSION_AUTO is not set
CONFIG_DEFAULT_HOSTNAME="(none)"
CONFIG_SWAP=y
CONFIG_SYSVIPC=y
CONFIG_SYSVIPC_SYSCTL=y
CONFIG_POSIX_MQUEUE=y
CONFIG_POSIX_MQUEUE_SYSCTL=y
CONFIG_CROSS_MEMORY_ATTACH=y
CONFIG_FHANDLE=y
CONFIG_USELIB=y
CONFIG_AUDIT=y
CONFIG_HAVE_ARCH_AUDITSYSCALL=y
CONFIG_AUDITSYSCALL=y
CONFIG_AUDIT_WATCH=y
CONFIG_AUDIT_TREE=y

#
# IRQ subsystem
#
CONFIG_GENERIC_IRQ_SHOW=y
CONFIG_GENERIC_IRQ_SHOW_LEVEL=y
CONFIG_IRQ_DOMAIN=y
CONFIG_GENERIC_MSI_IRQ=y
# CONFIG_IRQ_DOMAIN_DEBUG is not set
CONFIG_IRQ_FORCED_THREADING=y
CONFIG_SPARSE_IRQ=y
CONFIG_GENERIC_TIME_VSYSCALL_OLD=y
CONFIG_GENERIC_CLOCKEVENTS=y
CONFIG_ARCH_HAS_TICK_BROADCAST=y
CONFIG_GENERIC_CLOCKEVENTS_BROADCAST=y
CONFIG_GENERIC_CMOS_UPDATE=y

#
# Timers subsystem
#
CONFIG_TICK_ONESHOT=y
CONFIG_NO_HZ_COMMON=y
# CONFIG_HZ_PERIODIC is not set
CONFIG_NO_HZ_IDLE=y
# CONFIG_NO_HZ is not set
CONFIG_HIGH_RES_TIMERS=y

#
# CPU/Task time and stats accounting
#
CONFIG_VIRT_CPU_ACCOUNTING=y
# CONFIG_TICK_CPU_ACCOUNTING is not set
CONFIG_VIRT_CPU_ACCOUNTING_NATIVE=y
CONFIG_BSD_PROCESS_ACCT=y
CONFIG_BSD_PROCESS_ACCT_V3=y
CONFIG_TASKSTATS=y
CONFIG_TASK_DELAY_ACCT=y
CONFIG_TASK_XACCT=y
CONFIG_TASK_IO_ACCOUNTING=y

#
# RCU Subsystem
#
CONFIG_TREE_RCU=y
# CONFIG_RCU_EXPERT is not set
CONFIG_SRCU=y
# CONFIG_TASKS_RCU is not set
CONFIG_RCU_STALL_COMMON=y
# CONFIG_TREE_RCU_TRACE is not set
# CONFIG_RCU_EXPEDITE_BOOT is not set
CONFIG_BUILD_BIN2C=y
CONFIG_IKCONFIG=y
CONFIG_IKCONFIG_PROC=y
CONFIG_LOG_BUF_SHIFT=17
CONFIG_LOG_CPU_MAX_BUF_SHIFT=13
CONFIG_ARCH_SUPPORTS_NUMA_BALANCING=y
CONFIG_CGROUPS=y
# CONFIG_CGROUP_DEBUG is not set
CONFIG_CGROUP_FREEZER=y
# CONFIG_CGROUP_PIDS is not set
CONFIG_CGROUP_DEVICE=y
CONFIG_CPUSETS=y
CONFIG_PROC_PID_CPUSET=y
CONFIG_CGROUP_CPUACCT=y
# CONFIG_MEMCG is not set
# CONFIG_CGROUP_HUGETLB is not set
CONFIG_CGROUP_PERF=y
CONFIG_CGROUP_SCHED=y
CONFIG_FAIR_GROUP_SCHED=y
CONFIG_CFS_BANDWIDTH=y
CONFIG_RT_GROUP_SCHED=y
CONFIG_BLK_CGROUP=y
# CONFIG_DEBUG_BLK_CGROUP is not set
# CONFIG_CHECKPOINT_RESTORE is not set
CONFIG_NAMESPACES=y
CONFIG_UTS_NS=y
CONFIG_IPC_NS=y
CONFIG_USER_NS=y
CONFIG_PID_NS=y
CONFIG_NET_NS=y
CONFIG_SCHED_AUTOGROUP=y
# CONFIG_SYSFS_DEPRECATED is not set
CONFIG_RELAY=y
CONFIG_BLK_DEV_INITRD=y
CONFIG_INITRAMFS_SOURCE=""
CONFIG_RD_GZIP=y
# CONFIG_RD_BZIP2 is not set
# CONFIG_RD_LZMA is not set
# CONFIG_RD_XZ is not set
# CONFIG_RD_LZO is not set
# CONFIG_RD_LZ4 is not set
# CONFIG_CC_OPTIMIZE_FOR_SIZE is not set
CONFIG_SYSCTL=y
CONFIG_ANON_INODES=y
CONFIG_SYSCTL_EXCEPTION_TRACE=y
CONFIG_BPF=y
CONFIG_EXPERT=y
CONFIG_MULTIUSER=y
CONFIG_SGETMASK_SYSCALL=y
CONFIG_SYSFS_SYSCALL=y
# CONFIG_SYSCTL_SYSCALL is not set
CONFIG_KALLSYMS=y
CONFIG_KALLSYMS_ALL=y
CONFIG_PRINTK=y
CONFIG_BUG=y
CONFIG_ELF_CORE=y
CONFIG_BASE_FULL=y
CONFIG_FUTEX=y
CONFIG_EPOLL=y
CONFIG_SIGNALFD=y
CONFIG_TIMERFD=y
CONFIG_EVENTFD=y
CONFIG_BPF_SYSCALL=y
CONFIG_SHMEM=y
CONFIG_AIO=y
CONFIG_ADVISE_SYSCALLS=y
CONFIG_USERFAULTFD=y
CONFIG_PCI_QUIRKS=y
CONFIG_MEMBARRIER=y
# CONFIG_EMBEDDED is not set
CONFIG_HAVE_PERF_EVENTS=y

#
# Kernel Performance Events And Counters
#
CONFIG_PERF_EVENTS=y
CONFIG_VM_EVENT_COUNTERS=y
# CONFIG_SLUB_DEBUG is not set
# CONFIG_COMPAT_BRK is not set
# CONFIG_SLAB is not set
CONFIG_SLUB=y
# CONFIG_SLOB is not set
# CONFIG_SLUB_CPU_PARTIAL is not set
# CONFIG_SYSTEM_DATA_VERIFICATION is not set
CONFIG_PROFILING=y
CONFIG_KEXEC_CORE=y
# CONFIG_OPROFILE is not set
CONFIG_HAVE_OPROFILE=y
# CONFIG_KPROBES is not set
CONFIG_JUMP_LABEL=y
CONFIG_STATIC_KEYS_SELFTEST=y
# CONFIG_UPROBES is not set
# CONFIG_HAVE_64BIT_ALIGNED_ACCESS is not set
CONFIG_HAVE_EFFICIENT_UNALIGNED_ACCESS=y
CONFIG_ARCH_USE_BUILTIN_BSWAP=y
CONFIG_HAVE_IOREMAP_PROT=y
CONFIG_HAVE_KPROBES=y
CONFIG_HAVE_KRETPROBES=y
CONFIG_HAVE_ARCH_TRACEHOOK=y
CONFIG_HAVE_DMA_ATTRS=y
CONFIG_GENERIC_SMP_IDLE_THREAD=y
CONFIG_HAVE_REGS_AND_STACK_ACCESS_API=y
CONFIG_HAVE_DMA_API_DEBUG=y
CONFIG_HAVE_HW_BREAKPOINT=y
CONFIG_HAVE_PERF_EVENTS_NMI=y
CONFIG_HAVE_ARCH_JUMP_LABEL=y
CONFIG_HAVE_RCU_TABLE_FREE=y
CONFIG_ARCH_HAVE_NMI_SAFE_CMPXCHG=y
CONFIG_ARCH_WANT_IPC_PARSE_VERSION=y
CONFIG_ARCH_WANT_COMPAT_IPC_PARSE_VERSION=y
CONFIG_ARCH_WANT_OLD_COMPAT_IPC=y
CONFIG_HAVE_ARCH_SECCOMP_FILTER=y
CONFIG_SECCOMP_FILTER=y
# CONFIG_CC_STACKPROTECTOR is not set
CONFIG_HAVE_VIRT_CPU_ACCOUNTING=y
CONFIG_HAVE_VIRT_CPU_ACCOUNTING_GEN=y
CONFIG_HAVE_MOD_ARCH_SPECIFIC=y
CONFIG_MODULES_USE_ELF_RELA=y
CONFIG_HAVE_IRQ_EXIT_ON_IRQ_STACK=y
CONFIG_ARCH_HAS_ELF_RANDOMIZE=y
CONFIG_CLONE_BACKWARDS=y
CONFIG_OLD_SIGSUSPEND=y
CONFIG_COMPAT_OLD_SIGACTION=y

#
# GCOV-based kernel profiling
#
# CONFIG_GCOV_KERNEL is not set
CONFIG_ARCH_HAS_GCOV_PROFILE_ALL=y
# CONFIG_HAVE_GENERIC_DMA_COHERENT is not set
CONFIG_RT_MUTEXES=y
CONFIG_BASE_SMALL=0
CONFIG_MODULES=y
CONFIG_MODULE_FORCE_LOAD=y
CONFIG_MODULE_UNLOAD=y
CONFIG_MODULE_FORCE_UNLOAD=y
CONFIG_MODVERSIONS=y
# CONFIG_MODULE_SRCVERSION_ALL is not set
# CONFIG_MODULE_SIG is not set
# CONFIG_MODULE_COMPRESS is not set
CONFIG_MODULES_TREE_LOOKUP=y
CONFIG_STOP_MACHINE=y
CONFIG_BLOCK=y
CONFIG_BLK_DEV_BSG=y
CONFIG_BLK_DEV_BSGLIB=y
CONFIG_BLK_DEV_INTEGRITY=y
# CONFIG_BLK_DEV_THROTTLING is not set
# CONFIG_BLK_CMDLINE_PARSER is not set

#
# Partition Types
#
CONFIG_PARTITION_ADVANCED=y
# CONFIG_ACORN_PARTITION is not set
# CONFIG_AIX_PARTITION is not set
# CONFIG_OSF_PARTITION is not set
# CONFIG_AMIGA_PARTITION is not set
# CONFIG_ATARI_PARTITION is not set
CONFIG_MAC_PARTITION=y
CONFIG_MSDOS_PARTITION=y
# CONFIG_BSD_DISKLABEL is not set
# CONFIG_MINIX_SUBPARTITION is not set
# CONFIG_SOLARIS_X86_PARTITION is not set
# CONFIG_UNIXWARE_DISKLABEL is not set
# CONFIG_LDM_PARTITION is not set
# CONFIG_SGI_PARTITION is not set
# CONFIG_ULTRIX_PARTITION is not set
# CONFIG_SUN_PARTITION is not set
# CONFIG_KARMA_PARTITION is not set
CONFIG_EFI_PARTITION=y
# CONFIG_SYSV68_PARTITION is not set
# CONFIG_CMDLINE_PARTITION is not set
CONFIG_BLOCK_COMPAT=y

#
# IO Schedulers
#
CONFIG_IOSCHED_NOOP=y
CONFIG_IOSCHED_DEADLINE=y
CONFIG_IOSCHED_CFQ=y
CONFIG_CFQ_GROUP_IOSCHED=y
# CONFIG_DEFAULT_DEADLINE is not set
CONFIG_DEFAULT_CFQ=y
# CONFIG_DEFAULT_NOOP is not set
CONFIG_DEFAULT_IOSCHED="cfq"
CONFIG_PREEMPT_NOTIFIERS=y
CONFIG_PADATA=y
CONFIG_INLINE_SPIN_UNLOCK_IRQ=y
CONFIG_INLINE_READ_UNLOCK=y
CONFIG_INLINE_READ_UNLOCK_IRQ=y
CONFIG_INLINE_WRITE_UNLOCK=y
CONFIG_INLINE_WRITE_UNLOCK_IRQ=y
CONFIG_ARCH_SUPPORTS_ATOMIC_RMW=y
CONFIG_MUTEX_SPIN_ON_OWNER=y
CONFIG_RWSEM_SPIN_ON_OWNER=y
CONFIG_LOCK_SPIN_ON_OWNER=y
CONFIG_FREEZER=y
CONFIG_PPC_MSI_BITMAP=y
# CONFIG_PPC_XICS is not set
# CONFIG_PPC_ICP_NATIVE is not set
# CONFIG_PPC_ICP_HV is not set
# CONFIG_PPC_ICS_RTAS is not set
# CONFIG_GE_FPGA is not set

#
# Platform support
#
# CONFIG_PPC_POWERNV is not set
# CONFIG_PPC_PSERIES is not set
CONFIG_PPC_PMAC=y
CONFIG_PPC_PMAC64=y
# CONFIG_PPC_MAPLE is not set
# CONFIG_PPC_PASEMI is not set
# CONFIG_PPC_PS3 is not set
# CONFIG_PPC_CELL is not set
# CONFIG_PPC_CELL_NATIVE is not set
# CONFIG_PPC_IBM_CELL_BLADE is not set
# CONFIG_PPC_CELL_QPACE is not set
# CONFIG_PQ2ADS is not set
CONFIG_KVM_GUEST=y
CONFIG_EPAPR_PARAVIRT=y
CONFIG_PPC_NATIVE=y
CONFIG_PPC_OF_BOOT_TRAMPOLINE=y
# CONFIG_IPIC is not set
CONFIG_MPIC=y
# CONFIG_PPC_EPAPR_HV_PIC is not set
# CONFIG_MPIC_WEIRD is not set
CONFIG_MPIC_MSGR=y
# CONFIG_PPC_I8259 is not set
CONFIG_U3_DART=y
# CONFIG_PPC_RTAS is not set
# CONFIG_MMIO_NVRAM is not set
CONFIG_MPIC_U3_HT_IRQS=y
# CONFIG_PPC_MPC106 is not set
CONFIG_PPC_970_NAP=y
# CONFIG_PPC_P7_NAP is not set

#
# CPU Frequency scaling
#
CONFIG_CPU_FREQ=y
CONFIG_CPU_FREQ_GOV_COMMON=y
CONFIG_CPU_FREQ_STAT=m
CONFIG_CPU_FREQ_STAT_DETAILS=y
# CONFIG_CPU_FREQ_DEFAULT_GOV_PERFORMANCE is not set
# CONFIG_CPU_FREQ_DEFAULT_GOV_POWERSAVE is not set
# CONFIG_CPU_FREQ_DEFAULT_GOV_USERSPACE is not set
CONFIG_CPU_FREQ_DEFAULT_GOV_ONDEMAND=y
# CONFIG_CPU_FREQ_DEFAULT_GOV_CONSERVATIVE is not set
CONFIG_CPU_FREQ_GOV_PERFORMANCE=y
CONFIG_CPU_FREQ_GOV_POWERSAVE=m
CONFIG_CPU_FREQ_GOV_USERSPACE=m
CONFIG_CPU_FREQ_GOV_ONDEMAND=y
CONFIG_CPU_FREQ_GOV_CONSERVATIVE=m

#
# CPU frequency scaling drivers
#
CONFIG_CPU_FREQ_PMAC64=y

#
# CPUIdle driver
#

#
# CPU Idle
#
CONFIG_CPU_IDLE=y
CONFIG_CPU_IDLE_GOV_LADDER=y
CONFIG_CPU_IDLE_GOV_MENU=y

#
# POWERPC CPU Idle Drivers
#
# CONFIG_ARCH_NEEDS_CPU_IDLE_COUPLED is not set
# CONFIG_FSL_ULI1575 is not set
CONFIG_SIMPLE_GPIO=y

#
# Kernel options
#
# CONFIG_HZ_100 is not set
# CONFIG_HZ_250 is not set
# CONFIG_HZ_300 is not set
CONFIG_HZ_1000=y
CONFIG_HZ=1000
CONFIG_SCHED_HRTICK=y
# CONFIG_PREEMPT_NONE is not set
CONFIG_PREEMPT_VOLUNTARY=y
# CONFIG_PREEMPT is not set
CONFIG_BINFMT_ELF=y
CONFIG_COMPAT_BINFMT_ELF=y
CONFIG_CORE_DUMP_DEFAULT_ELF_HEADERS=y
CONFIG_BINFMT_SCRIPT=y
# CONFIG_HAVE_AOUT is not set
CONFIG_BINFMT_MISC=m
CONFIG_COREDUMP=y
CONFIG_HUGETLB_PAGE_SIZE_VARIABLE=y
CONFIG_PPC_TRANSACTIONAL_MEM=y
CONFIG_IOMMU_HELPER=y
# CONFIG_SWIOTLB is not set
CONFIG_HOTPLUG_CPU=y
CONFIG_ARCH_CPU_PROBE_RELEASE=y
CONFIG_ARCH_ENABLE_MEMORY_HOTPLUG=y
CONFIG_ARCH_HAS_WALK_MEMORY=y
CONFIG_ARCH_ENABLE_MEMORY_HOTREMOVE=y
CONFIG_PPC64_SUPPORTS_MEMORY_FAILURE=y
CONFIG_KEXEC=y
# CONFIG_CRASH_DUMP is not set
CONFIG_IRQ_ALL_CPUS=y
# CONFIG_NUMA is not set
CONFIG_ARCH_SELECT_MEMORY_MODEL=y
CONFIG_ARCH_FLATMEM_ENABLE=y
CONFIG_ARCH_SPARSEMEM_ENABLE=y
CONFIG_SYS_SUPPORTS_HUGETLBFS=y
CONFIG_SELECT_MEMORY_MODEL=y
CONFIG_FLATMEM_MANUAL=y
# CONFIG_SPARSEMEM_MANUAL is not set
CONFIG_FLATMEM=y
CONFIG_FLAT_NODE_MEM_MAP=y
CONFIG_SPARSEMEM_VMEMMAP_ENABLE=y
CONFIG_HAVE_MEMBLOCK=y
CONFIG_HAVE_MEMBLOCK_NODE_MAP=y
CONFIG_HAVE_GENERIC_RCU_GUP=y
CONFIG_NO_BOOTMEM=y
# CONFIG_HAVE_BOOTMEM_INFO_NODE is not set
CONFIG_SPLIT_PTLOCK_CPUS=4
CONFIG_COMPACTION=y
CONFIG_MIGRATION=y
CONFIG_PHYS_ADDR_T_64BIT=y
CONFIG_ZONE_DMA_FLAG=1
CONFIG_BOUNCE=y
CONFIG_MMU_NOTIFIER=y
CONFIG_KSM=y
CONFIG_DEFAULT_MMAP_MIN_ADDR=65536
CONFIG_ARCH_SUPPORTS_MEMORY_FAILURE=y
# CONFIG_MEMORY_FAILURE is not set
CONFIG_CLEANCACHE=y
CONFIG_FRONTSWAP=y
# CONFIG_CMA is not set
# CONFIG_ZSWAP is not set
# CONFIG_ZPOOL is not set
# CONFIG_ZBUD is not set
# CONFIG_ZSMALLOC is not set
# CONFIG_IDLE_PAGE_TRACKING is not set
CONFIG_PPC_4K_PAGES=y
# CONFIG_PPC_64K_PAGES is not set
CONFIG_FORCE_MAX_ZONEORDER=13
# CONFIG_PPC_COPRO_BASE is not set
# CONFIG_SCHED_SMT is not set
CONFIG_PPC_DENORMALISATION=y
# CONFIG_CMDLINE_BOOL is not set
CONFIG_EXTRA_TARGETS=""
CONFIG_HIBERNATE_CALLBACKS=y
CONFIG_HIBERNATION=y
CONFIG_PM_STD_PARTITION=""
CONFIG_PM_SLEEP=y
CONFIG_PM_SLEEP_SMP=y
CONFIG_PM_AUTOSLEEP=y
CONFIG_PM_WAKELOCKS=y
CONFIG_PM_WAKELOCKS_LIMIT=100
CONFIG_PM_WAKELOCKS_GC=y
CONFIG_PM=y
# CONFIG_PM_DEBUG is not set
# CONFIG_WQ_POWER_EFFICIENT_DEFAULT is not set
CONFIG_SECCOMP=y
CONFIG_ISA_DMA_API=y

#
# Bus options
#
CONFIG_ZONE_DMA=y
CONFIG_NEED_DMA_MAP_STATE=y
CONFIG_NEED_SG_DMA_LENGTH=y
CONFIG_GENERIC_ISA_DMA=y
# CONFIG_PPC_INDIRECT_PCI is not set
CONFIG_PCI=y
CONFIG_PCI_DOMAINS=y
CONFIG_PCI_SYSCALL=y
CONFIG_PCIEPORTBUS=y
CONFIG_PCIEAER=y
# CONFIG_PCIE_ECRC is not set
# CONFIG_PCIEAER_INJECT is not set
# CONFIG_PCIEASPM is not set
CONFIG_PCIE_PME=y
CONFIG_PCI_BUS_ADDR_T_64BIT=y
CONFIG_PCI_MSI=y
# CONFIG_PCI_DEBUG is not set
CONFIG_PCI_REALLOC_ENABLE_AUTO=y
# CONFIG_PCI_STUB is not set
CONFIG_PCI_ATS=y
CONFIG_PCI_IOV=y
CONFIG_PCI_PRI=y
CONFIG_PCI_PASID=y

#
# PCI host controller drivers
#
# CONFIG_PCCARD is not set
# CONFIG_HOTPLUG_PCI is not set
# CONFIG_HAS_RAPIDIO is not set
# CONFIG_RAPIDIO is not set
# CONFIG_NONSTATIC_KERNEL is not set
# CONFIG_RELOCATABLE is not set
CONFIG_PAGE_OFFSET=0xc000000000000000
CONFIG_KERNEL_START=0xc000000000000000
CONFIG_PHYSICAL_START=0x00000000
# CONFIG_ARCH_RANDOM is not set
CONFIG_NET=y
CONFIG_COMPAT_NETLINK_MESSAGES=y
CONFIG_NET_INGRESS=y

#
# Networking options
#
CONFIG_PACKET=y
# CONFIG_PACKET_DIAG is not set
CONFIG_UNIX=y
# CONFIG_UNIX_DIAG is not set
CONFIG_XFRM=y
CONFIG_XFRM_ALGO=m
CONFIG_XFRM_USER=m
CONFIG_XFRM_SUB_POLICY=y
CONFIG_XFRM_MIGRATE=y
# CONFIG_XFRM_STATISTICS is not set
CONFIG_XFRM_IPCOMP=m
CONFIG_NET_KEY=m
CONFIG_NET_KEY_MIGRATE=y
CONFIG_INET=y
CONFIG_IP_MULTICAST=y
CONFIG_IP_ADVANCED_ROUTER=y
CONFIG_IP_FIB_TRIE_STATS=y
CONFIG_IP_MULTIPLE_TABLES=y
CONFIG_IP_ROUTE_MULTIPATH=y
CONFIG_IP_ROUTE_VERBOSE=y
CONFIG_IP_ROUTE_CLASSID=y
# CONFIG_IP_PNP is not set
CONFIG_NET_IPIP=m
CONFIG_NET_IPGRE_DEMUX=m
CONFIG_NET_IP_TUNNEL=m
CONFIG_NET_IPGRE=m
CONFIG_NET_IPGRE_BROADCAST=y
CONFIG_IP_MROUTE=y
CONFIG_IP_MROUTE_MULTIPLE_TABLES=y
CONFIG_IP_PIMSM_V1=y
CONFIG_IP_PIMSM_V2=y
CONFIG_SYN_COOKIES=y
# CONFIG_NET_IPVTI is not set
CONFIG_NET_UDP_TUNNEL=m
# CONFIG_NET_FOU is not set
# CONFIG_NET_FOU_IP_TUNNELS is not set
CONFIG_INET_AH=m
CONFIG_INET_ESP=m
CONFIG_INET_IPCOMP=m
CONFIG_INET_XFRM_TUNNEL=m
CONFIG_INET_TUNNEL=m
CONFIG_INET_XFRM_MODE_TRANSPORT=m
CONFIG_INET_XFRM_MODE_TUNNEL=m
CONFIG_INET_XFRM_MODE_BEET=m
CONFIG_INET_LRO=m
CONFIG_INET_DIAG=m
CONFIG_INET_TCP_DIAG=m
# CONFIG_INET_UDP_DIAG is not set
CONFIG_TCP_CONG_ADVANCED=y
CONFIG_TCP_CONG_BIC=m
CONFIG_TCP_CONG_CUBIC=y
CONFIG_TCP_CONG_WESTWOOD=m
CONFIG_TCP_CONG_HTCP=m
CONFIG_TCP_CONG_HSTCP=m
CONFIG_TCP_CONG_HYBLA=m
CONFIG_TCP_CONG_VEGAS=m
CONFIG_TCP_CONG_SCALABLE=m
CONFIG_TCP_CONG_LP=m
CONFIG_TCP_CONG_VENO=m
CONFIG_TCP_CONG_YEAH=m
CONFIG_TCP_CONG_ILLINOIS=m
# CONFIG_TCP_CONG_DCTCP is not set
# CONFIG_TCP_CONG_CDG is not set
CONFIG_DEFAULT_CUBIC=y
# CONFIG_DEFAULT_RENO is not set
CONFIG_DEFAULT_TCP_CONG="cubic"
CONFIG_TCP_MD5SIG=y
CONFIG_IPV6=y
CONFIG_IPV6_ROUTER_PREF=y
CONFIG_IPV6_ROUTE_INFO=y
CONFIG_IPV6_OPTIMISTIC_DAD=y
CONFIG_INET6_AH=m
CONFIG_INET6_ESP=m
CONFIG_INET6_IPCOMP=m
CONFIG_IPV6_MIP6=y
# CONFIG_IPV6_ILA is not set
CONFIG_INET6_XFRM_TUNNEL=m
CONFIG_INET6_TUNNEL=m
CONFIG_INET6_XFRM_MODE_TRANSPORT=m
CONFIG_INET6_XFRM_MODE_TUNNEL=m
CONFIG_INET6_XFRM_MODE_BEET=m
CONFIG_INET6_XFRM_MODE_ROUTEOPTIMIZATION=m
# CONFIG_IPV6_VTI is not set
CONFIG_IPV6_SIT=m
CONFIG_IPV6_SIT_6RD=y
CONFIG_IPV6_NDISC_NODETYPE=y
CONFIG_IPV6_TUNNEL=m
# CONFIG_IPV6_GRE is not set
CONFIG_IPV6_MULTIPLE_TABLES=y
CONFIG_IPV6_SUBTREES=y
CONFIG_IPV6_MROUTE=y
CONFIG_IPV6_MROUTE_MULTIPLE_TABLES=y
CONFIG_IPV6_PIMSM_V2=y
# CONFIG_NETLABEL is not set
CONFIG_NETWORK_SECMARK=y
CONFIG_NET_PTP_CLASSIFY=y
# CONFIG_NETWORK_PHY_TIMESTAMPING is not set
CONFIG_NETFILTER=y
# CONFIG_NETFILTER_DEBUG is not set
CONFIG_NETFILTER_ADVANCED=y
CONFIG_BRIDGE_NETFILTER=m

#
# Core Netfilter Configuration
#
CONFIG_NETFILTER_INGRESS=y
CONFIG_NETFILTER_NETLINK=m
# CONFIG_NETFILTER_NETLINK_ACCT is not set
CONFIG_NETFILTER_NETLINK_QUEUE=m
CONFIG_NETFILTER_NETLINK_LOG=m
CONFIG_NF_CONNTRACK=m
CONFIG_NF_CONNTRACK_MARK=y
CONFIG_NF_CONNTRACK_SECMARK=y
CONFIG_NF_CONNTRACK_ZONES=y
CONFIG_NF_CONNTRACK_PROCFS=y
CONFIG_NF_CONNTRACK_EVENTS=y
# CONFIG_NF_CONNTRACK_TIMEOUT is not set
CONFIG_NF_CONNTRACK_TIMESTAMP=y
CONFIG_NF_CT_PROTO_DCCP=m
CONFIG_NF_CT_PROTO_GRE=m
CONFIG_NF_CT_PROTO_SCTP=m
CONFIG_NF_CT_PROTO_UDPLITE=m
CONFIG_NF_CONNTRACK_AMANDA=m
CONFIG_NF_CONNTRACK_FTP=m
CONFIG_NF_CONNTRACK_H323=m
CONFIG_NF_CONNTRACK_IRC=m
CONFIG_NF_CONNTRACK_BROADCAST=m
CONFIG_NF_CONNTRACK_NETBIOS_NS=m
CONFIG_NF_CONNTRACK_SNMP=m
CONFIG_NF_CONNTRACK_PPTP=m
CONFIG_NF_CONNTRACK_SANE=m
CONFIG_NF_CONNTRACK_SIP=m
CONFIG_NF_CONNTRACK_TFTP=m
CONFIG_NF_CT_NETLINK=m
# CONFIG_NF_CT_NETLINK_TIMEOUT is not set
# CONFIG_NETFILTER_NETLINK_GLUE_CT is not set
# CONFIG_NF_TABLES is not set
CONFIG_NETFILTER_XTABLES=m

#
# Xtables combined modules
#
CONFIG_NETFILTER_XT_MARK=m
CONFIG_NETFILTER_XT_CONNMARK=m
CONFIG_NETFILTER_XT_SET=m

#
# Xtables targets
#
CONFIG_NETFILTER_XT_TARGET_AUDIT=m
CONFIG_NETFILTER_XT_TARGET_CHECKSUM=m
CONFIG_NETFILTER_XT_TARGET_CLASSIFY=m
CONFIG_NETFILTER_XT_TARGET_CONNMARK=m
CONFIG_NETFILTER_XT_TARGET_CONNSECMARK=m
CONFIG_NETFILTER_XT_TARGET_CT=m
CONFIG_NETFILTER_XT_TARGET_DSCP=m
CONFIG_NETFILTER_XT_TARGET_HL=m
# CONFIG_NETFILTER_XT_TARGET_HMARK is not set
CONFIG_NETFILTER_XT_TARGET_IDLETIMER=m
CONFIG_NETFILTER_XT_TARGET_LED=m
# CONFIG_NETFILTER_XT_TARGET_LOG is not set
CONFIG_NETFILTER_XT_TARGET_MARK=m
CONFIG_NETFILTER_XT_TARGET_NFLOG=m
CONFIG_NETFILTER_XT_TARGET_NFQUEUE=m
CONFIG_NETFILTER_XT_TARGET_NOTRACK=m
CONFIG_NETFILTER_XT_TARGET_RATEEST=m
CONFIG_NETFILTER_XT_TARGET_TEE=m
CONFIG_NETFILTER_XT_TARGET_TPROXY=m
CONFIG_NETFILTER_XT_TARGET_TRACE=m
CONFIG_NETFILTER_XT_TARGET_SECMARK=m
CONFIG_NETFILTER_XT_TARGET_TCPMSS=m
CONFIG_NETFILTER_XT_TARGET_TCPOPTSTRIP=m

#
# Xtables matches
#
CONFIG_NETFILTER_XT_MATCH_ADDRTYPE=m
# CONFIG_NETFILTER_XT_MATCH_BPF is not set
# CONFIG_NETFILTER_XT_MATCH_CGROUP is not set
CONFIG_NETFILTER_XT_MATCH_CLUSTER=m
CONFIG_NETFILTER_XT_MATCH_COMMENT=m
CONFIG_NETFILTER_XT_MATCH_CONNBYTES=m
# CONFIG_NETFILTER_XT_MATCH_CONNLABEL is not set
CONFIG_NETFILTER_XT_MATCH_CONNLIMIT=m
CONFIG_NETFILTER_XT_MATCH_CONNMARK=m
CONFIG_NETFILTER_XT_MATCH_CONNTRACK=m
CONFIG_NETFILTER_XT_MATCH_CPU=m
CONFIG_NETFILTER_XT_MATCH_DCCP=m
CONFIG_NETFILTER_XT_MATCH_DEVGROUP=m
CONFIG_NETFILTER_XT_MATCH_DSCP=m
CONFIG_NETFILTER_XT_MATCH_ECN=m
CONFIG_NETFILTER_XT_MATCH_ESP=m
CONFIG_NETFILTER_XT_MATCH_HASHLIMIT=m
CONFIG_NETFILTER_XT_MATCH_HELPER=m
CONFIG_NETFILTER_XT_MATCH_HL=m
# CONFIG_NETFILTER_XT_MATCH_IPCOMP is not set
CONFIG_NETFILTER_XT_MATCH_IPRANGE=m
CONFIG_NETFILTER_XT_MATCH_IPVS=m
CONFIG_NETFILTER_XT_MATCH_L2TP=m
CONFIG_NETFILTER_XT_MATCH_LENGTH=m
CONFIG_NETFILTER_XT_MATCH_LIMIT=m
CONFIG_NETFILTER_XT_MATCH_MAC=m
CONFIG_NETFILTER_XT_MATCH_MARK=m
CONFIG_NETFILTER_XT_MATCH_MULTIPORT=m
# CONFIG_NETFILTER_XT_MATCH_NFACCT is not set
CONFIG_NETFILTER_XT_MATCH_OSF=m
CONFIG_NETFILTER_XT_MATCH_OWNER=m
CONFIG_NETFILTER_XT_MATCH_POLICY=m
CONFIG_NETFILTER_XT_MATCH_PHYSDEV=m
CONFIG_NETFILTER_XT_MATCH_PKTTYPE=m
CONFIG_NETFILTER_XT_MATCH_QUOTA=m
CONFIG_NETFILTER_XT_MATCH_RATEEST=m
CONFIG_NETFILTER_XT_MATCH_REALM=m
CONFIG_NETFILTER_XT_MATCH_RECENT=m
CONFIG_NETFILTER_XT_MATCH_SCTP=m
CONFIG_NETFILTER_XT_MATCH_SOCKET=m
CONFIG_NETFILTER_XT_MATCH_STATE=m
CONFIG_NETFILTER_XT_MATCH_STATISTIC=m
CONFIG_NETFILTER_XT_MATCH_STRING=m
CONFIG_NETFILTER_XT_MATCH_TCPMSS=m
CONFIG_NETFILTER_XT_MATCH_TIME=m
CONFIG_NETFILTER_XT_MATCH_U32=m
CONFIG_IP_SET=m
CONFIG_IP_SET_MAX=256
CONFIG_IP_SET_BITMAP_IP=m
CONFIG_IP_SET_BITMAP_IPMAC=m
CONFIG_IP_SET_BITMAP_PORT=m
CONFIG_IP_SET_HASH_IP=m
# CONFIG_IP_SET_HASH_IPMARK is not set
CONFIG_IP_SET_HASH_IPPORT=m
CONFIG_IP_SET_HASH_IPPORTIP=m
CONFIG_IP_SET_HASH_IPPORTNET=m
# CONFIG_IP_SET_HASH_MAC is not set
# CONFIG_IP_SET_HASH_NETPORTNET is not set
CONFIG_IP_SET_HASH_NET=m
# CONFIG_IP_SET_HASH_NETNET is not set
CONFIG_IP_SET_HASH_NETPORT=m
CONFIG_IP_SET_HASH_NETIFACE=m
CONFIG_IP_SET_LIST_SET=m
CONFIG_IP_VS=m
CONFIG_IP_VS_IPV6=y
# CONFIG_IP_VS_DEBUG is not set
CONFIG_IP_VS_TAB_BITS=12

#
# IPVS transport protocol load balancing support
#
CONFIG_IP_VS_PROTO_TCP=y
CONFIG_IP_VS_PROTO_UDP=y
CONFIG_IP_VS_PROTO_AH_ESP=y
CONFIG_IP_VS_PROTO_ESP=y
CONFIG_IP_VS_PROTO_AH=y
CONFIG_IP_VS_PROTO_SCTP=y

#
# IPVS scheduler
#
CONFIG_IP_VS_RR=m
CONFIG_IP_VS_WRR=m
CONFIG_IP_VS_LC=m
CONFIG_IP_VS_WLC=m
# CONFIG_IP_VS_FO is not set
# CONFIG_IP_VS_OVF is not set
CONFIG_IP_VS_LBLC=m
CONFIG_IP_VS_LBLCR=m
CONFIG_IP_VS_DH=m
CONFIG_IP_VS_SH=m
CONFIG_IP_VS_SED=m
CONFIG_IP_VS_NQ=m

#
# IPVS SH scheduler
#
CONFIG_IP_VS_SH_TAB_BITS=8

#
# IPVS application helper
#
CONFIG_IP_VS_NFCT=y
CONFIG_IP_VS_PE_SIP=m

#
# IP: Netfilter Configuration
#
CONFIG_NF_DEFRAG_IPV4=m
CONFIG_NF_CONNTRACK_IPV4=m
CONFIG_NF_CONNTRACK_PROC_COMPAT=y
CONFIG_NF_DUP_IPV4=m
# CONFIG_NF_LOG_ARP is not set
# CONFIG_NF_LOG_IPV4 is not set
CONFIG_NF_REJECT_IPV4=m
# CONFIG_NF_NAT_IPV4 is not set
CONFIG_IP_NF_IPTABLES=m
CONFIG_IP_NF_MATCH_AH=m
CONFIG_IP_NF_MATCH_ECN=m
# CONFIG_IP_NF_MATCH_RPFILTER is not set
CONFIG_IP_NF_MATCH_TTL=m
CONFIG_IP_NF_FILTER=m
CONFIG_IP_NF_TARGET_REJECT=m
# CONFIG_IP_NF_TARGET_SYNPROXY is not set
# CONFIG_IP_NF_NAT is not set
CONFIG_IP_NF_MANGLE=m
CONFIG_IP_NF_TARGET_CLUSTERIP=m
CONFIG_IP_NF_TARGET_ECN=m
CONFIG_IP_NF_TARGET_TTL=m
CONFIG_IP_NF_RAW=m
CONFIG_IP_NF_SECURITY=m
CONFIG_IP_NF_ARPTABLES=m
CONFIG_IP_NF_ARPFILTER=m
CONFIG_IP_NF_ARP_MANGLE=m

#
# IPv6: Netfilter Configuration
#
CONFIG_NF_DEFRAG_IPV6=m
CONFIG_NF_CONNTRACK_IPV6=m
CONFIG_NF_DUP_IPV6=m
CONFIG_NF_REJECT_IPV6=m
# CONFIG_NF_LOG_IPV6 is not set
# CONFIG_NF_NAT_IPV6 is not set
CONFIG_IP6_NF_IPTABLES=m
CONFIG_IP6_NF_MATCH_AH=m
CONFIG_IP6_NF_MATCH_EUI64=m
CONFIG_IP6_NF_MATCH_FRAG=m
CONFIG_IP6_NF_MATCH_OPTS=m
CONFIG_IP6_NF_MATCH_HL=m
CONFIG_IP6_NF_MATCH_IPV6HEADER=m
CONFIG_IP6_NF_MATCH_MH=m
# CONFIG_IP6_NF_MATCH_RPFILTER is not set
CONFIG_IP6_NF_MATCH_RT=m
CONFIG_IP6_NF_TARGET_HL=m
CONFIG_IP6_NF_FILTER=m
CONFIG_IP6_NF_TARGET_REJECT=m
# CONFIG_IP6_NF_TARGET_SYNPROXY is not set
CONFIG_IP6_NF_MANGLE=m
CONFIG_IP6_NF_RAW=m
CONFIG_IP6_NF_SECURITY=m
# CONFIG_IP6_NF_NAT is not set

#
# DECnet: Netfilter Configuration
#
CONFIG_DECNET_NF_GRABULATOR=m
CONFIG_BRIDGE_NF_EBTABLES=m
CONFIG_BRIDGE_EBT_BROUTE=m
CONFIG_BRIDGE_EBT_T_FILTER=m
CONFIG_BRIDGE_EBT_T_NAT=m
CONFIG_BRIDGE_EBT_802_3=m
CONFIG_BRIDGE_EBT_AMONG=m
CONFIG_BRIDGE_EBT_ARP=m
CONFIG_BRIDGE_EBT_IP=m
CONFIG_BRIDGE_EBT_IP6=m
CONFIG_BRIDGE_EBT_LIMIT=m
CONFIG_BRIDGE_EBT_MARK=m
CONFIG_BRIDGE_EBT_PKTTYPE=m
CONFIG_BRIDGE_EBT_STP=m
CONFIG_BRIDGE_EBT_VLAN=m
CONFIG_BRIDGE_EBT_ARPREPLY=m
CONFIG_BRIDGE_EBT_DNAT=m
CONFIG_BRIDGE_EBT_MARK_T=m
CONFIG_BRIDGE_EBT_REDIRECT=m
CONFIG_BRIDGE_EBT_SNAT=m
CONFIG_BRIDGE_EBT_LOG=m
CONFIG_BRIDGE_EBT_NFLOG=m
CONFIG_IP_DCCP=m
CONFIG_INET_DCCP_DIAG=m

#
# DCCP CCIDs Configuration
#
# CONFIG_IP_DCCP_CCID2_DEBUG is not set
CONFIG_IP_DCCP_CCID3=y
# CONFIG_IP_DCCP_CCID3_DEBUG is not set
CONFIG_IP_DCCP_TFRC_LIB=y

#
# DCCP Kernel Hacking
#
# CONFIG_IP_DCCP_DEBUG is not set
CONFIG_IP_SCTP=m
# CONFIG_SCTP_DBG_OBJCNT is not set
CONFIG_SCTP_DEFAULT_COOKIE_HMAC_MD5=y
# CONFIG_SCTP_DEFAULT_COOKIE_HMAC_SHA1 is not set
# CONFIG_SCTP_DEFAULT_COOKIE_HMAC_NONE is not set
CONFIG_SCTP_COOKIE_HMAC_MD5=y
# CONFIG_SCTP_COOKIE_HMAC_SHA1 is not set
CONFIG_RDS=m
CONFIG_RDS_TCP=m
# CONFIG_RDS_DEBUG is not set
CONFIG_TIPC=m
CONFIG_TIPC_MEDIA_UDP=y
CONFIG_ATM=m
CONFIG_ATM_CLIP=m
# CONFIG_ATM_CLIP_NO_ICMP is not set
CONFIG_ATM_LANE=m
CONFIG_ATM_MPOA=m
CONFIG_ATM_BR2684=m
# CONFIG_ATM_BR2684_IPFILTER is not set
CONFIG_L2TP=m
# CONFIG_L2TP_DEBUGFS is not set
CONFIG_L2TP_V3=y
CONFIG_L2TP_IP=m
CONFIG_L2TP_ETH=m
CONFIG_STP=m
CONFIG_GARP=m
CONFIG_BRIDGE=m
CONFIG_BRIDGE_IGMP_SNOOPING=y
# CONFIG_BRIDGE_VLAN_FILTERING is not set
CONFIG_HAVE_NET_DSA=y
CONFIG_VLAN_8021Q=m
CONFIG_VLAN_8021Q_GVRP=y
# CONFIG_VLAN_8021Q_MVRP is not set
CONFIG_DECNET=m
CONFIG_DECNET_ROUTER=y
CONFIG_LLC=m
CONFIG_LLC2=m
CONFIG_IPX=m
CONFIG_IPX_INTERN=y
CONFIG_ATALK=m
CONFIG_DEV_APPLETALK=m
CONFIG_IPDDP=m
CONFIG_IPDDP_ENCAP=y
# CONFIG_X25 is not set
CONFIG_LAPB=m
CONFIG_PHONET=m
# CONFIG_6LOWPAN is not set
CONFIG_IEEE802154=m
# CONFIG_IEEE802154_NL802154_EXPERIMENTAL is not set
CONFIG_IEEE802154_SOCKET=m
# CONFIG_MAC802154 is not set
CONFIG_NET_SCHED=y

#
# Queueing/Scheduling
#
CONFIG_NET_SCH_CBQ=m
CONFIG_NET_SCH_HTB=m
CONFIG_NET_SCH_HFSC=m
CONFIG_NET_SCH_ATM=m
CONFIG_NET_SCH_PRIO=m
CONFIG_NET_SCH_MULTIQ=m
CONFIG_NET_SCH_RED=m
CONFIG_NET_SCH_SFB=m
CONFIG_NET_SCH_SFQ=m
CONFIG_NET_SCH_TEQL=m
CONFIG_NET_SCH_TBF=m
CONFIG_NET_SCH_GRED=m
CONFIG_NET_SCH_DSMARK=m
CONFIG_NET_SCH_NETEM=m
CONFIG_NET_SCH_DRR=m
CONFIG_NET_SCH_MQPRIO=m
CONFIG_NET_SCH_CHOKE=m
CONFIG_NET_SCH_QFQ=m
CONFIG_NET_SCH_CODEL=m
CONFIG_NET_SCH_FQ_CODEL=m
# CONFIG_NET_SCH_FQ is not set
# CONFIG_NET_SCH_HHF is not set
# CONFIG_NET_SCH_PIE is not set
CONFIG_NET_SCH_INGRESS=m
# CONFIG_NET_SCH_PLUG is not set

#
# Classification
#
CONFIG_NET_CLS=y
CONFIG_NET_CLS_BASIC=m
CONFIG_NET_CLS_TCINDEX=m
CONFIG_NET_CLS_ROUTE4=m
CONFIG_NET_CLS_FW=m
CONFIG_NET_CLS_U32=m
CONFIG_CLS_U32_PERF=y
CONFIG_CLS_U32_MARK=y
CONFIG_NET_CLS_RSVP=m
CONFIG_NET_CLS_RSVP6=m
CONFIG_NET_CLS_FLOW=m
CONFIG_NET_CLS_CGROUP=y
# CONFIG_NET_CLS_BPF is not set
# CONFIG_NET_CLS_FLOWER is not set
CONFIG_NET_EMATCH=y
CONFIG_NET_EMATCH_STACK=32
CONFIG_NET_EMATCH_CMP=m
CONFIG_NET_EMATCH_NBYTE=m
CONFIG_NET_EMATCH_U32=m
CONFIG_NET_EMATCH_META=m
CONFIG_NET_EMATCH_TEXT=m
# CONFIG_NET_EMATCH_IPSET is not set
CONFIG_NET_CLS_ACT=y
CONFIG_NET_ACT_POLICE=m
CONFIG_NET_ACT_GACT=m
CONFIG_GACT_PROB=y
CONFIG_NET_ACT_MIRRED=m
CONFIG_NET_ACT_IPT=m
CONFIG_NET_ACT_NAT=m
CONFIG_NET_ACT_PEDIT=m
CONFIG_NET_ACT_SIMP=m
CONFIG_NET_ACT_SKBEDIT=m
CONFIG_NET_ACT_CSUM=m
# CONFIG_NET_ACT_VLAN is not set
# CONFIG_NET_ACT_BPF is not set
# CONFIG_NET_ACT_CONNMARK is not set
CONFIG_NET_CLS_IND=y
CONFIG_NET_SCH_FIFO=y
CONFIG_DCB=y
CONFIG_DNS_RESOLVER=y
CONFIG_BATMAN_ADV=m
CONFIG_BATMAN_ADV_BLA=y
# CONFIG_BATMAN_ADV_DAT is not set
# CONFIG_BATMAN_ADV_NC is not set
# CONFIG_BATMAN_ADV_MCAST is not set
# CONFIG_BATMAN_ADV_DEBUG is not set
# CONFIG_OPENVSWITCH is not set
# CONFIG_VSOCKETS is not set
# CONFIG_NETLINK_MMAP is not set
# CONFIG_NETLINK_DIAG is not set
# CONFIG_MPLS is not set
# CONFIG_HSR is not set
# CONFIG_NET_SWITCHDEV is not set
# CONFIG_NET_L3_MASTER_DEV is not set
CONFIG_RPS=y
CONFIG_RFS_ACCEL=y
CONFIG_XPS=y
# CONFIG_CGROUP_NET_PRIO is not set
CONFIG_CGROUP_NET_CLASSID=y
CONFIG_NET_RX_BUSY_POLL=y
CONFIG_BQL=y
CONFIG_BPF_JIT=y
CONFIG_NET_FLOW_LIMIT=y

#
# Network testing
#
CONFIG_NET_PKTGEN=m
# CONFIG_HAMRADIO is not set
# CONFIG_CAN is not set
# CONFIG_IRDA is not set
CONFIG_BT=m
CONFIG_BT_BREDR=y
CONFIG_BT_RFCOMM=m
CONFIG_BT_RFCOMM_TTY=y
CONFIG_BT_BNEP=m
CONFIG_BT_BNEP_MC_FILTER=y
CONFIG_BT_BNEP_PROTO_FILTER=y
CONFIG_BT_HIDP=m
CONFIG_BT_HS=y
CONFIG_BT_LE=y
# CONFIG_BT_SELFTEST is not set
CONFIG_BT_DEBUGFS=y

#
# Bluetooth device drivers
#
CONFIG_BT_INTEL=m
CONFIG_BT_BCM=m
CONFIG_BT_RTL=m
CONFIG_BT_HCIBTUSB=m
CONFIG_BT_HCIBTUSB_BCM=y
CONFIG_BT_HCIBTUSB_RTL=y
CONFIG_BT_HCIUART=m
CONFIG_BT_HCIUART_H4=y
CONFIG_BT_HCIUART_BCSP=y
CONFIG_BT_HCIUART_ATH3K=y
CONFIG_BT_HCIUART_LL=y
# CONFIG_BT_HCIUART_3WIRE is not set
# CONFIG_BT_HCIUART_INTEL is not set
# CONFIG_BT_HCIUART_BCM is not set
# CONFIG_BT_HCIUART_QCA is not set
CONFIG_BT_HCIBCM203X=m
CONFIG_BT_HCIBPA10X=m
CONFIG_BT_HCIBFUSB=m
CONFIG_BT_HCIVHCI=m
CONFIG_BT_MRVL=m
CONFIG_BT_ATH3K=m
CONFIG_AF_RXRPC=m
# CONFIG_AF_RXRPC_DEBUG is not set
CONFIG_RXKAD=m
CONFIG_FIB_RULES=y
CONFIG_WIRELESS=y
CONFIG_WEXT_CORE=y
CONFIG_WEXT_PROC=y
CONFIG_CFG80211=m
# CONFIG_NL80211_TESTMODE is not set
# CONFIG_CFG80211_DEVELOPER_WARNINGS is not set
# CONFIG_CFG80211_REG_DEBUG is not set
# CONFIG_CFG80211_CERTIFICATION_ONUS is not set
# CONFIG_CFG80211_DEFAULT_PS is not set
# CONFIG_CFG80211_DEBUGFS is not set
# CONFIG_CFG80211_INTERNAL_REGDB is not set
CONFIG_CFG80211_CRDA_SUPPORT=y
CONFIG_CFG80211_WEXT=y
# CONFIG_LIB80211 is not set
CONFIG_MAC80211=m
CONFIG_MAC80211_HAS_RC=y
CONFIG_MAC80211_RC_MINSTREL=y
CONFIG_MAC80211_RC_MINSTREL_HT=y
CONFIG_MAC80211_RC_MINSTREL_VHT=y
CONFIG_MAC80211_RC_DEFAULT_MINSTREL=y
CONFIG_MAC80211_RC_DEFAULT="minstrel_ht"
CONFIG_MAC80211_MESH=y
CONFIG_MAC80211_LEDS=y
# CONFIG_MAC80211_DEBUGFS is not set
# CONFIG_MAC80211_MESSAGE_TRACING is not set
# CONFIG_MAC80211_DEBUG_MENU is not set
CONFIG_MAC80211_STA_HASH_MAX_SIZE=0
# CONFIG_WIMAX is not set
CONFIG_RFKILL=m
CONFIG_RFKILL_LEDS=y
# CONFIG_RFKILL_INPUT is not set
# CONFIG_RFKILL_REGULATOR is not set
# CONFIG_RFKILL_GPIO is not set
# CONFIG_NET_9P is not set
# CONFIG_CAIF is not set
CONFIG_CEPH_LIB=m
# CONFIG_CEPH_LIB_PRETTYDEBUG is not set
# CONFIG_CEPH_LIB_USE_DNS_RESOLVER is not set
# CONFIG_NFC is not set
# CONFIG_LWTUNNEL is not set
CONFIG_HAVE_BPF_JIT=y

#
# Device Drivers
#

#
# Generic Driver Options
#
CONFIG_UEVENT_HELPER=y
CONFIG_UEVENT_HELPER_PATH=""
CONFIG_DEVTMPFS=y
CONFIG_DEVTMPFS_MOUNT=y
CONFIG_STANDALONE=y
# CONFIG_PREVENT_FIRMWARE_BUILD is not set
CONFIG_FW_LOADER=y
# CONFIG_FIRMWARE_IN_KERNEL is not set
CONFIG_EXTRA_FIRMWARE=""
# CONFIG_FW_LOADER_USER_HELPER_FALLBACK is not set
CONFIG_ALLOW_DEV_COREDUMP=y
# CONFIG_DEBUG_DRIVER is not set
# CONFIG_DEBUG_DEVRES is not set
# CONFIG_SYS_HYPERVISOR is not set
# CONFIG_GENERIC_CPU_DEVICES is not set
CONFIG_REGMAP=y
CONFIG_REGMAP_I2C=m
CONFIG_DMA_SHARED_BUFFER=y
# CONFIG_FENCE_TRACE is not set

#
# Bus devices
#
CONFIG_CONNECTOR=y
CONFIG_PROC_EVENTS=y
CONFIG_MTD=m
# CONFIG_MTD_TESTS is not set
# CONFIG_MTD_REDBOOT_PARTS is not set
# CONFIG_MTD_CMDLINE_PARTS is not set
CONFIG_MTD_OF_PARTS=m
# CONFIG_MTD_AR7_PARTS is not set

#
# User Modules And Translation Layers
#
# CONFIG_MTD_BLOCK is not set
# CONFIG_MTD_BLOCK_RO is not set
# CONFIG_FTL is not set
# CONFIG_NFTL is not set
# CONFIG_INFTL is not set
# CONFIG_RFD_FTL is not set
# CONFIG_SSFDC is not set
# CONFIG_SM_FTL is not set
# CONFIG_MTD_OOPS is not set
# CONFIG_MTD_SWAP is not set
# CONFIG_MTD_PARTITIONED_MASTER is not set

#
# RAM/ROM/Flash chip drivers
#
CONFIG_MTD_CFI=m
CONFIG_MTD_JEDECPROBE=m
CONFIG_MTD_GEN_PROBE=m
CONFIG_MTD_CFI_ADV_OPTIONS=y
CONFIG_MTD_CFI_NOSWAP=y
# CONFIG_MTD_CFI_BE_BYTE_SWAP is not set
# CONFIG_MTD_CFI_LE_BYTE_SWAP is not set
# CONFIG_MTD_CFI_GEOMETRY is not set
CONFIG_MTD_MAP_BANK_WIDTH_1=y
CONFIG_MTD_MAP_BANK_WIDTH_2=y
CONFIG_MTD_MAP_BANK_WIDTH_4=y
# CONFIG_MTD_MAP_BANK_WIDTH_8 is not set
# CONFIG_MTD_MAP_BANK_WIDTH_16 is not set
# CONFIG_MTD_MAP_BANK_WIDTH_32 is not set
CONFIG_MTD_CFI_I1=y
CONFIG_MTD_CFI_I2=y
# CONFIG_MTD_CFI_I4 is not set
# CONFIG_MTD_CFI_I8 is not set
# CONFIG_MTD_OTP is not set
CONFIG_MTD_CFI_INTELEXT=m
CONFIG_MTD_CFI_AMDSTD=m
CONFIG_MTD_CFI_STAA=m
CONFIG_MTD_CFI_UTIL=m
CONFIG_MTD_RAM=m
CONFIG_MTD_ROM=m
CONFIG_MTD_ABSENT=m

#
# Mapping drivers for chip access
#
# CONFIG_MTD_COMPLEX_MAPPINGS is not set
# CONFIG_MTD_PHYSMAP is not set
CONFIG_MTD_PHYSMAP_OF=m
# CONFIG_MTD_INTEL_VR_NOR is not set
# CONFIG_MTD_PLATRAM is not set

#
# Self-contained MTD device drivers
#
# CONFIG_MTD_PMC551 is not set
# CONFIG_MTD_SLRAM is not set
# CONFIG_MTD_PHRAM is not set
# CONFIG_MTD_MTDRAM is not set
# CONFIG_MTD_BLOCK2MTD is not set

#
# Disk-On-Chip Device Drivers
#
# CONFIG_MTD_DOCG3 is not set
# CONFIG_MTD_NAND is not set
# CONFIG_MTD_ONENAND is not set

#
# LPDDR & LPDDR2 PCM memory drivers
#
# CONFIG_MTD_LPDDR is not set
# CONFIG_MTD_SPI_NOR is not set
# CONFIG_MTD_UBI is not set
CONFIG_DTC=y
CONFIG_OF=y
# CONFIG_OF_UNITTEST is not set
CONFIG_OF_FLATTREE=y
CONFIG_OF_EARLY_FLATTREE=y
CONFIG_OF_ADDRESS=y
CONFIG_OF_ADDRESS_PCI=y
CONFIG_OF_IRQ=y
CONFIG_OF_NET=y
CONFIG_OF_MDIO=m
CONFIG_OF_PCI=y
CONFIG_OF_PCI_IRQ=y
CONFIG_OF_MTD=y
CONFIG_OF_RESERVED_MEM=y
# CONFIG_OF_OVERLAY is not set
CONFIG_ARCH_MIGHT_HAVE_PC_PARPORT=y
# CONFIG_PARPORT is not set
CONFIG_BLK_DEV=y
# CONFIG_BLK_DEV_NULL_BLK is not set
# CONFIG_BLK_DEV_FD is not set
# CONFIG_BLK_DEV_PCIESSD_MTIP32XX is not set
# CONFIG_BLK_CPQ_CISS_DA is not set
# CONFIG_BLK_DEV_DAC960 is not set
# CONFIG_BLK_DEV_UMEM is not set
# CONFIG_BLK_DEV_COW_COMMON is not set
CONFIG_BLK_DEV_LOOP=m
CONFIG_BLK_DEV_LOOP_MIN_COUNT=8
# CONFIG_BLK_DEV_CRYPTOLOOP is not set
CONFIG_BLK_DEV_DRBD=m
# CONFIG_DRBD_FAULT_INJECTION is not set
CONFIG_BLK_DEV_NBD=m
# CONFIG_BLK_DEV_SKD is not set
CONFIG_BLK_DEV_OSD=m
# CONFIG_BLK_DEV_SX8 is not set
CONFIG_BLK_DEV_RAM=m
CONFIG_BLK_DEV_RAM_COUNT=16
CONFIG_BLK_DEV_RAM_SIZE=8192
CONFIG_CDROM_PKTCDVD=m
CONFIG_CDROM_PKTCDVD_BUFFERS=8
CONFIG_CDROM_PKTCDVD_WCACHE=y
# CONFIG_ATA_OVER_ETH is not set
# CONFIG_BLK_DEV_HD is not set
# CONFIG_BLK_DEV_RBD is not set
# CONFIG_BLK_DEV_RSXX is not set
# CONFIG_BLK_DEV_NVME is not set

#
# Misc devices
#
# CONFIG_SENSORS_LIS3LV02D is not set
# CONFIG_AD525X_DPOT is not set
CONFIG_DUMMY_IRQ=m
# CONFIG_PHANTOM is not set
# CONFIG_SGI_IOC4 is not set
# CONFIG_TIFM_CORE is not set
# CONFIG_ICS932S401 is not set
# CONFIG_ENCLOSURE_SERVICES is not set
# CONFIG_HP_ILO is not set
# CONFIG_APDS9802ALS is not set
# CONFIG_ISL29003 is not set
# CONFIG_ISL29020 is not set
# CONFIG_SENSORS_TSL2550 is not set
# CONFIG_SENSORS_BH1780 is not set
# CONFIG_SENSORS_BH1770 is not set
# CONFIG_SENSORS_APDS990X is not set
# CONFIG_HMC6352 is not set
# CONFIG_DS1682 is not set
# CONFIG_BMP085_I2C is not set
# CONFIG_USB_SWITCH_FSA9480 is not set
# CONFIG_SRAM is not set
# CONFIG_C2PORT is not set

#
# EEPROM support
#
# CONFIG_EEPROM_AT24 is not set
# CONFIG_EEPROM_LEGACY is not set
# CONFIG_EEPROM_MAX6875 is not set
# CONFIG_EEPROM_93CX6 is not set
# CONFIG_CB710_CORE is not set

#
# Texas Instruments shared transport line discipline
#
# CONFIG_TI_ST is not set
# CONFIG_SENSORS_LIS3_I2C is not set

#
# Altera FPGA firmware download module
#
# CONFIG_ALTERA_STAPL is not set

#
# Intel MIC Bus Driver
#

#
# SCIF Bus Driver
#

#
# Intel MIC Host Driver
#

#
# Intel MIC Card Driver
#

#
# SCIF Driver
#

#
# Intel MIC Coprocessor State Management (COSM) Drivers
#
# CONFIG_GENWQE is not set
# CONFIG_ECHO is not set
# CONFIG_CXL_BASE is not set
# CONFIG_CXL_KERNEL_API is not set
# CONFIG_CXL_EEH is not set
CONFIG_HAVE_IDE=y
# CONFIG_IDE is not set

#
# SCSI device support
#
CONFIG_SCSI_MOD=y
CONFIG_RAID_ATTRS=m
CONFIG_SCSI=y
CONFIG_SCSI_DMA=y
CONFIG_SCSI_NETLINK=y
# CONFIG_SCSI_MQ_DEFAULT is not set
# CONFIG_SCSI_PROC_FS is not set

#
# SCSI support type (disk, tape, CD-ROM)
#
CONFIG_BLK_DEV_SD=m
CONFIG_CHR_DEV_ST=m
CONFIG_CHR_DEV_OSST=m
CONFIG_BLK_DEV_SR=m
CONFIG_BLK_DEV_SR_VENDOR=y
CONFIG_CHR_DEV_SG=m
CONFIG_CHR_DEV_SCH=m
CONFIG_SCSI_CONSTANTS=y
CONFIG_SCSI_LOGGING=y
CONFIG_SCSI_SCAN_ASYNC=y

#
# SCSI Transports
#
CONFIG_SCSI_SPI_ATTRS=m
CONFIG_SCSI_FC_ATTRS=m
CONFIG_SCSI_ISCSI_ATTRS=m
CONFIG_SCSI_SAS_ATTRS=m
CONFIG_SCSI_SAS_LIBSAS=m
CONFIG_SCSI_SAS_ATA=y
CONFIG_SCSI_SAS_HOST_SMP=y
CONFIG_SCSI_SRP_ATTRS=m
CONFIG_SCSI_LOWLEVEL=y
# CONFIG_ISCSI_TCP is not set
# CONFIG_ISCSI_BOOT_SYSFS is not set
# CONFIG_SCSI_CXGB3_ISCSI is not set
# CONFIG_SCSI_CXGB4_ISCSI is not set
# CONFIG_SCSI_BNX2_ISCSI is not set
# CONFIG_BE2ISCSI is not set
# CONFIG_BLK_DEV_3W_XXXX_RAID is not set
# CONFIG_SCSI_HPSA is not set
# CONFIG_SCSI_3W_9XXX is not set
# CONFIG_SCSI_3W_SAS is not set
# CONFIG_SCSI_ACARD is not set
# CONFIG_SCSI_AACRAID is not set
# CONFIG_SCSI_AIC7XXX is not set
# CONFIG_SCSI_AIC79XX is not set
# CONFIG_SCSI_AIC94XX is not set
# CONFIG_SCSI_MVSAS is not set
# CONFIG_SCSI_MVUMI is not set
# CONFIG_SCSI_ADVANSYS is not set
# CONFIG_SCSI_ARCMSR is not set
# CONFIG_SCSI_ESAS2R is not set
# CONFIG_MEGARAID_NEWGEN is not set
# CONFIG_MEGARAID_LEGACY is not set
# CONFIG_MEGARAID_SAS is not set
# CONFIG_SCSI_MPT3SAS is not set
# CONFIG_SCSI_UFSHCD is not set
# CONFIG_SCSI_HPTIOP is not set
# CONFIG_LIBFC is not set
# CONFIG_SCSI_SNIC is not set
# CONFIG_SCSI_DMX3191D is not set
# CONFIG_SCSI_EATA is not set
# CONFIG_SCSI_FUTURE_DOMAIN is not set
# CONFIG_SCSI_GDTH is not set
# CONFIG_SCSI_IPS is not set
# CONFIG_SCSI_INITIO is not set
# CONFIG_SCSI_INIA100 is not set
# CONFIG_SCSI_STEX is not set
# CONFIG_SCSI_SYM53C8XX_2 is not set
# CONFIG_SCSI_IPR is not set
# CONFIG_SCSI_QLOGIC_1280 is not set
# CONFIG_SCSI_QLA_FC is not set
# CONFIG_SCSI_QLA_ISCSI is not set
# CONFIG_SCSI_LPFC is not set
# CONFIG_SCSI_DC395x is not set
# CONFIG_SCSI_AM53C974 is not set
# CONFIG_SCSI_WD719X is not set
# CONFIG_SCSI_DEBUG is not set
# CONFIG_SCSI_PMCRAID is not set
# CONFIG_SCSI_PM8001 is not set
# CONFIG_SCSI_BFA_FC is not set
# CONFIG_SCSI_CHELSIO_FCOE is not set
# CONFIG_SCSI_DH is not set
CONFIG_SCSI_OSD_INITIATOR=m
CONFIG_SCSI_OSD_ULD=m
CONFIG_SCSI_OSD_DPRINT_SENSE=1
# CONFIG_SCSI_OSD_DEBUG is not set
CONFIG_ATA=m
# CONFIG_ATA_NONSTANDARD is not set
CONFIG_ATA_VERBOSE_ERROR=y
CONFIG_SATA_PMP=y

#
# Controllers with non-SFF native interface
#
# CONFIG_SATA_AHCI is not set
# CONFIG_SATA_AHCI_PLATFORM is not set
# CONFIG_AHCI_CEVA is not set
# CONFIG_AHCI_QORIQ is not set
# CONFIG_SATA_INIC162X is not set
# CONFIG_SATA_ACARD_AHCI is not set
# CONFIG_SATA_SIL24 is not set
CONFIG_ATA_SFF=y

#
# SFF controllers with custom DMA interface
#
# CONFIG_PDC_ADMA is not set
# CONFIG_SATA_QSTOR is not set
# CONFIG_SATA_SX4 is not set
CONFIG_ATA_BMDMA=y

#
# SATA SFF controllers with BMDMA
#
# CONFIG_ATA_PIIX is not set
# CONFIG_SATA_MV is not set
# CONFIG_SATA_NV is not set
# CONFIG_SATA_PROMISE is not set
# CONFIG_SATA_SIL is not set
# CONFIG_SATA_SIS is not set
CONFIG_SATA_SVW=m
# CONFIG_SATA_ULI is not set
# CONFIG_SATA_VIA is not set
# CONFIG_SATA_VITESSE is not set

#
# PATA SFF controllers with BMDMA
#
# CONFIG_PATA_ALI is not set
# CONFIG_PATA_AMD is not set
# CONFIG_PATA_ARTOP is not set
# CONFIG_PATA_ATIIXP is not set
# CONFIG_PATA_ATP867X is not set
# CONFIG_PATA_CMD64X is not set
# CONFIG_PATA_CYPRESS is not set
# CONFIG_PATA_EFAR is not set
# CONFIG_PATA_HPT366 is not set
# CONFIG_PATA_HPT37X is not set
# CONFIG_PATA_HPT3X2N is not set
# CONFIG_PATA_HPT3X3 is not set
# CONFIG_PATA_IT8213 is not set
# CONFIG_PATA_IT821X is not set
# CONFIG_PATA_JMICRON is not set
CONFIG_PATA_MACIO=m
# CONFIG_PATA_MARVELL is not set
# CONFIG_PATA_NETCELL is not set
# CONFIG_PATA_NINJA32 is not set
# CONFIG_PATA_NS87415 is not set
# CONFIG_PATA_OLDPIIX is not set
# CONFIG_PATA_OPTIDMA is not set
# CONFIG_PATA_PDC2027X is not set
# CONFIG_PATA_PDC_OLD is not set
# CONFIG_PATA_RADISYS is not set
# CONFIG_PATA_RDC is not set
# CONFIG_PATA_SCH is not set
CONFIG_PATA_SERVERWORKS=m
# CONFIG_PATA_SIL680 is not set
# CONFIG_PATA_SIS is not set
# CONFIG_PATA_TOSHIBA is not set
# CONFIG_PATA_TRIFLEX is not set
# CONFIG_PATA_VIA is not set
# CONFIG_PATA_WINBOND is not set

#
# PIO-only SFF controllers
#
# CONFIG_PATA_CMD640_PCI is not set
# CONFIG_PATA_MPIIX is not set
# CONFIG_PATA_NS87410 is not set
# CONFIG_PATA_OPTI is not set
# CONFIG_PATA_PLATFORM is not set
# CONFIG_PATA_RZ1000 is not set

#
# Generic fallback / legacy drivers
#
# CONFIG_ATA_GENERIC is not set
# CONFIG_PATA_LEGACY is not set
# CONFIG_MD is not set
# CONFIG_TARGET_CORE is not set
# CONFIG_FUSION is not set

#
# IEEE 1394 (FireWire) support
#
CONFIG_FIREWIRE=m
CONFIG_FIREWIRE_OHCI=m
CONFIG_FIREWIRE_SBP2=m
CONFIG_FIREWIRE_NET=m
# CONFIG_FIREWIRE_NOSY is not set
CONFIG_MACINTOSH_DRIVERS=y
# CONFIG_ADB_PMU is not set
CONFIG_PMAC_SMU=y
CONFIG_MAC_EMUMOUSEBTN=m
CONFIG_WINDFARM=m
CONFIG_WINDFARM_PM81=m
CONFIG_WINDFARM_PM91=m
CONFIG_WINDFARM_PM112=m
CONFIG_WINDFARM_PM121=m
# CONFIG_PMAC_RACKMETER is not set
CONFIG_NETDEVICES=y
CONFIG_MII=m
CONFIG_NET_CORE=y
CONFIG_BONDING=m
CONFIG_DUMMY=m
CONFIG_EQUALIZER=m
# CONFIG_NET_FC is not set
CONFIG_IFB=m
CONFIG_NET_TEAM=m
# CONFIG_NET_TEAM_MODE_BROADCAST is not set
# CONFIG_NET_TEAM_MODE_ROUNDROBIN is not set
# CONFIG_NET_TEAM_MODE_RANDOM is not set
# CONFIG_NET_TEAM_MODE_ACTIVEBACKUP is not set
# CONFIG_NET_TEAM_MODE_LOADBALANCE is not set
CONFIG_MACVLAN=m
CONFIG_MACVTAP=m
# CONFIG_IPVLAN is not set
CONFIG_VXLAN=m
# CONFIG_GENEVE is not set
CONFIG_NETCONSOLE=m
CONFIG_NETCONSOLE_DYNAMIC=y
CONFIG_NETPOLL=y
CONFIG_NET_POLL_CONTROLLER=y
CONFIG_TUN=m
# CONFIG_TUN_VNET_CROSS_LE is not set
CONFIG_VETH=m
# CONFIG_NLMON is not set
CONFIG_SUNGEM_PHY=m
# CONFIG_ARCNET is not set
# CONFIG_ATM_DRIVERS is not set

#
# CAIF transport drivers
#
CONFIG_VHOST_NET=m
CONFIG_VHOST_RING=m
CONFIG_VHOST=m
# CONFIG_VHOST_CROSS_ENDIAN_LEGACY is not set

#
# Distributed Switch Architecture drivers
#
# CONFIG_NET_DSA_MV88E6XXX is not set
# CONFIG_NET_DSA_MV88E6XXX_NEED_PPU is not set
CONFIG_ETHERNET=y
CONFIG_MDIO=m
# CONFIG_NET_VENDOR_3COM is not set
# CONFIG_NET_VENDOR_ADAPTEC is not set
# CONFIG_NET_VENDOR_AGERE is not set
# CONFIG_NET_VENDOR_ALTEON is not set
# CONFIG_ALTERA_TSE is not set
# CONFIG_NET_VENDOR_AMD is not set
# CONFIG_NET_VENDOR_ARC is not set
# CONFIG_NET_VENDOR_ATHEROS is not set
CONFIG_NET_CADENCE=y
# CONFIG_MACB is not set
CONFIG_NET_VENDOR_BROADCOM=y
# CONFIG_B44 is not set
# CONFIG_BCMGENET is not set
CONFIG_BNX2=m
CONFIG_CNIC=m
CONFIG_TIGON3=m
CONFIG_BNX2X=m
CONFIG_BNX2X_SRIOV=y
# CONFIG_BNX2X_VXLAN is not set
# CONFIG_SYSTEMPORT is not set
# CONFIG_BNXT is not set
# CONFIG_NET_VENDOR_BROCADE is not set
CONFIG_NET_VENDOR_CAVIUM=y
# CONFIG_THUNDER_NIC_PF is not set
# CONFIG_THUNDER_NIC_VF is not set
# CONFIG_THUNDER_NIC_BGX is not set
# CONFIG_LIQUIDIO is not set
# CONFIG_NET_VENDOR_CHELSIO is not set
# CONFIG_NET_VENDOR_CISCO is not set
# CONFIG_DNET is not set
# CONFIG_NET_VENDOR_DEC is not set
# CONFIG_NET_VENDOR_DLINK is not set
# CONFIG_NET_VENDOR_EMULEX is not set
CONFIG_NET_VENDOR_EZCHIP=y
# CONFIG_EZCHIP_NPS_MANAGEMENT_ENET is not set
# CONFIG_NET_VENDOR_EXAR is not set
# CONFIG_NET_VENDOR_HP is not set
# CONFIG_NET_VENDOR_INTEL is not set
# CONFIG_JME is not set
# CONFIG_NET_VENDOR_MARVELL is not set
# CONFIG_NET_VENDOR_MELLANOX is not set
# CONFIG_NET_VENDOR_MICREL is not set
# CONFIG_NET_VENDOR_MYRI is not set
# CONFIG_FEALNX is not set
# CONFIG_NET_VENDOR_NATSEMI is not set
# CONFIG_NET_VENDOR_NVIDIA is not set
# CONFIG_NET_VENDOR_OKI is not set
# CONFIG_ETHOC is not set
# CONFIG_NET_PACKET_ENGINE is not set
# CONFIG_NET_VENDOR_QLOGIC is not set
# CONFIG_NET_VENDOR_QUALCOMM is not set
# CONFIG_NET_VENDOR_REALTEK is not set
CONFIG_NET_VENDOR_RENESAS=y
# CONFIG_NET_VENDOR_RDC is not set
CONFIG_NET_VENDOR_ROCKER=y
# CONFIG_NET_VENDOR_SAMSUNG is not set
# CONFIG_NET_VENDOR_SEEQ is not set
# CONFIG_NET_VENDOR_SILAN is not set
# CONFIG_NET_VENDOR_SIS is not set
# CONFIG_SFC is not set
# CONFIG_NET_VENDOR_SMSC is not set
# CONFIG_NET_VENDOR_STMICRO is not set
CONFIG_NET_VENDOR_SUN=y
# CONFIG_HAPPYMEAL is not set
CONFIG_SUNGEM=m
# CONFIG_CASSINI is not set
# CONFIG_NIU is not set
CONFIG_NET_VENDOR_SYNOPSYS=y
# CONFIG_SYNOPSYS_DWC_ETH_QOS is not set
# CONFIG_NET_VENDOR_TEHUTI is not set
# CONFIG_NET_VENDOR_TI is not set
# CONFIG_NET_VENDOR_VIA is not set
# CONFIG_NET_VENDOR_WIZNET is not set
# CONFIG_NET_VENDOR_XILINX is not set
# CONFIG_FDDI is not set
# CONFIG_HIPPI is not set
CONFIG_PHYLIB=m

#
# MII PHY device drivers
#
# CONFIG_AQUANTIA_PHY is not set
# CONFIG_AT803X_PHY is not set
# CONFIG_AMD_PHY is not set
CONFIG_MARVELL_PHY=m
CONFIG_DAVICOM_PHY=m
CONFIG_QSEMI_PHY=m
CONFIG_LXT_PHY=m
CONFIG_CICADA_PHY=m
CONFIG_VITESSE_PHY=m
# CONFIG_TERANETICS_PHY is not set
CONFIG_SMSC_PHY=m
CONFIG_BCM_NET_PHYLIB=m
CONFIG_BROADCOM_PHY=m
CONFIG_BCM7XXX_PHY=m
CONFIG_BCM87XX_PHY=m
CONFIG_ICPLUS_PHY=m
CONFIG_REALTEK_PHY=m
CONFIG_NATIONAL_PHY=m
CONFIG_STE10XP=m
CONFIG_LSI_ET1011C_PHY=m
CONFIG_MICREL_PHY=m
# CONFIG_DP83848_PHY is not set
# CONFIG_DP83867_PHY is not set
# CONFIG_MICROCHIP_PHY is not set
# CONFIG_FIXED_PHY is not set
CONFIG_MDIO_BITBANG=m
CONFIG_MDIO_GPIO=m
# CONFIG_MDIO_OCTEON is not set
CONFIG_MDIO_BUS_MUX=m
CONFIG_MDIO_BUS_MUX_GPIO=m
CONFIG_MDIO_BUS_MUX_MMIOREG=m
CONFIG_MDIO_BCM_UNIMAC=m
# CONFIG_PPP is not set
# CONFIG_SLIP is not set

#
# Host-side USB support is needed for USB Network Adapter support
#
CONFIG_USB_NET_DRIVERS=m
# CONFIG_USB_CATC is not set
# CONFIG_USB_KAWETH is not set
# CONFIG_USB_PEGASUS is not set
# CONFIG_USB_RTL8150 is not set
# CONFIG_USB_RTL8152 is not set
# CONFIG_USB_LAN78XX is not set
CONFIG_USB_USBNET=m
# CONFIG_USB_NET_AX8817X is not set
# CONFIG_USB_NET_AX88179_178A is not set
CONFIG_USB_NET_CDCETHER=m
# CONFIG_USB_NET_CDC_EEM is not set
# CONFIG_USB_NET_CDC_NCM is not set
# CONFIG_USB_NET_HUAWEI_CDC_NCM is not set
# CONFIG_USB_NET_CDC_MBIM is not set
# CONFIG_USB_NET_DM9601 is not set
# CONFIG_USB_NET_SR9700 is not set
# CONFIG_USB_NET_SR9800 is not set
# CONFIG_USB_NET_SMSC75XX is not set
# CONFIG_USB_NET_SMSC95XX is not set
# CONFIG_USB_NET_GL620A is not set
# CONFIG_USB_NET_NET1080 is not set
# CONFIG_USB_NET_PLUSB is not set
# CONFIG_USB_NET_MCS7830 is not set
CONFIG_USB_NET_RNDIS_HOST=m
# CONFIG_USB_NET_CDC_SUBSET is not set
# CONFIG_USB_NET_ZAURUS is not set
# CONFIG_USB_NET_CX82310_ETH is not set
# CONFIG_USB_NET_KALMIA is not set
# CONFIG_USB_NET_QMI_WWAN is not set
# CONFIG_USB_HSO is not set
# CONFIG_USB_NET_INT51X1 is not set
# CONFIG_USB_CDC_PHONET is not set
# CONFIG_USB_IPHETH is not set
# CONFIG_USB_SIERRA_NET is not set
# CONFIG_USB_VL600 is not set
# CONFIG_USB_NET_CH9200 is not set
CONFIG_WLAN=y
# CONFIG_LIBERTAS_THINFIRM is not set
# CONFIG_AIRO is not set
# CONFIG_ATMEL is not set
# CONFIG_AT76C50X_USB is not set
# CONFIG_PRISM54 is not set
# CONFIG_USB_ZD1201 is not set
# CONFIG_USB_NET_RNDIS_WLAN is not set
# CONFIG_ADM8211 is not set
# CONFIG_RTL8180 is not set
# CONFIG_RTL8187 is not set
# CONFIG_MAC80211_HWSIM is not set
# CONFIG_MWL8K is not set
# CONFIG_ATH_CARDS is not set
CONFIG_B43=m
CONFIG_B43_BCMA=y
CONFIG_B43_SSB=y
CONFIG_B43_BUSES_BCMA_AND_SSB=y
# CONFIG_B43_BUSES_BCMA is not set
# CONFIG_B43_BUSES_SSB is not set
CONFIG_B43_PCI_AUTOSELECT=y
CONFIG_B43_PCICORE_AUTOSELECT=y
CONFIG_B43_BCMA_PIO=y
CONFIG_B43_PIO=y
CONFIG_B43_PHY_G=y
CONFIG_B43_PHY_N=y
CONFIG_B43_PHY_LP=y
CONFIG_B43_PHY_HT=y
CONFIG_B43_LEDS=y
CONFIG_B43_HWRNG=y
# CONFIG_B43_DEBUG is not set
CONFIG_B43LEGACY=m
CONFIG_B43LEGACY_PCI_AUTOSELECT=y
CONFIG_B43LEGACY_PCICORE_AUTOSELECT=y
CONFIG_B43LEGACY_LEDS=y
CONFIG_B43LEGACY_HWRNG=y
CONFIG_B43LEGACY_DEBUG=y
CONFIG_B43LEGACY_DMA=y
CONFIG_B43LEGACY_PIO=y
CONFIG_B43LEGACY_DMA_AND_PIO_MODE=y
# CONFIG_B43LEGACY_DMA_MODE is not set
# CONFIG_B43LEGACY_PIO_MODE is not set
CONFIG_BRCMUTIL=m
CONFIG_BRCMSMAC=m
CONFIG_BRCMFMAC=m
# CONFIG_BRCMFMAC_USB is not set
# CONFIG_BRCMFMAC_PCIE is not set
# CONFIG_BRCM_TRACING is not set
# CONFIG_BRCMDBG is not set
# CONFIG_HOSTAP is not set
# CONFIG_IPW2100 is not set
# CONFIG_IPW2200 is not set
# CONFIG_IWLWIFI is not set
# CONFIG_IWL4965 is not set
# CONFIG_IWL3945 is not set
# CONFIG_LIBERTAS is not set
# CONFIG_HERMES is not set
# CONFIG_P54_COMMON is not set
# CONFIG_RT2X00 is not set
# CONFIG_WL_MEDIATEK is not set
# CONFIG_RTL_CARDS is not set
# CONFIG_RTL8XXXU is not set
# CONFIG_WL_TI is not set
# CONFIG_ZD1211RW is not set
# CONFIG_MWIFIEX is not set
# CONFIG_CW1200 is not set
# CONFIG_RSI_91X is not set

#
# Enable WiMAX (Networking options) to see the WiMAX drivers
#
# CONFIG_WAN is not set
# CONFIG_IEEE802154_DRIVERS is not set
# CONFIG_VMXNET3 is not set
# CONFIG_ISDN is not set
# CONFIG_NVM is not set

#
# Input device support
#
CONFIG_INPUT=y
CONFIG_INPUT_LEDS=y
CONFIG_INPUT_FF_MEMLESS=m
CONFIG_INPUT_POLLDEV=m
CONFIG_INPUT_SPARSEKMAP=m
# CONFIG_INPUT_MATRIXKMAP is not set

#
# Userland interfaces
#
CONFIG_INPUT_MOUSEDEV=y
# CONFIG_INPUT_MOUSEDEV_PSAUX is not set
CONFIG_INPUT_MOUSEDEV_SCREEN_X=1024
CONFIG_INPUT_MOUSEDEV_SCREEN_Y=768
# CONFIG_INPUT_JOYDEV is not set
CONFIG_INPUT_EVDEV=m
# CONFIG_INPUT_EVBUG is not set

#
# Input Device Drivers
#
# CONFIG_INPUT_KEYBOARD is not set
# CONFIG_INPUT_MOUSE is not set
# CONFIG_INPUT_JOYSTICK is not set
# CONFIG_INPUT_TABLET is not set
# CONFIG_INPUT_TOUCHSCREEN is not set
CONFIG_INPUT_MISC=y
# CONFIG_INPUT_AD714X is not set
# CONFIG_INPUT_BMA150 is not set
# CONFIG_INPUT_E3X0_BUTTON is not set
# CONFIG_INPUT_MMA8450 is not set
# CONFIG_INPUT_MPU3050 is not set
# CONFIG_INPUT_GP2A is not set
# CONFIG_INPUT_GPIO_BEEPER is not set
# CONFIG_INPUT_GPIO_TILT_POLLED is not set
# CONFIG_INPUT_ATI_REMOTE2 is not set
# CONFIG_INPUT_KEYSPAN_REMOTE is not set
# CONFIG_INPUT_KXTJ9 is not set
# CONFIG_INPUT_POWERMATE is not set
# CONFIG_INPUT_YEALINK is not set
# CONFIG_INPUT_CM109 is not set
# CONFIG_INPUT_REGULATOR_HAPTIC is not set
# CONFIG_INPUT_UINPUT is not set
# CONFIG_INPUT_PCF8574 is not set
# CONFIG_INPUT_GPIO_ROTARY_ENCODER is not set
# CONFIG_INPUT_ADXL34X is not set
# CONFIG_INPUT_IMS_PCU is not set
# CONFIG_INPUT_CMA3000 is not set
# CONFIG_INPUT_DRV260X_HAPTICS is not set
# CONFIG_INPUT_DRV2665_HAPTICS is not set
# CONFIG_INPUT_DRV2667_HAPTICS is not set

#
# Hardware I/O ports
#
# CONFIG_SERIO is not set
CONFIG_ARCH_MIGHT_HAVE_PC_SERIO=y
# CONFIG_GAMEPORT is not set

#
# Character devices
#
CONFIG_TTY=y
CONFIG_VT=y
CONFIG_CONSOLE_TRANSLATIONS=y
CONFIG_VT_CONSOLE=y
CONFIG_VT_CONSOLE_SLEEP=y
CONFIG_HW_CONSOLE=y
CONFIG_VT_HW_CONSOLE_BINDING=y
CONFIG_UNIX98_PTYS=y
CONFIG_DEVPTS_MULTIPLE_INSTANCES=y
# CONFIG_LEGACY_PTYS is not set
# CONFIG_SERIAL_NONSTANDARD is not set
# CONFIG_NOZOMI is not set
# CONFIG_N_GSM is not set
# CONFIG_TRACE_SINK is not set
# CONFIG_PPC_EPAPR_HV_BYTECHAN is not set
CONFIG_DEVMEM=y
# CONFIG_DEVKMEM is not set

#
# Serial drivers
#
CONFIG_SERIAL_8250=m
CONFIG_SERIAL_8250_DEPRECATED_OPTIONS=y
CONFIG_SERIAL_8250_DMA=y
CONFIG_SERIAL_8250_PCI=m
CONFIG_SERIAL_8250_NR_UARTS=4
CONFIG_SERIAL_8250_RUNTIME_UARTS=4
# CONFIG_SERIAL_8250_EXTENDED is not set
# CONFIG_SERIAL_8250_DW is not set
# CONFIG_SERIAL_8250_RT288X is not set
# CONFIG_SERIAL_8250_MID is not set

#
# Non-8250 serial port support
#
# CONFIG_SERIAL_UARTLITE is not set
CONFIG_SERIAL_CORE=m
CONFIG_SERIAL_PMACZILOG=m
# CONFIG_SERIAL_PMACZILOG_TTYS is not set
# CONFIG_SERIAL_JSM is not set
CONFIG_SERIAL_OF_PLATFORM=m
# CONFIG_SERIAL_SCCNXP is not set
# CONFIG_SERIAL_SC16IS7XX is not set
# CONFIG_SERIAL_ALTERA_JTAGUART is not set
# CONFIG_SERIAL_ALTERA_UART is not set
# CONFIG_SERIAL_XILINX_PS_UART is not set
# CONFIG_SERIAL_ARC is not set
# CONFIG_SERIAL_RP2 is not set
# CONFIG_SERIAL_FSL_LPUART is not set
# CONFIG_SERIAL_CONEXANT_DIGICOLOR is not set
# CONFIG_TTY_PRINTK is not set
# CONFIG_HVC_UDBG is not set
CONFIG_IPMI_HANDLER=m
# CONFIG_IPMI_PANIC_EVENT is not set
CONFIG_IPMI_DEVICE_INTERFACE=m
CONFIG_IPMI_SI=m
# CONFIG_IPMI_SI_PROBE_DEFAULTS is not set
# CONFIG_IPMI_SSIF is not set
CONFIG_IPMI_WATCHDOG=m
CONFIG_IPMI_POWEROFF=m
CONFIG_HW_RANDOM=m
CONFIG_HW_RANDOM_TIMERIOMEM=m
# CONFIG_R3964 is not set
# CONFIG_APPLICOM is not set
# CONFIG_RAW_DRIVER is not set
CONFIG_HANGCHECK_TIMER=m
# CONFIG_TCG_TPM is not set
CONFIG_DEVPORT=y
# CONFIG_XILLYBUS is not set

#
# I2C support
#
CONFIG_I2C=y
CONFIG_I2C_BOARDINFO=y
CONFIG_I2C_COMPAT=y
CONFIG_I2C_CHARDEV=m
CONFIG_I2C_MUX=m

#
# Multiplexer I2C Chip support
#
CONFIG_I2C_ARB_GPIO_CHALLENGE=m
CONFIG_I2C_MUX_GPIO=m
CONFIG_I2C_MUX_PCA9541=m
CONFIG_I2C_MUX_PCA954x=m
CONFIG_I2C_MUX_REG=m
CONFIG_I2C_HELPER_AUTO=y
CONFIG_I2C_ALGOBIT=m

#
# I2C Hardware Bus support
#

#
# PC SMBus host controller drivers
#
# CONFIG_I2C_ALI1535 is not set
# CONFIG_I2C_ALI1563 is not set
# CONFIG_I2C_ALI15X3 is not set
# CONFIG_I2C_AMD756 is not set
# CONFIG_I2C_AMD8111 is not set
# CONFIG_I2C_I801 is not set
# CONFIG_I2C_ISCH is not set
# CONFIG_I2C_PIIX4 is not set
# CONFIG_I2C_NFORCE2 is not set
# CONFIG_I2C_SIS5595 is not set
# CONFIG_I2C_SIS630 is not set
# CONFIG_I2C_SIS96X is not set
# CONFIG_I2C_VIA is not set
# CONFIG_I2C_VIAPRO is not set

#
# Mac SMBus host controller drivers
#
CONFIG_I2C_POWERMAC=y

#
# I2C system bus drivers (mostly embedded / system-on-chip)
#
# CONFIG_I2C_CBUS_GPIO is not set
# CONFIG_I2C_DESIGNWARE_PLATFORM is not set
# CONFIG_I2C_DESIGNWARE_PCI is not set
CONFIG_I2C_GPIO=m
# CONFIG_I2C_MPC is not set
# CONFIG_I2C_OCORES is not set
# CONFIG_I2C_PCA_PLATFORM is not set
# CONFIG_I2C_PXA_PCI is not set
# CONFIG_I2C_SIMTEC is not set
# CONFIG_I2C_XILINX is not set

#
# External I2C/SMBus adapter drivers
#
# CONFIG_I2C_DIOLAN_U2C is not set
# CONFIG_I2C_PARPORT_LIGHT is not set
# CONFIG_I2C_ROBOTFUZZ_OSIF is not set
# CONFIG_I2C_TAOS_EVM is not set
# CONFIG_I2C_TINY_USB is not set

#
# Other I2C/SMBus bus drivers
#
# CONFIG_I2C_STUB is not set
CONFIG_I2C_SLAVE=y
CONFIG_I2C_SLAVE_EEPROM=m
# CONFIG_I2C_DEBUG_CORE is not set
# CONFIG_I2C_DEBUG_ALGO is not set
CONFIG_I2C_DEBUG_BUS=y
# CONFIG_SPI is not set
# CONFIG_SPMI is not set
# CONFIG_HSI is not set

#
# PPS support
#
CONFIG_PPS=y
# CONFIG_PPS_DEBUG is not set
# CONFIG_NTP_PPS is not set

#
# PPS clients support
#
# CONFIG_PPS_CLIENT_KTIMER is not set
# CONFIG_PPS_CLIENT_LDISC is not set
# CONFIG_PPS_CLIENT_GPIO is not set

#
# PPS generators support
#

#
# PTP clock support
#
CONFIG_PTP_1588_CLOCK=m

#
# Enable PHYLIB and NETWORK_PHY_TIMESTAMPING to see the additional clocks.
#
CONFIG_ARCH_WANT_OPTIONAL_GPIOLIB=y
CONFIG_ARCH_REQUIRE_GPIOLIB=y
CONFIG_GPIOLIB=y
CONFIG_GPIO_DEVRES=y
CONFIG_OF_GPIO=y
# CONFIG_DEBUG_GPIO is not set
CONFIG_GPIO_SYSFS=y

#
# Memory mapped GPIO drivers
#
# CONFIG_GPIO_74XX_MMIO is not set
# CONFIG_GPIO_ALTERA is not set
# CONFIG_GPIO_DWAPB is not set
# CONFIG_GPIO_GENERIC_PLATFORM is not set
# CONFIG_GPIO_GRGPIO is not set
# CONFIG_GPIO_VX855 is not set
# CONFIG_GPIO_XILINX is not set
# CONFIG_GPIO_ZX is not set

#
# I2C GPIO expanders
#
# CONFIG_GPIO_ADP5588 is not set
# CONFIG_GPIO_ADNP is not set
# CONFIG_GPIO_MAX7300 is not set
# CONFIG_GPIO_MAX732X is not set
# CONFIG_GPIO_PCA953X is not set
# CONFIG_GPIO_PCF857X is not set
# CONFIG_GPIO_SX150X is not set

#
# MFD GPIO expanders
#

#
# PCI GPIO expanders
#
# CONFIG_GPIO_AMD8111 is not set
# CONFIG_GPIO_BT8XX is not set
# CONFIG_GPIO_ML_IOH is not set
# CONFIG_GPIO_RDC321X is not set

#
# SPI or I2C GPIO expanders
#
# CONFIG_GPIO_MCP23S08 is not set

#
# USB GPIO expanders
#
# CONFIG_W1 is not set
CONFIG_POWER_SUPPLY=y
# CONFIG_POWER_SUPPLY_DEBUG is not set
# CONFIG_PDA_POWER is not set
# CONFIG_TEST_POWER is not set
# CONFIG_BATTERY_DS2780 is not set
# CONFIG_BATTERY_DS2781 is not set
CONFIG_BATTERY_DS2782=m
# CONFIG_BATTERY_SBS is not set
# CONFIG_BATTERY_BQ27XXX is not set
# CONFIG_BATTERY_MAX17040 is not set
# CONFIG_BATTERY_MAX17042 is not set
# CONFIG_CHARGER_ISP1704 is not set
# CONFIG_CHARGER_MAX8903 is not set
# CONFIG_CHARGER_LP8727 is not set
# CONFIG_CHARGER_GPIO is not set
# CONFIG_CHARGER_MANAGER is not set
# CONFIG_CHARGER_BQ2415X is not set
# CONFIG_CHARGER_BQ24190 is not set
# CONFIG_CHARGER_BQ24257 is not set
# CONFIG_CHARGER_BQ24735 is not set
# CONFIG_CHARGER_BQ25890 is not set
# CONFIG_CHARGER_SMB347 is not set
# CONFIG_BATTERY_GAUGE_LTC2941 is not set
# CONFIG_CHARGER_RT9455 is not set
CONFIG_POWER_RESET=y
CONFIG_POWER_RESET_GPIO=y
# CONFIG_POWER_RESET_GPIO_RESTART is not set
# CONFIG_POWER_RESET_LTC2952 is not set
# CONFIG_POWER_RESET_RESTART is not set
# CONFIG_POWER_RESET_SYSCON is not set
# CONFIG_POWER_RESET_SYSCON_POWEROFF is not set
CONFIG_POWER_AVS=y
CONFIG_HWMON=m
# CONFIG_HWMON_VID is not set
# CONFIG_HWMON_DEBUG_CHIP is not set

#
# Native drivers
#
# CONFIG_SENSORS_AD7414 is not set
# CONFIG_SENSORS_AD7418 is not set
# CONFIG_SENSORS_ADM1021 is not set
# CONFIG_SENSORS_ADM1025 is not set
# CONFIG_SENSORS_ADM1026 is not set
# CONFIG_SENSORS_ADM1029 is not set
# CONFIG_SENSORS_ADM1031 is not set
# CONFIG_SENSORS_ADM9240 is not set
# CONFIG_SENSORS_ADT7410 is not set
# CONFIG_SENSORS_ADT7411 is not set
# CONFIG_SENSORS_ADT7462 is not set
# CONFIG_SENSORS_ADT7470 is not set
# CONFIG_SENSORS_ADT7475 is not set
# CONFIG_SENSORS_ASC7621 is not set
# CONFIG_SENSORS_ATXP1 is not set
# CONFIG_SENSORS_DS620 is not set
# CONFIG_SENSORS_DS1621 is not set
# CONFIG_SENSORS_I5K_AMB is not set
# CONFIG_SENSORS_F75375S is not set
# CONFIG_SENSORS_GL518SM is not set
# CONFIG_SENSORS_GL520SM is not set
# CONFIG_SENSORS_G760A is not set
# CONFIG_SENSORS_G762 is not set
# CONFIG_SENSORS_GPIO_FAN is not set
# CONFIG_SENSORS_HIH6130 is not set
# CONFIG_SENSORS_IBMAEM is not set
# CONFIG_SENSORS_IBMPEX is not set
# CONFIG_SENSORS_JC42 is not set
# CONFIG_SENSORS_POWR1220 is not set
# CONFIG_SENSORS_LINEAGE is not set
# CONFIG_SENSORS_LTC2945 is not set
# CONFIG_SENSORS_LTC4151 is not set
# CONFIG_SENSORS_LTC4215 is not set
# CONFIG_SENSORS_LTC4222 is not set
# CONFIG_SENSORS_LTC4245 is not set
# CONFIG_SENSORS_LTC4260 is not set
# CONFIG_SENSORS_LTC4261 is not set
# CONFIG_SENSORS_MAX16065 is not set
# CONFIG_SENSORS_MAX1619 is not set
# CONFIG_SENSORS_MAX1668 is not set
# CONFIG_SENSORS_MAX197 is not set
# CONFIG_SENSORS_MAX6639 is not set
# CONFIG_SENSORS_MAX6642 is not set
# CONFIG_SENSORS_MAX6650 is not set
# CONFIG_SENSORS_MAX6697 is not set
# CONFIG_SENSORS_MAX31790 is not set
# CONFIG_SENSORS_HTU21 is not set
# CONFIG_SENSORS_MCP3021 is not set
# CONFIG_SENSORS_LM63 is not set
# CONFIG_SENSORS_LM73 is not set
# CONFIG_SENSORS_LM75 is not set
# CONFIG_SENSORS_LM77 is not set
# CONFIG_SENSORS_LM78 is not set
# CONFIG_SENSORS_LM80 is not set
# CONFIG_SENSORS_LM83 is not set
# CONFIG_SENSORS_LM85 is not set
# CONFIG_SENSORS_LM87 is not set
# CONFIG_SENSORS_LM90 is not set
# CONFIG_SENSORS_LM92 is not set
# CONFIG_SENSORS_LM93 is not set
# CONFIG_SENSORS_LM95234 is not set
# CONFIG_SENSORS_LM95241 is not set
# CONFIG_SENSORS_LM95245 is not set
# CONFIG_SENSORS_NTC_THERMISTOR is not set
# CONFIG_SENSORS_NCT7802 is not set
# CONFIG_SENSORS_NCT7904 is not set
# CONFIG_SENSORS_PCF8591 is not set
# CONFIG_PMBUS is not set
# CONFIG_SENSORS_SHT15 is not set
# CONFIG_SENSORS_SHT21 is not set
# CONFIG_SENSORS_SHTC1 is not set
# CONFIG_SENSORS_SIS5595 is not set
# CONFIG_SENSORS_EMC1403 is not set
# CONFIG_SENSORS_EMC2103 is not set
# CONFIG_SENSORS_EMC6W201 is not set
# CONFIG_SENSORS_SMSC47M192 is not set
# CONFIG_SENSORS_SCH56XX_COMMON is not set
# CONFIG_SENSORS_SMM665 is not set
# CONFIG_SENSORS_ADC128D818 is not set
# CONFIG_SENSORS_ADS1015 is not set
# CONFIG_SENSORS_ADS7828 is not set
# CONFIG_SENSORS_AMC6821 is not set
# CONFIG_SENSORS_INA209 is not set
# CONFIG_SENSORS_INA2XX is not set
# CONFIG_SENSORS_TC74 is not set
# CONFIG_SENSORS_THMC50 is not set
# CONFIG_SENSORS_TMP102 is not set
# CONFIG_SENSORS_TMP103 is not set
# CONFIG_SENSORS_TMP401 is not set
# CONFIG_SENSORS_TMP421 is not set
# CONFIG_SENSORS_VIA686A is not set
# CONFIG_SENSORS_VT8231 is not set
# CONFIG_SENSORS_W83781D is not set
# CONFIG_SENSORS_W83791D is not set
# CONFIG_SENSORS_W83792D is not set
# CONFIG_SENSORS_W83793 is not set
# CONFIG_SENSORS_W83795 is not set
# CONFIG_SENSORS_W83L785TS is not set
# CONFIG_SENSORS_W83L786NG is not set
CONFIG_THERMAL=m
CONFIG_THERMAL_HWMON=y
CONFIG_THERMAL_OF=y
# CONFIG_THERMAL_WRITABLE_TRIPS is not set
CONFIG_THERMAL_DEFAULT_GOV_STEP_WISE=y
# CONFIG_THERMAL_DEFAULT_GOV_FAIR_SHARE is not set
# CONFIG_THERMAL_DEFAULT_GOV_USER_SPACE is not set
# CONFIG_THERMAL_DEFAULT_GOV_POWER_ALLOCATOR is not set
CONFIG_THERMAL_GOV_FAIR_SHARE=y
CONFIG_THERMAL_GOV_STEP_WISE=y
CONFIG_THERMAL_GOV_BANG_BANG=y
CONFIG_THERMAL_GOV_USER_SPACE=y
# CONFIG_THERMAL_GOV_POWER_ALLOCATOR is not set
CONFIG_CPU_THERMAL=y
CONFIG_THERMAL_EMULATION=y
CONFIG_WATCHDOG=y
CONFIG_WATCHDOG_CORE=y
# CONFIG_WATCHDOG_NOWAYOUT is not set

#
# Watchdog Device Drivers
#
# CONFIG_SOFT_WATCHDOG is not set
CONFIG_GPIO_WATCHDOG=m
# CONFIG_XILINX_WATCHDOG is not set
# CONFIG_CADENCE_WATCHDOG is not set
# CONFIG_DW_WATCHDOG is not set
# CONFIG_MAX63XX_WATCHDOG is not set
# CONFIG_ALIM7101_WDT is not set
# CONFIG_I6300ESB_WDT is not set
# CONFIG_BCM7038_WDT is not set
# CONFIG_MEN_A21_WDT is not set

#
# PCI-based Watchdog Cards
#
# CONFIG_PCIPCWATCHDOG is not set
# CONFIG_WDTPCI is not set

#
# USB-based Watchdog Cards
#
# CONFIG_USBPCWATCHDOG is not set
CONFIG_SSB_POSSIBLE=y

#
# Sonics Silicon Backplane
#
CONFIG_SSB=y
CONFIG_SSB_SPROM=y
CONFIG_SSB_BLOCKIO=y
CONFIG_SSB_PCIHOST_POSSIBLE=y
CONFIG_SSB_PCIHOST=y
CONFIG_SSB_B43_PCI_BRIDGE=y
# CONFIG_SSB_HOST_SOC is not set
# CONFIG_SSB_SILENT is not set
# CONFIG_SSB_DEBUG is not set
CONFIG_SSB_DRIVER_PCICORE_POSSIBLE=y
CONFIG_SSB_DRIVER_PCICORE=y
CONFIG_SSB_DRIVER_GPIO=y
CONFIG_BCMA_POSSIBLE=y

#
# Broadcom specific AMBA
#
CONFIG_BCMA=y
CONFIG_BCMA_BLOCKIO=y
CONFIG_BCMA_HOST_PCI_POSSIBLE=y
# CONFIG_BCMA_HOST_PCI is not set
# CONFIG_BCMA_HOST_SOC is not set
# CONFIG_BCMA_DRIVER_PCI is not set
# CONFIG_BCMA_DRIVER_GMAC_CMN is not set
# CONFIG_BCMA_DRIVER_GPIO is not set
# CONFIG_BCMA_DEBUG is not set

#
# Multifunction device drivers
#
# CONFIG_MFD_CORE is not set
# CONFIG_MFD_AS3711 is not set
# CONFIG_MFD_AS3722 is not set
# CONFIG_PMIC_ADP5520 is not set
# CONFIG_MFD_AAT2870_CORE is not set
# CONFIG_MFD_ATMEL_FLEXCOM is not set
# CONFIG_MFD_ATMEL_HLCDC is not set
# CONFIG_MFD_BCM590XX is not set
# CONFIG_MFD_AXP20X is not set
# CONFIG_PMIC_DA903X is not set
# CONFIG_MFD_DA9052_I2C is not set
# CONFIG_MFD_DA9055 is not set
# CONFIG_MFD_DA9062 is not set
# CONFIG_MFD_DA9063 is not set
# CONFIG_MFD_DA9150 is not set
# CONFIG_MFD_DLN2 is not set
# CONFIG_MFD_MC13XXX_I2C is not set
# CONFIG_MFD_HI6421_PMIC is not set
# CONFIG_HTC_PASIC3 is not set
# CONFIG_HTC_I2CPLD is not set
# CONFIG_LPC_ICH is not set
# CONFIG_LPC_SCH is not set
# CONFIG_INTEL_SOC_PMIC is not set
# CONFIG_MFD_JANZ_CMODIO is not set
# CONFIG_MFD_KEMPLD is not set
# CONFIG_MFD_88PM800 is not set
# CONFIG_MFD_88PM805 is not set
# CONFIG_MFD_88PM860X is not set
# CONFIG_MFD_MAX14577 is not set
# CONFIG_MFD_MAX77686 is not set
# CONFIG_MFD_MAX77693 is not set
# CONFIG_MFD_MAX77843 is not set
# CONFIG_MFD_MAX8907 is not set
# CONFIG_MFD_MAX8925 is not set
# CONFIG_MFD_MAX8997 is not set
# CONFIG_MFD_MAX8998 is not set
# CONFIG_MFD_MT6397 is not set
# CONFIG_MFD_MENF21BMC is not set
# CONFIG_MFD_VIPERBOARD is not set
# CONFIG_MFD_RETU is not set
# CONFIG_MFD_PCF50633 is not set
# CONFIG_MFD_RDC321X is not set
# CONFIG_MFD_RTSX_PCI is not set
# CONFIG_MFD_RT5033 is not set
# CONFIG_MFD_RTSX_USB is not set
# CONFIG_MFD_RC5T583 is not set
# CONFIG_MFD_RK808 is not set
# CONFIG_MFD_RN5T618 is not set
# CONFIG_MFD_SEC_CORE is not set
# CONFIG_MFD_SI476X_CORE is not set
# CONFIG_MFD_SM501 is not set
# CONFIG_MFD_SKY81452 is not set
# CONFIG_MFD_SMSC is not set
# CONFIG_ABX500_CORE is not set
# CONFIG_MFD_STMPE is not set
# CONFIG_MFD_SYSCON is not set
# CONFIG_MFD_TI_AM335X_TSCADC is not set
# CONFIG_MFD_LP3943 is not set
# CONFIG_MFD_LP8788 is not set
# CONFIG_MFD_PALMAS is not set
# CONFIG_TPS6105X is not set
# CONFIG_TPS65010 is not set
# CONFIG_TPS6507X is not set
# CONFIG_MFD_TPS65090 is not set
# CONFIG_MFD_TPS65217 is not set
# CONFIG_MFD_TPS65218 is not set
# CONFIG_MFD_TPS6586X is not set
# CONFIG_MFD_TPS65910 is not set
# CONFIG_MFD_TPS65912 is not set
# CONFIG_MFD_TPS65912_I2C is not set
# CONFIG_MFD_TPS80031 is not set
# CONFIG_TWL4030_CORE is not set
# CONFIG_TWL6040_CORE is not set
# CONFIG_MFD_WL1273_CORE is not set
# CONFIG_MFD_LM3533 is not set
# CONFIG_MFD_TC3589X is not set
# CONFIG_MFD_TMIO is not set
# CONFIG_MFD_VX855 is not set
# CONFIG_MFD_ARIZONA_I2C is not set
# CONFIG_MFD_WM8400 is not set
# CONFIG_MFD_WM831X_I2C is not set
# CONFIG_MFD_WM8350_I2C is not set
# CONFIG_MFD_WM8994 is not set
CONFIG_REGULATOR=y
# CONFIG_REGULATOR_DEBUG is not set
CONFIG_REGULATOR_FIXED_VOLTAGE=m
# CONFIG_REGULATOR_VIRTUAL_CONSUMER is not set
CONFIG_REGULATOR_USERSPACE_CONSUMER=m
# CONFIG_REGULATOR_ACT8865 is not set
# CONFIG_REGULATOR_AD5398 is not set
# CONFIG_REGULATOR_DA9210 is not set
# CONFIG_REGULATOR_DA9211 is not set
# CONFIG_REGULATOR_FAN53555 is not set
# CONFIG_REGULATOR_GPIO is not set
# CONFIG_REGULATOR_ISL9305 is not set
# CONFIG_REGULATOR_ISL6271A is not set
CONFIG_REGULATOR_LP3971=m
# CONFIG_REGULATOR_LP3972 is not set
# CONFIG_REGULATOR_LP872X is not set
# CONFIG_REGULATOR_LP8755 is not set
# CONFIG_REGULATOR_LTC3589 is not set
CONFIG_REGULATOR_MAX1586=m
CONFIG_REGULATOR_MAX8649=m
CONFIG_REGULATOR_MAX8660=m
# CONFIG_REGULATOR_MAX8952 is not set
# CONFIG_REGULATOR_MAX8973 is not set
# CONFIG_REGULATOR_MT6311 is not set
# CONFIG_REGULATOR_PFUZE100 is not set
# CONFIG_REGULATOR_TPS51632 is not set
# CONFIG_REGULATOR_TPS62360 is not set
CONFIG_REGULATOR_TPS65023=m
CONFIG_REGULATOR_TPS6507X=m
# CONFIG_MEDIA_SUPPORT is not set

#
# Graphics support
#
CONFIG_AGP=m
CONFIG_AGP_UNINORTH=m
CONFIG_VGA_ARB=y
CONFIG_VGA_ARB_MAX_GPUS=16
CONFIG_DRM=m
CONFIG_DRM_KMS_HELPER=m
CONFIG_DRM_KMS_FB_HELPER=y
CONFIG_DRM_FBDEV_EMULATION=y
# CONFIG_DRM_LOAD_EDID_FIRMWARE is not set
CONFIG_DRM_TTM=m

#
# I2C encoder or helper chips
#
# CONFIG_DRM_I2C_ADV7511 is not set
CONFIG_DRM_I2C_CH7006=m
CONFIG_DRM_I2C_SIL164=m
CONFIG_DRM_I2C_NXP_TDA998X=m
# CONFIG_DRM_TDFX is not set
# CONFIG_DRM_R128 is not set
CONFIG_DRM_RADEON=m
# CONFIG_DRM_RADEON_USERPTR is not set
# CONFIG_DRM_RADEON_UMS is not set
CONFIG_DRM_AMDGPU=m
# CONFIG_DRM_AMDGPU_CIK is not set
# CONFIG_DRM_AMDGPU_USERPTR is not set
CONFIG_DRM_NOUVEAU=m
CONFIG_NOUVEAU_DEBUG=5
CONFIG_NOUVEAU_DEBUG_DEFAULT=3
CONFIG_DRM_NOUVEAU_BACKLIGHT=y
# CONFIG_DRM_MGA is not set
# CONFIG_DRM_SIS is not set
# CONFIG_DRM_VIA is not set
# CONFIG_DRM_SAVAGE is not set
# CONFIG_DRM_VGEM is not set
# CONFIG_DRM_UDL is not set
# CONFIG_DRM_AST is not set
# CONFIG_DRM_MGAG200 is not set
# CONFIG_DRM_CIRRUS_QEMU is not set
# CONFIG_DRM_QXL is not set
# CONFIG_DRM_BOCHS is not set
CONFIG_DRM_BRIDGE=y

#
# Display Interface Bridges
#
# CONFIG_DRM_NXP_PTN3460 is not set
# CONFIG_DRM_PARADE_PS8622 is not set

#
# Frame buffer Devices
#
CONFIG_FB=y
CONFIG_FIRMWARE_EDID=y
CONFIG_FB_CMDLINE=y
# CONFIG_FB_DDC is not set
# CONFIG_FB_BOOT_VESA_SUPPORT is not set
CONFIG_FB_CFB_FILLRECT=y
CONFIG_FB_CFB_COPYAREA=y
CONFIG_FB_CFB_IMAGEBLIT=y
# CONFIG_FB_CFB_REV_PIXELS_IN_BYTE is not set
CONFIG_FB_SYS_FILLRECT=m
CONFIG_FB_SYS_COPYAREA=m
CONFIG_FB_SYS_IMAGEBLIT=m
CONFIG_FB_FOREIGN_ENDIAN=y
CONFIG_FB_BOTH_ENDIAN=y
# CONFIG_FB_BIG_ENDIAN is not set
# CONFIG_FB_LITTLE_ENDIAN is not set
CONFIG_FB_SYS_FOPS=m
# CONFIG_FB_SVGALIB is not set
CONFIG_FB_MACMODES=y
CONFIG_FB_BACKLIGHT=y
CONFIG_FB_MODE_HELPERS=y
CONFIG_FB_TILEBLITTING=y

#
# Frame buffer hardware drivers
#
# CONFIG_FB_CIRRUS is not set
# CONFIG_FB_PM2 is not set
# CONFIG_FB_CYBER2000 is not set
CONFIG_FB_OF=y
# CONFIG_FB_ASILIANT is not set
# CONFIG_FB_IMSTT is not set
# CONFIG_FB_VGA16 is not set
# CONFIG_FB_UVESA is not set
# CONFIG_FB_OPENCORES is not set
# CONFIG_FB_S1D13XXX is not set
# CONFIG_FB_NVIDIA is not set
# CONFIG_FB_RIVA is not set
# CONFIG_FB_I740 is not set
# CONFIG_FB_MATROX is not set
# CONFIG_FB_RADEON is not set
# CONFIG_FB_ATY128 is not set
# CONFIG_FB_ATY is not set
# CONFIG_FB_S3 is not set
# CONFIG_FB_SAVAGE is not set
# CONFIG_FB_SIS is not set
# CONFIG_FB_NEOMAGIC is not set
# CONFIG_FB_KYRO is not set
# CONFIG_FB_3DFX is not set
# CONFIG_FB_VOODOO1 is not set
# CONFIG_FB_VT8623 is not set
# CONFIG_FB_TRIDENT is not set
# CONFIG_FB_ARK is not set
# CONFIG_FB_PM3 is not set
# CONFIG_FB_CARMINE is not set
# CONFIG_FB_SMSCUFX is not set
# CONFIG_FB_UDL is not set
# CONFIG_FB_IBM_GXT4500 is not set
# CONFIG_FB_VIRTUAL is not set
# CONFIG_FB_METRONOME is not set
# CONFIG_FB_MB862XX is not set
# CONFIG_FB_BROADSHEET is not set
# CONFIG_FB_AUO_K190X is not set
# CONFIG_FB_SIMPLE is not set
# CONFIG_FB_SSD1307 is not set
# CONFIG_FB_SM712 is not set
CONFIG_BACKLIGHT_LCD_SUPPORT=y
# CONFIG_LCD_CLASS_DEVICE is not set
CONFIG_BACKLIGHT_CLASS_DEVICE=y
# CONFIG_BACKLIGHT_GENERIC is not set
# CONFIG_BACKLIGHT_PM8941_WLED is not set
# CONFIG_BACKLIGHT_ADP8860 is not set
# CONFIG_BACKLIGHT_ADP8870 is not set
# CONFIG_BACKLIGHT_LM3639 is not set
# CONFIG_BACKLIGHT_GPIO is not set
# CONFIG_BACKLIGHT_LV5207LP is not set
# CONFIG_BACKLIGHT_BD6107 is not set
# CONFIG_VGASTATE is not set
CONFIG_HDMI=y

#
# Console display driver support
#
# CONFIG_VGA_CONSOLE is not set
CONFIG_DUMMY_CONSOLE=y
CONFIG_DUMMY_CONSOLE_COLUMNS=80
CONFIG_DUMMY_CONSOLE_ROWS=25
CONFIG_FRAMEBUFFER_CONSOLE=y
CONFIG_FRAMEBUFFER_CONSOLE_DETECT_PRIMARY=y
# CONFIG_FRAMEBUFFER_CONSOLE_ROTATION is not set
# CONFIG_LOGO is not set
CONFIG_SOUND=m
CONFIG_SOUND_OSS_CORE=y
CONFIG_SOUND_OSS_CORE_PRECLAIM=y
CONFIG_SND=m
CONFIG_SND_TIMER=m
CONFIG_SND_PCM=m
CONFIG_SND_RAWMIDI=m
CONFIG_SND_SEQUENCER=m
CONFIG_SND_SEQ_DUMMY=m
CONFIG_SND_OSSEMUL=y
CONFIG_SND_MIXER_OSS=m
CONFIG_SND_PCM_OSS=m
CONFIG_SND_PCM_OSS_PLUGINS=y
CONFIG_SND_PCM_TIMER=y
CONFIG_SND_SEQUENCER_OSS=y
CONFIG_SND_HRTIMER=m
CONFIG_SND_SEQ_HRTIMER_DEFAULT=y
CONFIG_SND_DYNAMIC_MINORS=y
CONFIG_SND_MAX_CARDS=32
# CONFIG_SND_SUPPORT_OLD_API is not set
CONFIG_SND_PROC_FS=y
# CONFIG_SND_VERBOSE_PROCFS is not set
# CONFIG_SND_VERBOSE_PRINTK is not set
# CONFIG_SND_DEBUG is not set
CONFIG_SND_RAWMIDI_SEQ=m
# CONFIG_SND_OPL3_LIB_SEQ is not set
# CONFIG_SND_OPL4_LIB_SEQ is not set
# CONFIG_SND_SBAWE_SEQ is not set
# CONFIG_SND_EMU10K1_SEQ is not set
CONFIG_SND_DRIVERS=y
# CONFIG_SND_DUMMY is not set
CONFIG_SND_ALOOP=m
CONFIG_SND_VIRMIDI=m
# CONFIG_SND_MTPAV is not set
# CONFIG_SND_SERIAL_U16550 is not set
# CONFIG_SND_MPU401 is not set
# CONFIG_SND_PCI is not set

#
# HD-Audio
#
CONFIG_SND_HDA_PREALLOC_SIZE=64
# CONFIG_SND_PPC is not set
CONFIG_SND_AOA=m
CONFIG_SND_AOA_FABRIC_LAYOUT=m
CONFIG_SND_AOA_ONYX=m
CONFIG_SND_AOA_TAS=m
CONFIG_SND_AOA_TOONIE=m
CONFIG_SND_AOA_SOUNDBUS=m
CONFIG_SND_AOA_SOUNDBUS_I2S=m
# CONFIG_SND_USB is not set
# CONFIG_SND_FIREWIRE is not set
# CONFIG_SND_SOC is not set
# CONFIG_SOUND_PRIME is not set

#
# HID support
#
CONFIG_HID=m
# CONFIG_HID_BATTERY_STRENGTH is not set
CONFIG_HIDRAW=y
CONFIG_UHID=m
CONFIG_HID_GENERIC=m

#
# Special HID drivers
#
# CONFIG_HID_A4TECH is not set
# CONFIG_HID_ACRUX is not set
CONFIG_HID_APPLE=m
# CONFIG_HID_APPLEIR is not set
# CONFIG_HID_AUREAL is not set
# CONFIG_HID_BELKIN is not set
# CONFIG_HID_BETOP_FF is not set
# CONFIG_HID_CHERRY is not set
# CONFIG_HID_CHICONY is not set
# CONFIG_HID_CORSAIR is not set
# CONFIG_HID_PRODIKEYS is not set
# CONFIG_HID_CP2112 is not set
# CONFIG_HID_CYPRESS is not set
# CONFIG_HID_DRAGONRISE is not set
# CONFIG_HID_EMS_FF is not set
# CONFIG_HID_ELECOM is not set
# CONFIG_HID_ELO is not set
# CONFIG_HID_EZKEY is not set
# CONFIG_HID_GEMBIRD is not set
# CONFIG_HID_GFRM is not set
# CONFIG_HID_HOLTEK is not set
# CONFIG_HID_GT683R is not set
# CONFIG_HID_KEYTOUCH is not set
# CONFIG_HID_KYE is not set
# CONFIG_HID_UCLOGIC is not set
# CONFIG_HID_WALTOP is not set
# CONFIG_HID_GYRATION is not set
# CONFIG_HID_ICADE is not set
# CONFIG_HID_TWINHAN is not set
# CONFIG_HID_KENSINGTON is not set
# CONFIG_HID_LCPOWER is not set
# CONFIG_HID_LENOVO is not set
# CONFIG_HID_LOGITECH is not set
CONFIG_HID_MAGICMOUSE=m
# CONFIG_HID_MICROSOFT is not set
# CONFIG_HID_MONTEREY is not set
CONFIG_HID_MULTITOUCH=m
# CONFIG_HID_NTRIG is not set
# CONFIG_HID_ORTEK is not set
# CONFIG_HID_PANTHERLORD is not set
# CONFIG_HID_PENMOUNT is not set
# CONFIG_HID_PETALYNX is not set
# CONFIG_HID_PICOLCD is not set
# CONFIG_HID_PLANTRONICS is not set
# CONFIG_HID_PRIMAX is not set
# CONFIG_HID_ROCCAT is not set
# CONFIG_HID_SAITEK is not set
# CONFIG_HID_SAMSUNG is not set
# CONFIG_HID_SONY is not set
# CONFIG_HID_SPEEDLINK is not set
# CONFIG_HID_STEELSERIES is not set
# CONFIG_HID_SUNPLUS is not set
# CONFIG_HID_RMI is not set
# CONFIG_HID_GREENASIA is not set
# CONFIG_HID_SMARTJOYPLUS is not set
# CONFIG_HID_TIVO is not set
# CONFIG_HID_TOPSEED is not set
# CONFIG_HID_THINGM is not set
# CONFIG_HID_THRUSTMASTER is not set
# CONFIG_HID_WACOM is not set
# CONFIG_HID_WIIMOTE is not set
# CONFIG_HID_XINMO is not set
# CONFIG_HID_ZEROPLUS is not set
# CONFIG_HID_ZYDACRON is not set
# CONFIG_HID_SENSOR_HUB is not set

#
# USB HID support
#
CONFIG_USB_HID=m
CONFIG_HID_PID=y
CONFIG_USB_HIDDEV=y

#
# USB HID Boot Protocol drivers
#
# CONFIG_USB_KBD is not set
# CONFIG_USB_MOUSE is not set

#
# I2C HID support
#
# CONFIG_I2C_HID is not set
CONFIG_USB_OHCI_BIG_ENDIAN_DESC=y
CONFIG_USB_OHCI_BIG_ENDIAN_MMIO=y
CONFIG_USB_OHCI_LITTLE_ENDIAN=y
CONFIG_USB_SUPPORT=y
CONFIG_USB_COMMON=m
CONFIG_USB_ARCH_HAS_HCD=y
CONFIG_USB=m
CONFIG_USB_ANNOUNCE_NEW_DEVICES=y

#
# Miscellaneous USB options
#
CONFIG_USB_DEFAULT_PERSIST=y
CONFIG_USB_DYNAMIC_MINORS=y
# CONFIG_USB_OTG is not set
# CONFIG_USB_OTG_WHITELIST is not set
# CONFIG_USB_OTG_BLACKLIST_HUB is not set
# CONFIG_USB_ULPI_BUS is not set
CONFIG_USB_MON=m
CONFIG_USB_WUSB_CBAF=m
# CONFIG_USB_WUSB_CBAF_DEBUG is not set

#
# USB Host Controller Drivers
#
CONFIG_USB_C67X00_HCD=m
CONFIG_USB_XHCI_HCD=m
CONFIG_USB_XHCI_PCI=m
CONFIG_USB_XHCI_PLATFORM=m
CONFIG_USB_EHCI_HCD=m
CONFIG_USB_EHCI_ROOT_HUB_TT=y
CONFIG_USB_EHCI_TT_NEWSCHED=y
CONFIG_USB_EHCI_PCI=m
CONFIG_USB_EHCI_HCD_PPC_OF=y
CONFIG_USB_EHCI_HCD_PLATFORM=m
# CONFIG_USB_OXU210HP_HCD is not set
# CONFIG_USB_ISP116X_HCD is not set
# CONFIG_USB_ISP1362_HCD is not set
# CONFIG_USB_FOTG210_HCD is not set
CONFIG_USB_OHCI_HCD=m
CONFIG_USB_OHCI_HCD_PPC_OF_BE=y
CONFIG_USB_OHCI_HCD_PPC_OF_LE=y
CONFIG_USB_OHCI_HCD_PPC_OF=y
CONFIG_USB_OHCI_HCD_PCI=m
# CONFIG_USB_OHCI_HCD_SSB is not set
CONFIG_USB_OHCI_HCD_PLATFORM=m
CONFIG_USB_UHCI_HCD=m
CONFIG_USB_SL811_HCD=m
# CONFIG_USB_SL811_HCD_ISO is not set
CONFIG_USB_R8A66597_HCD=m
CONFIG_USB_HCD_BCMA=m
CONFIG_USB_HCD_SSB=m
# CONFIG_USB_HCD_TEST_MODE is not set

#
# USB Device Class drivers
#
CONFIG_USB_ACM=m
CONFIG_USB_PRINTER=m
CONFIG_USB_WDM=m
CONFIG_USB_TMC=m

#
# NOTE: USB_STORAGE depends on SCSI but BLK_DEV_SD may
#

#
# also be needed; see USB_STORAGE Help for more info
#
CONFIG_USB_STORAGE=m
# CONFIG_USB_STORAGE_DEBUG is not set
CONFIG_USB_STORAGE_REALTEK=m
CONFIG_REALTEK_AUTOPM=y
CONFIG_USB_STORAGE_DATAFAB=m
CONFIG_USB_STORAGE_FREECOM=m
CONFIG_USB_STORAGE_ISD200=m
CONFIG_USB_STORAGE_USBAT=m
CONFIG_USB_STORAGE_SDDR09=m
CONFIG_USB_STORAGE_SDDR55=m
CONFIG_USB_STORAGE_JUMPSHOT=m
CONFIG_USB_STORAGE_ALAUDA=m
CONFIG_USB_STORAGE_ONETOUCH=m
CONFIG_USB_STORAGE_KARMA=m
CONFIG_USB_STORAGE_CYPRESS_ATACB=m
CONFIG_USB_STORAGE_ENE_UB6250=m
# CONFIG_USB_UAS is not set

#
# USB Imaging devices
#
# CONFIG_USB_MDC800 is not set
# CONFIG_USB_MICROTEK is not set
# CONFIG_USBIP_CORE is not set
# CONFIG_USB_MUSB_HDRC is not set
# CONFIG_USB_DWC3 is not set
# CONFIG_USB_DWC2 is not set
# CONFIG_USB_CHIPIDEA is not set
# CONFIG_USB_ISP1760 is not set

#
# USB port drivers
#
CONFIG_USB_SERIAL=m
CONFIG_USB_SERIAL_GENERIC=y
# CONFIG_USB_SERIAL_SIMPLE is not set
CONFIG_USB_SERIAL_AIRCABLE=m
CONFIG_USB_SERIAL_ARK3116=m
CONFIG_USB_SERIAL_BELKIN=m
CONFIG_USB_SERIAL_CH341=m
CONFIG_USB_SERIAL_WHITEHEAT=m
CONFIG_USB_SERIAL_DIGI_ACCELEPORT=m
CONFIG_USB_SERIAL_CP210X=m
CONFIG_USB_SERIAL_CYPRESS_M8=m
CONFIG_USB_SERIAL_EMPEG=m
CONFIG_USB_SERIAL_FTDI_SIO=m
CONFIG_USB_SERIAL_VISOR=m
CONFIG_USB_SERIAL_IPAQ=m
CONFIG_USB_SERIAL_IR=m
CONFIG_USB_SERIAL_EDGEPORT=m
CONFIG_USB_SERIAL_EDGEPORT_TI=m
# CONFIG_USB_SERIAL_F81232 is not set
CONFIG_USB_SERIAL_GARMIN=m
CONFIG_USB_SERIAL_IPW=m
CONFIG_USB_SERIAL_IUU=m
CONFIG_USB_SERIAL_KEYSPAN_PDA=m
CONFIG_USB_SERIAL_KEYSPAN=m
CONFIG_USB_SERIAL_KLSI=m
CONFIG_USB_SERIAL_KOBIL_SCT=m
CONFIG_USB_SERIAL_MCT_U232=m
# CONFIG_USB_SERIAL_METRO is not set
CONFIG_USB_SERIAL_MOS7720=m
CONFIG_USB_SERIAL_MOS7840=m
# CONFIG_USB_SERIAL_MXUPORT is not set
CONFIG_USB_SERIAL_NAVMAN=m
CONFIG_USB_SERIAL_PL2303=m
CONFIG_USB_SERIAL_OTI6858=m
CONFIG_USB_SERIAL_QCAUX=m
CONFIG_USB_SERIAL_QUALCOMM=m
CONFIG_USB_SERIAL_SPCP8X5=m
CONFIG_USB_SERIAL_SAFE=m
# CONFIG_USB_SERIAL_SAFE_PADDED is not set
CONFIG_USB_SERIAL_SIERRAWIRELESS=m
CONFIG_USB_SERIAL_SYMBOL=m
CONFIG_USB_SERIAL_TI=m
CONFIG_USB_SERIAL_CYBERJACK=m
CONFIG_USB_SERIAL_XIRCOM=m
CONFIG_USB_SERIAL_WWAN=m
CONFIG_USB_SERIAL_OPTION=m
CONFIG_USB_SERIAL_OMNINET=m
CONFIG_USB_SERIAL_OPTICON=m
# CONFIG_USB_SERIAL_XSENS_MT is not set
# CONFIG_USB_SERIAL_WISHBONE is not set
CONFIG_USB_SERIAL_SSU100=m
# CONFIG_USB_SERIAL_QT2 is not set
CONFIG_USB_SERIAL_DEBUG=m

#
# USB Miscellaneous drivers
#
# CONFIG_USB_EMI62 is not set
# CONFIG_USB_EMI26 is not set
# CONFIG_USB_ADUTUX is not set
# CONFIG_USB_SEVSEG is not set
# CONFIG_USB_RIO500 is not set
# CONFIG_USB_LEGOTOWER is not set
CONFIG_USB_LCD=m
CONFIG_USB_LED=m
# CONFIG_USB_CYPRESS_CY7C63 is not set
# CONFIG_USB_CYTHERM is not set
# CONFIG_USB_IDMOUSE is not set
# CONFIG_USB_FTDI_ELAN is not set
CONFIG_USB_APPLEDISPLAY=m
# CONFIG_USB_SISUSBVGA is not set
# CONFIG_USB_LD is not set
# CONFIG_USB_TRANCEVIBRATOR is not set
# CONFIG_USB_IOWARRIOR is not set
CONFIG_USB_TEST=m
# CONFIG_USB_EHSET_TEST_FIXTURE is not set
# CONFIG_USB_ISIGHTFW is not set
# CONFIG_USB_YUREX is not set
CONFIG_USB_EZUSB_FX2=m
# CONFIG_USB_HSIC_USB3503 is not set
# CONFIG_USB_LINK_LAYER_TEST is not set
# CONFIG_USB_CHAOSKEY is not set
# CONFIG_USB_ATM is not set

#
# USB Physical Layer drivers
#
CONFIG_USB_PHY=y
CONFIG_NOP_USB_XCEIV=m
# CONFIG_USB_GPIO_VBUS is not set
# CONFIG_USB_ISP1301 is not set
# CONFIG_USB_GADGET is not set
# CONFIG_USB_LED_TRIG is not set
# CONFIG_UWB is not set
# CONFIG_MMC is not set
# CONFIG_MEMSTICK is not set
CONFIG_NEW_LEDS=y
CONFIG_LEDS_CLASS=y
# CONFIG_LEDS_CLASS_FLASH is not set

#
# LED drivers
#
# CONFIG_LEDS_BCM6328 is not set
# CONFIG_LEDS_BCM6358 is not set
# CONFIG_LEDS_LM3530 is not set
# CONFIG_LEDS_LM3642 is not set
CONFIG_LEDS_PCA9532=m
# CONFIG_LEDS_PCA9532_GPIO is not set
# CONFIG_LEDS_GPIO is not set
CONFIG_LEDS_LP3944=m
# CONFIG_LEDS_LP5521 is not set
# CONFIG_LEDS_LP5523 is not set
# CONFIG_LEDS_LP5562 is not set
# CONFIG_LEDS_LP8501 is not set
# CONFIG_LEDS_LP8860 is not set
CONFIG_LEDS_PCA955X=m
# CONFIG_LEDS_PCA963X is not set
CONFIG_LEDS_REGULATOR=m
CONFIG_LEDS_BD2802=m
# CONFIG_LEDS_LT3593 is not set
# CONFIG_LEDS_TCA6507 is not set
# CONFIG_LEDS_TLC591XX is not set
# CONFIG_LEDS_LM355x is not set

#
# LED driver for blink(1) USB RGB LED is under Special HID drivers (HID_THINGM)
#
# CONFIG_LEDS_BLINKM is not set

#
# LED Triggers
#
CONFIG_LEDS_TRIGGERS=y
CONFIG_LEDS_TRIGGER_TIMER=m
# CONFIG_LEDS_TRIGGER_ONESHOT is not set
CONFIG_LEDS_TRIGGER_HEARTBEAT=m
CONFIG_LEDS_TRIGGER_BACKLIGHT=m
# CONFIG_LEDS_TRIGGER_CPU is not set
# CONFIG_LEDS_TRIGGER_GPIO is not set
CONFIG_LEDS_TRIGGER_DEFAULT_ON=m

#
# iptables trigger is under Netfilter config (LED target)
#
# CONFIG_LEDS_TRIGGER_TRANSIENT is not set
# CONFIG_LEDS_TRIGGER_CAMERA is not set
CONFIG_ACCESSIBILITY=y
# CONFIG_INFINIBAND is not set
CONFIG_EDAC_ATOMIC_SCRUB=y
CONFIG_EDAC_SUPPORT=y
# CONFIG_EDAC is not set
CONFIG_RTC_LIB=y
CONFIG_RTC_CLASS=y
CONFIG_RTC_HCTOSYS=y
CONFIG_RTC_HCTOSYS_DEVICE="rtc0"
CONFIG_RTC_SYSTOHC=y
CONFIG_RTC_SYSTOHC_DEVICE="rtc0"
# CONFIG_RTC_DEBUG is not set

#
# RTC interfaces
#
CONFIG_RTC_INTF_SYSFS=y
CONFIG_RTC_INTF_PROC=y
CONFIG_RTC_INTF_DEV=y
# CONFIG_RTC_INTF_DEV_UIE_EMUL is not set
# CONFIG_RTC_DRV_TEST is not set

#
# I2C RTC drivers
#
# CONFIG_RTC_DRV_ABB5ZES3 is not set
# CONFIG_RTC_DRV_ABX80X is not set
CONFIG_RTC_DRV_DS1307=m
CONFIG_RTC_DRV_DS1374=m
# CONFIG_RTC_DRV_DS1374_WDT is not set
CONFIG_RTC_DRV_DS1672=m
# CONFIG_RTC_DRV_DS3232 is not set
# CONFIG_RTC_DRV_HYM8563 is not set
CONFIG_RTC_DRV_MAX6900=m
CONFIG_RTC_DRV_RS5C372=m
CONFIG_RTC_DRV_ISL1208=m
# CONFIG_RTC_DRV_ISL12022 is not set
# CONFIG_RTC_DRV_ISL12057 is not set
CONFIG_RTC_DRV_X1205=m
# CONFIG_RTC_DRV_PCF2127 is not set
# CONFIG_RTC_DRV_PCF8523 is not set
CONFIG_RTC_DRV_PCF8563=m
# CONFIG_RTC_DRV_PCF85063 is not set
CONFIG_RTC_DRV_PCF8583=m
CONFIG_RTC_DRV_M41T80=m
# CONFIG_RTC_DRV_M41T80_WDT is not set
CONFIG_RTC_DRV_BQ32K=m
CONFIG_RTC_DRV_S35390A=m
CONFIG_RTC_DRV_FM3130=m
CONFIG_RTC_DRV_RX8581=m
CONFIG_RTC_DRV_RX8025=m
# CONFIG_RTC_DRV_EM3027 is not set
# CONFIG_RTC_DRV_RV3029C2 is not set
# CONFIG_RTC_DRV_RV8803 is not set

#
# SPI RTC drivers
#

#
# Platform RTC drivers
#
CONFIG_RTC_DRV_CMOS=m
CONFIG_RTC_DRV_DS1286=m
CONFIG_RTC_DRV_DS1511=m
CONFIG_RTC_DRV_DS1553=m
# CONFIG_RTC_DRV_DS1685_FAMILY is not set
CONFIG_RTC_DRV_DS1742=m
# CONFIG_RTC_DRV_DS2404 is not set
CONFIG_RTC_DRV_STK17TA8=m
CONFIG_RTC_DRV_M48T86=m
CONFIG_RTC_DRV_M48T35=m
CONFIG_RTC_DRV_M48T59=m
CONFIG_RTC_DRV_MSM6242=m
CONFIG_RTC_DRV_BQ4802=m
CONFIG_RTC_DRV_RP5C01=m
CONFIG_RTC_DRV_V3020=m
# CONFIG_RTC_DRV_ZYNQMP is not set

#
# on-CPU RTC drivers
#
CONFIG_RTC_DRV_GENERIC=y
# CONFIG_RTC_DRV_SNVS is not set

#
# HID Sensor RTC drivers
#
# CONFIG_RTC_DRV_HID_SENSOR_TIME is not set
CONFIG_DMADEVICES=y
# CONFIG_DMADEVICES_DEBUG is not set

#
# DMA Devices
#
CONFIG_DMA_ENGINE=y
CONFIG_DMA_OF=y
# CONFIG_FSL_EDMA is not set
# CONFIG_INTEL_IDMA64 is not set
# CONFIG_DW_DMAC is not set
# CONFIG_DW_DMAC_PCI is not set

#
# DMA Clients
#
CONFIG_ASYNC_TX_DMA=y
# CONFIG_DMATEST is not set
# CONFIG_AUXDISPLAY is not set
CONFIG_UIO=m
# CONFIG_UIO_CIF is not set
CONFIG_UIO_PDRV_GENIRQ=m
CONFIG_UIO_DMEM_GENIRQ=m
# CONFIG_UIO_AEC is not set
# CONFIG_UIO_SERCOS3 is not set
CONFIG_UIO_PCI_GENERIC=m
# CONFIG_UIO_NETX is not set
# CONFIG_UIO_PRUSS is not set
# CONFIG_UIO_MF624 is not set
# CONFIG_VIRT_DRIVERS is not set

#
# Virtio drivers
#
# CONFIG_VIRTIO_PCI is not set
# CONFIG_VIRTIO_MMIO is not set

#
# Microsoft Hyper-V guest support
#
# CONFIG_STAGING is not set

#
# Hardware Spinlock drivers
#

#
# Clock Source drivers
#
# CONFIG_ATMEL_PIT is not set
# CONFIG_SH_TIMER_CMT is not set
# CONFIG_SH_TIMER_MTU2 is not set
# CONFIG_SH_TIMER_TMU is not set
# CONFIG_EM_TIMER_STI is not set
# CONFIG_MAILBOX is not set
CONFIG_IOMMU_SUPPORT=y

#
# Generic IOMMU Pagetable Support
#

#
# Remoteproc drivers
#
# CONFIG_STE_MODEM_RPROC is not set

#
# Rpmsg drivers
#

#
# SOC (System On Chip) specific Drivers
#
# CONFIG_SUNXI_SRAM is not set
# CONFIG_SOC_TI is not set
CONFIG_PM_DEVFREQ=y

#
# DEVFREQ Governors
#
CONFIG_DEVFREQ_GOV_SIMPLE_ONDEMAND=m
CONFIG_DEVFREQ_GOV_PERFORMANCE=m
CONFIG_DEVFREQ_GOV_POWERSAVE=m
CONFIG_DEVFREQ_GOV_USERSPACE=m

#
# DEVFREQ Drivers
#
# CONFIG_PM_DEVFREQ_EVENT is not set
# CONFIG_EXTCON is not set
# CONFIG_MEMORY is not set
# CONFIG_IIO is not set
# CONFIG_NTB is not set
# CONFIG_VME_BUS is not set
# CONFIG_PWM is not set
CONFIG_IRQCHIP=y
# CONFIG_IPACK_BUS is not set
# CONFIG_RESET_CONTROLLER is not set
# CONFIG_FMC is not set

#
# PHY Subsystem
#
CONFIG_GENERIC_PHY=y
# CONFIG_PHY_PXA_28NM_HSIC is not set
# CONFIG_PHY_PXA_28NM_USB2 is not set
# CONFIG_BCM_KONA_USB2_PHY is not set
# CONFIG_POWERCAP is not set
# CONFIG_MCB is not set

#
# Performance monitor support
#
CONFIG_RAS=y
# CONFIG_THUNDERBOLT is not set

#
# Android
#
# CONFIG_ANDROID is not set
# CONFIG_LIBNVDIMM is not set
# CONFIG_NVMEM is not set
# CONFIG_STM is not set
# CONFIG_STM_DUMMY is not set
# CONFIG_STM_SOURCE_CONSOLE is not set
# CONFIG_INTEL_TH is not set

#
# FPGA Configuration Support
#
# CONFIG_FPGA is not set

#
# File systems
#
CONFIG_EXT2_FS=m
CONFIG_EXT2_FS_XATTR=y
CONFIG_EXT2_FS_POSIX_ACL=y
CONFIG_EXT2_FS_SECURITY=y
CONFIG_EXT3_FS=m
CONFIG_EXT3_FS_POSIX_ACL=y
CONFIG_EXT3_FS_SECURITY=y
CONFIG_EXT4_FS=m
CONFIG_EXT4_FS_POSIX_ACL=y
CONFIG_EXT4_FS_SECURITY=y
# CONFIG_EXT4_ENCRYPTION is not set
# CONFIG_EXT4_DEBUG is not set
CONFIG_JBD2=m
# CONFIG_JBD2_DEBUG is not set
CONFIG_FS_MBCACHE=m
CONFIG_REISERFS_FS=m
# CONFIG_REISERFS_CHECK is not set
# CONFIG_REISERFS_PROC_INFO is not set
CONFIG_REISERFS_FS_XATTR=y
CONFIG_REISERFS_FS_POSIX_ACL=y
CONFIG_REISERFS_FS_SECURITY=y
CONFIG_JFS_FS=m
CONFIG_JFS_POSIX_ACL=y
CONFIG_JFS_SECURITY=y
# CONFIG_JFS_DEBUG is not set
# CONFIG_JFS_STATISTICS is not set
CONFIG_XFS_FS=m
CONFIG_XFS_QUOTA=y
CONFIG_XFS_POSIX_ACL=y
CONFIG_XFS_RT=y
# CONFIG_XFS_WARN is not set
# CONFIG_XFS_DEBUG is not set
CONFIG_GFS2_FS=m
CONFIG_GFS2_FS_LOCKING_DLM=y
CONFIG_OCFS2_FS=m
CONFIG_OCFS2_FS_O2CB=m
CONFIG_OCFS2_FS_USERSPACE_CLUSTER=m
CONFIG_OCFS2_FS_STATS=y
CONFIG_OCFS2_DEBUG_MASKLOG=y
# CONFIG_OCFS2_DEBUG_FS is not set
CONFIG_BTRFS_FS=m
CONFIG_BTRFS_FS_POSIX_ACL=y
# CONFIG_BTRFS_FS_CHECK_INTEGRITY is not set
# CONFIG_BTRFS_FS_RUN_SANITY_TESTS is not set
# CONFIG_BTRFS_DEBUG is not set
# CONFIG_BTRFS_ASSERT is not set
CONFIG_NILFS2_FS=m
# CONFIG_F2FS_FS is not set
# CONFIG_FS_DAX is not set
CONFIG_FS_POSIX_ACL=y
CONFIG_EXPORTFS=y
CONFIG_FILE_LOCKING=y
CONFIG_FSNOTIFY=y
CONFIG_DNOTIFY=y
CONFIG_INOTIFY_USER=y
CONFIG_FANOTIFY=y
# CONFIG_FANOTIFY_ACCESS_PERMISSIONS is not set
CONFIG_QUOTA=y
CONFIG_QUOTA_NETLINK_INTERFACE=y
CONFIG_PRINT_QUOTA_WARNING=y
# CONFIG_QUOTA_DEBUG is not set
CONFIG_QUOTA_TREE=m
CONFIG_QFMT_V1=m
CONFIG_QFMT_V2=m
CONFIG_QUOTACTL=y
CONFIG_AUTOFS4_FS=m
CONFIG_FUSE_FS=m
CONFIG_CUSE=m
# CONFIG_OVERLAY_FS is not set

#
# Caches
#
CONFIG_FSCACHE=m
CONFIG_FSCACHE_STATS=y
# CONFIG_FSCACHE_HISTOGRAM is not set
# CONFIG_FSCACHE_DEBUG is not set
# CONFIG_FSCACHE_OBJECT_LIST is not set
CONFIG_CACHEFILES=m
# CONFIG_CACHEFILES_DEBUG is not set
# CONFIG_CACHEFILES_HISTOGRAM is not set

#
# CD-ROM/DVD Filesystems
#
CONFIG_ISO9660_FS=m
CONFIG_JOLIET=y
CONFIG_ZISOFS=y
CONFIG_UDF_FS=m
CONFIG_UDF_NLS=y

#
# DOS/FAT/NT Filesystems
#
CONFIG_FAT_FS=m
CONFIG_MSDOS_FS=m
CONFIG_VFAT_FS=m
CONFIG_FAT_DEFAULT_CODEPAGE=437
CONFIG_FAT_DEFAULT_IOCHARSET="utf8"
CONFIG_NTFS_FS=m
# CONFIG_NTFS_DEBUG is not set
CONFIG_NTFS_RW=y

#
# Pseudo filesystems
#
CONFIG_PROC_FS=y
CONFIG_PROC_KCORE=y
CONFIG_PROC_SYSCTL=y
CONFIG_PROC_PAGE_MONITOR=y
# CONFIG_PROC_CHILDREN is not set
CONFIG_KERNFS=y
CONFIG_SYSFS=y
CONFIG_TMPFS=y
CONFIG_TMPFS_POSIX_ACL=y
CONFIG_TMPFS_XATTR=y
CONFIG_HUGETLBFS=y
CONFIG_HUGETLB_PAGE=y
CONFIG_CONFIGFS_FS=m
CONFIG_MISC_FILESYSTEMS=y
CONFIG_ADFS_FS=m
# CONFIG_ADFS_FS_RW is not set
CONFIG_AFFS_FS=m
CONFIG_ECRYPT_FS=m
# CONFIG_ECRYPT_FS_MESSAGING is not set
CONFIG_HFS_FS=m
CONFIG_HFSPLUS_FS=m
CONFIG_HFSPLUS_FS_POSIX_ACL=y
CONFIG_BEFS_FS=m
# CONFIG_BEFS_DEBUG is not set
CONFIG_BFS_FS=m
CONFIG_EFS_FS=m
# CONFIG_JFFS2_FS is not set
CONFIG_LOGFS=m
CONFIG_CRAMFS=m
CONFIG_SQUASHFS=m
CONFIG_SQUASHFS_FILE_CACHE=y
# CONFIG_SQUASHFS_FILE_DIRECT is not set
CONFIG_SQUASHFS_DECOMP_SINGLE=y
# CONFIG_SQUASHFS_DECOMP_MULTI is not set
# CONFIG_SQUASHFS_DECOMP_MULTI_PERCPU is not set
CONFIG_SQUASHFS_XATTR=y
CONFIG_SQUASHFS_ZLIB=y
# CONFIG_SQUASHFS_LZ4 is not set
CONFIG_SQUASHFS_LZO=y
CONFIG_SQUASHFS_XZ=y
# CONFIG_SQUASHFS_4K_DEVBLK_SIZE is not set
# CONFIG_SQUASHFS_EMBEDDED is not set
CONFIG_SQUASHFS_FRAGMENT_CACHE_SIZE=3
CONFIG_VXFS_FS=m
CONFIG_MINIX_FS=m
CONFIG_OMFS_FS=m
# CONFIG_HPFS_FS is not set
CONFIG_QNX4FS_FS=m
# CONFIG_QNX6FS_FS is not set
CONFIG_ROMFS_FS=m
CONFIG_ROMFS_BACKED_BY_BLOCK=y
# CONFIG_ROMFS_BACKED_BY_MTD is not set
# CONFIG_ROMFS_BACKED_BY_BOTH is not set
CONFIG_ROMFS_ON_BLOCK=y
# CONFIG_PSTORE is not set
CONFIG_SYSV_FS=m
CONFIG_UFS_FS=m
# CONFIG_UFS_FS_WRITE is not set
# CONFIG_UFS_DEBUG is not set
CONFIG_EXOFS_FS=m
# CONFIG_EXOFS_DEBUG is not set
CONFIG_ORE=m
CONFIG_NETWORK_FILESYSTEMS=y
CONFIG_NFS_FS=m
CONFIG_NFS_V2=m
CONFIG_NFS_V3=m
CONFIG_NFS_V3_ACL=y
CONFIG_NFS_V4=m
# CONFIG_NFS_SWAP is not set
CONFIG_NFS_V4_1=y
# CONFIG_NFS_V4_2 is not set
CONFIG_PNFS_FILE_LAYOUT=m
CONFIG_PNFS_OBJLAYOUT=m
CONFIG_PNFS_FLEXFILE_LAYOUT=m
CONFIG_NFS_V4_1_IMPLEMENTATION_ID_DOMAIN="kernel.org"
# CONFIG_NFS_V4_1_MIGRATION is not set
CONFIG_NFS_FSCACHE=y
# CONFIG_NFS_USE_LEGACY_DNS is not set
CONFIG_NFS_USE_KERNEL_DNS=y
CONFIG_NFSD=m
CONFIG_NFSD_V2_ACL=y
CONFIG_NFSD_V3=y
CONFIG_NFSD_V3_ACL=y
CONFIG_NFSD_V4=y
# CONFIG_NFSD_PNFS is not set
# CONFIG_NFSD_V4_SECURITY_LABEL is not set
# CONFIG_NFSD_FAULT_INJECTION is not set
CONFIG_GRACE_PERIOD=m
CONFIG_LOCKD=m
CONFIG_LOCKD_V4=y
CONFIG_NFS_ACL_SUPPORT=m
CONFIG_NFS_COMMON=y
CONFIG_SUNRPC=m
CONFIG_SUNRPC_GSS=m
CONFIG_SUNRPC_BACKCHANNEL=y
CONFIG_RPCSEC_GSS_KRB5=m
# CONFIG_SUNRPC_DEBUG is not set
CONFIG_CEPH_FS=m
# CONFIG_CEPH_FSCACHE is not set
# CONFIG_CEPH_FS_POSIX_ACL is not set
CONFIG_CIFS=m
# CONFIG_CIFS_STATS is not set
CONFIG_CIFS_WEAK_PW_HASH=y
CONFIG_CIFS_UPCALL=y
CONFIG_CIFS_XATTR=y
CONFIG_CIFS_POSIX=y
CONFIG_CIFS_ACL=y
CONFIG_CIFS_DEBUG=y
# CONFIG_CIFS_DEBUG2 is not set
CONFIG_CIFS_DFS_UPCALL=y
# CONFIG_CIFS_SMB2 is not set
CONFIG_CIFS_FSCACHE=y
CONFIG_NCP_FS=m
CONFIG_NCPFS_PACKET_SIGNING=y
CONFIG_NCPFS_IOCTL_LOCKING=y
CONFIG_NCPFS_STRONG=y
CONFIG_NCPFS_NFS_NS=y
CONFIG_NCPFS_OS2_NS=y
# CONFIG_NCPFS_SMALLDOS is not set
CONFIG_NCPFS_NLS=y
CONFIG_NCPFS_EXTRAS=y
CONFIG_CODA_FS=m
CONFIG_AFS_FS=m
# CONFIG_AFS_DEBUG is not set
CONFIG_AFS_FSCACHE=y
CONFIG_NLS=y
CONFIG_NLS_DEFAULT="utf8"
CONFIG_NLS_CODEPAGE_437=m
CONFIG_NLS_CODEPAGE_737=m
CONFIG_NLS_CODEPAGE_775=m
CONFIG_NLS_CODEPAGE_850=m
CONFIG_NLS_CODEPAGE_852=m
CONFIG_NLS_CODEPAGE_855=m
CONFIG_NLS_CODEPAGE_857=m
CONFIG_NLS_CODEPAGE_860=m
CONFIG_NLS_CODEPAGE_861=m
CONFIG_NLS_CODEPAGE_862=m
CONFIG_NLS_CODEPAGE_863=m
CONFIG_NLS_CODEPAGE_864=m
CONFIG_NLS_CODEPAGE_865=m
CONFIG_NLS_CODEPAGE_866=m
CONFIG_NLS_CODEPAGE_869=m
CONFIG_NLS_CODEPAGE_936=m
CONFIG_NLS_CODEPAGE_950=m
CONFIG_NLS_CODEPAGE_932=m
CONFIG_NLS_CODEPAGE_949=m
CONFIG_NLS_CODEPAGE_874=m
CONFIG_NLS_ISO8859_8=m
CONFIG_NLS_CODEPAGE_1250=m
CONFIG_NLS_CODEPAGE_1251=m
CONFIG_NLS_ASCII=m
CONFIG_NLS_ISO8859_1=m
CONFIG_NLS_ISO8859_2=m
CONFIG_NLS_ISO8859_3=m
CONFIG_NLS_ISO8859_4=m
CONFIG_NLS_ISO8859_5=m
CONFIG_NLS_ISO8859_6=m
CONFIG_NLS_ISO8859_7=m
CONFIG_NLS_ISO8859_9=m
CONFIG_NLS_ISO8859_13=m
CONFIG_NLS_ISO8859_14=m
CONFIG_NLS_ISO8859_15=m
CONFIG_NLS_KOI8_R=m
CONFIG_NLS_KOI8_U=m
# CONFIG_NLS_MAC_ROMAN is not set
# CONFIG_NLS_MAC_CELTIC is not set
# CONFIG_NLS_MAC_CENTEURO is not set
# CONFIG_NLS_MAC_CROATIAN is not set
# CONFIG_NLS_MAC_CYRILLIC is not set
# CONFIG_NLS_MAC_GAELIC is not set
# CONFIG_NLS_MAC_GREEK is not set
# CONFIG_NLS_MAC_ICELAND is not set
# CONFIG_NLS_MAC_INUIT is not set
# CONFIG_NLS_MAC_ROMANIAN is not set
# CONFIG_NLS_MAC_TURKISH is not set
CONFIG_NLS_UTF8=m
CONFIG_DLM=m
CONFIG_DLM_DEBUG=y
# CONFIG_BINARY_PRINTF is not set

#
# Library routines
#
CONFIG_RAID6_PQ=m
CONFIG_BITREVERSE=y
# CONFIG_HAVE_ARCH_BITREVERSE is not set
CONFIG_RATIONAL=y
CONFIG_GENERIC_STRNCPY_FROM_USER=y
CONFIG_GENERIC_STRNLEN_USER=y
CONFIG_GENERIC_NET_UTILS=y
CONFIG_GENERIC_PCI_IOMAP=y
CONFIG_GENERIC_IO=y
CONFIG_ARCH_USE_CMPXCHG_LOCKREF=y
CONFIG_CRC_CCITT=m
CONFIG_CRC16=m
CONFIG_CRC_T10DIF=y
CONFIG_CRC_ITU_T=m
CONFIG_CRC32=y
# CONFIG_CRC32_SELFTEST is not set
CONFIG_CRC32_SLICEBY8=y
# CONFIG_CRC32_SLICEBY4 is not set
# CONFIG_CRC32_SARWATE is not set
# CONFIG_CRC32_BIT is not set
CONFIG_CRC7=m
CONFIG_LIBCRC32C=m
CONFIG_CRC8=m
# CONFIG_AUDIT_ARCH_COMPAT_GENERIC is not set
# CONFIG_RANDOM32_SELFTEST is not set
CONFIG_ZLIB_INFLATE=y
CONFIG_ZLIB_DEFLATE=y
CONFIG_LZO_COMPRESS=y
CONFIG_LZO_DECOMPRESS=y
CONFIG_XZ_DEC=y
# CONFIG_XZ_DEC_X86 is not set
CONFIG_XZ_DEC_POWERPC=y
# CONFIG_XZ_DEC_IA64 is not set
# CONFIG_XZ_DEC_ARM is not set
# CONFIG_XZ_DEC_ARMTHUMB is not set
# CONFIG_XZ_DEC_SPARC is not set
CONFIG_XZ_DEC_BCJ=y
# CONFIG_XZ_DEC_TEST is not set
CONFIG_DECOMPRESS_GZIP=y
CONFIG_TEXTSEARCH=y
CONFIG_TEXTSEARCH_KMP=m
CONFIG_TEXTSEARCH_BM=m
CONFIG_TEXTSEARCH_FSM=m
CONFIG_BTREE=y
CONFIG_INTERVAL_TREE=y
CONFIG_ASSOCIATIVE_ARRAY=y
CONFIG_HAS_IOMEM=y
CONFIG_HAS_IOPORT_MAP=y
CONFIG_HAS_DMA=y
CONFIG_CPU_RMAP=y
CONFIG_DQL=y
CONFIG_GLOB=y
# CONFIG_GLOB_SELFTEST is not set
CONFIG_NLATTR=y
CONFIG_ARCH_HAS_ATOMIC64_DEC_IF_POSITIVE=y
CONFIG_LRU_CACHE=m
CONFIG_CORDIC=m
CONFIG_DDR=y
CONFIG_LIBFDT=y
CONFIG_OID_REGISTRY=m
CONFIG_FONT_SUPPORT=y
# CONFIG_FONTS is not set
CONFIG_FONT_8x8=y
CONFIG_FONT_8x16=y
# CONFIG_SG_SPLIT is not set
CONFIG_ARCH_HAS_SG_CHAIN=y

#
# Kernel hacking
#

#
# printk and dmesg options
#
CONFIG_PRINTK_TIME=y
CONFIG_MESSAGE_LOGLEVEL_DEFAULT=4
# CONFIG_DYNAMIC_DEBUG is not set

#
# Compile-time checks and compiler options
#
# CONFIG_DEBUG_INFO is not set
CONFIG_ENABLE_WARN_DEPRECATED=y
CONFIG_ENABLE_MUST_CHECK=y
CONFIG_FRAME_WARN=2048
CONFIG_STRIP_ASM_SYMS=y
# CONFIG_READABLE_ASM is not set
# CONFIG_UNUSED_SYMBOLS is not set
# CONFIG_PAGE_OWNER is not set
CONFIG_DEBUG_FS=y
# CONFIG_HEADERS_CHECK is not set
# CONFIG_DEBUG_SECTION_MISMATCH is not set
CONFIG_SECTION_MISMATCH_WARN_ONLY=y
# CONFIG_DEBUG_FORCE_WEAK_PER_CPU is not set
# CONFIG_MAGIC_SYSRQ is not set
CONFIG_DEBUG_KERNEL=y

#
# Memory Debugging
#
# CONFIG_PAGE_EXTENSION is not set
# CONFIG_DEBUG_OBJECTS is not set
# CONFIG_SLUB_STATS is not set
CONFIG_HAVE_DEBUG_KMEMLEAK=y
# CONFIG_DEBUG_KMEMLEAK is not set
# CONFIG_DEBUG_STACK_USAGE is not set
# CONFIG_DEBUG_VM is not set
# CONFIG_DEBUG_MEMORY_INIT is not set
# CONFIG_DEBUG_PER_CPU_MAPS is not set
CONFIG_HAVE_DEBUG_STACKOVERFLOW=y
# CONFIG_DEBUG_STACKOVERFLOW is not set
# CONFIG_DEBUG_SHIRQ is not set

#
# Debug Lockups and Hangs
#
CONFIG_LOCKUP_DETECTOR=y
CONFIG_HARDLOCKUP_DETECTOR=y
# CONFIG_BOOTPARAM_HARDLOCKUP_PANIC is not set
CONFIG_BOOTPARAM_HARDLOCKUP_PANIC_VALUE=0
# CONFIG_BOOTPARAM_SOFTLOCKUP_PANIC is not set
CONFIG_BOOTPARAM_SOFTLOCKUP_PANIC_VALUE=0
CONFIG_DETECT_HUNG_TASK=y
CONFIG_DEFAULT_HUNG_TASK_TIMEOUT=120
# CONFIG_BOOTPARAM_HUNG_TASK_PANIC is not set
CONFIG_BOOTPARAM_HUNG_TASK_PANIC_VALUE=0
# CONFIG_PANIC_ON_OOPS is not set
CONFIG_PANIC_ON_OOPS_VALUE=0
CONFIG_SCHED_DEBUG=y
CONFIG_SCHED_INFO=y
CONFIG_SCHEDSTATS=y
# CONFIG_SCHED_STACK_END_CHECK is not set
# CONFIG_DEBUG_TIMEKEEPING is not set
CONFIG_TIMER_STATS=y

#
# Lock Debugging (spinlocks, mutexes, etc...)
#
# CONFIG_DEBUG_RT_MUTEXES is not set
# CONFIG_DEBUG_SPINLOCK is not set
# CONFIG_DEBUG_MUTEXES is not set
# CONFIG_DEBUG_WW_MUTEX_SLOWPATH is not set
# CONFIG_DEBUG_LOCK_ALLOC is not set
# CONFIG_PROVE_LOCKING is not set
# CONFIG_LOCK_STAT is not set
# CONFIG_DEBUG_ATOMIC_SLEEP is not set
# CONFIG_DEBUG_LOCKING_API_SELFTESTS is not set
# CONFIG_LOCK_TORTURE_TEST is not set
CONFIG_STACKTRACE=y
# CONFIG_DEBUG_KOBJECT is not set
CONFIG_DEBUG_BUGVERBOSE=y
# CONFIG_DEBUG_LIST is not set
# CONFIG_DEBUG_PI_LIST is not set
# CONFIG_DEBUG_SG is not set
# CONFIG_DEBUG_NOTIFIERS is not set
# CONFIG_DEBUG_CREDENTIALS is not set

#
# RCU Debugging
#
# CONFIG_PROVE_RCU is not set
# CONFIG_SPARSE_RCU_POINTER is not set
# CONFIG_TORTURE_TEST is not set
# CONFIG_RCU_TORTURE_TEST is not set
CONFIG_RCU_CPU_STALL_TIMEOUT=60
# CONFIG_RCU_TRACE is not set
CONFIG_RCU_EQS_DEBUG=y
# CONFIG_DEBUG_BLOCK_EXT_DEVT is not set
# CONFIG_NOTIFIER_ERROR_INJECTION is not set
# CONFIG_FAULT_INJECTION is not set
CONFIG_LATENCYTOP=y
CONFIG_HAVE_FUNCTION_TRACER=y
CONFIG_HAVE_FUNCTION_GRAPH_TRACER=y
CONFIG_HAVE_DYNAMIC_FTRACE=y
CONFIG_HAVE_FTRACE_MCOUNT_RECORD=y
CONFIG_HAVE_SYSCALL_TRACEPOINTS=y
CONFIG_TRACING_SUPPORT=y
# CONFIG_FTRACE is not set

#
# Runtime Testing
#
# CONFIG_LKDTM is not set
# CONFIG_TEST_LIST_SORT is not set
# CONFIG_BACKTRACE_SELF_TEST is not set
# CONFIG_RBTREE_TEST is not set
# CONFIG_INTERVAL_TREE_TEST is not set
# CONFIG_PERCPU_TEST is not set
# CONFIG_ATOMIC64_SELFTEST is not set
# CONFIG_TEST_HEXDUMP is not set
# CONFIG_TEST_STRING_HELPERS is not set
# CONFIG_TEST_KSTRTOX is not set
# CONFIG_TEST_PRINTF is not set
# CONFIG_TEST_RHASHTABLE is not set
# CONFIG_DMA_API_DEBUG is not set
# CONFIG_TEST_LKM is not set
# CONFIG_TEST_USER_COPY is not set
# CONFIG_TEST_BPF is not set
# CONFIG_TEST_FIRMWARE is not set
# CONFIG_TEST_UDELAY is not set
# CONFIG_MEMTEST is not set
# CONFIG_TEST_STATIC_KEYS is not set
# CONFIG_SAMPLES is not set
CONFIG_HAVE_ARCH_KGDB=y
# CONFIG_KGDB is not set
# CONFIG_PPC_DISABLE_WERROR is not set
CONFIG_PPC_WERROR=y
# CONFIG_STRICT_MM_TYPECHECKS is not set
CONFIG_PRINT_STACK_DEPTH=64
# CONFIG_PPC_EMULATED_STATS is not set
# CONFIG_CODE_PATCHING_SELFTEST is not set
# CONFIG_FTR_FIXUP_SELFTEST is not set
# CONFIG_MSI_BITMAP_SELFTEST is not set
# CONFIG_XMON is not set
CONFIG_BOOTX_TEXT=y
# CONFIG_PPC_EARLY_DEBUG is not set
CONFIG_STRICT_DEVMEM=y

#
# Security options
#
CONFIG_KEYS=y
# CONFIG_PERSISTENT_KEYRINGS is not set
# CONFIG_BIG_KEYS is not set
# CONFIG_ENCRYPTED_KEYS is not set
# CONFIG_SECURITY_DMESG_RESTRICT is not set
CONFIG_SECURITY=y
CONFIG_SECURITYFS=y
CONFIG_SECURITY_NETWORK=y
CONFIG_SECURITY_NETWORK_XFRM=y
CONFIG_SECURITY_PATH=y
CONFIG_LSM_MMAP_MIN_ADDR=32768
CONFIG_SECURITY_SELINUX=y
# CONFIG_SECURITY_SELINUX_BOOTPARAM is not set
# CONFIG_SECURITY_SELINUX_DISABLE is not set
CONFIG_SECURITY_SELINUX_DEVELOP=y
CONFIG_SECURITY_SELINUX_AVC_STATS=y
CONFIG_SECURITY_SELINUX_CHECKREQPROT_VALUE=1
# CONFIG_SECURITY_SELINUX_POLICYDB_VERSION_MAX is not set
# CONFIG_SECURITY_SMACK is not set
CONFIG_SECURITY_TOMOYO=y
CONFIG_SECURITY_TOMOYO_MAX_ACCEPT_ENTRY=2048
CONFIG_SECURITY_TOMOYO_MAX_AUDIT_LOG=1024
# CONFIG_SECURITY_TOMOYO_OMIT_USERSPACE_LOADER is not set
CONFIG_SECURITY_TOMOYO_POLICY_LOADER="/sbin/tomoyo-init"
CONFIG_SECURITY_TOMOYO_ACTIVATION_TRIGGER="/sbin/init"
CONFIG_SECURITY_APPARMOR=y
CONFIG_SECURITY_APPARMOR_BOOTPARAM_VALUE=1
CONFIG_SECURITY_APPARMOR_HASH=y
# CONFIG_SECURITY_YAMA is not set
CONFIG_INTEGRITY=y
# CONFIG_INTEGRITY_SIGNATURE is not set
CONFIG_INTEGRITY_AUDIT=y
# CONFIG_IMA is not set
# CONFIG_EVM is not set
# CONFIG_DEFAULT_SECURITY_SELINUX is not set
# CONFIG_DEFAULT_SECURITY_TOMOYO is not set
# CONFIG_DEFAULT_SECURITY_APPARMOR is not set
CONFIG_DEFAULT_SECURITY_DAC=y
CONFIG_DEFAULT_SECURITY=""
CONFIG_KEYS_COMPAT=y
CONFIG_XOR_BLOCKS=m
CONFIG_ASYNC_CORE=m
CONFIG_ASYNC_XOR=m
CONFIG_ASYNC_PQ=m
CONFIG_CRYPTO=y

#
# Crypto core or helper
#
CONFIG_CRYPTO_ALGAPI=y
CONFIG_CRYPTO_ALGAPI2=y
CONFIG_CRYPTO_AEAD=m
CONFIG_CRYPTO_AEAD2=y
CONFIG_CRYPTO_BLKCIPHER=m
CONFIG_CRYPTO_BLKCIPHER2=y
CONFIG_CRYPTO_HASH=y
CONFIG_CRYPTO_HASH2=y
CONFIG_CRYPTO_RNG=m
CONFIG_CRYPTO_RNG2=y
CONFIG_CRYPTO_RNG_DEFAULT=m
CONFIG_CRYPTO_PCOMP=m
CONFIG_CRYPTO_PCOMP2=y
CONFIG_CRYPTO_AKCIPHER2=y
# CONFIG_CRYPTO_RSA is not set
CONFIG_CRYPTO_MANAGER=y
CONFIG_CRYPTO_MANAGER2=y
# CONFIG_CRYPTO_USER is not set
# CONFIG_CRYPTO_MANAGER_DISABLE_TESTS is not set
CONFIG_CRYPTO_GF128MUL=m
CONFIG_CRYPTO_NULL=m
CONFIG_CRYPTO_NULL2=y
CONFIG_CRYPTO_PCRYPT=m
CONFIG_CRYPTO_WORKQUEUE=y
# CONFIG_CRYPTO_CRYPTD is not set
# CONFIG_CRYPTO_MCRYPTD is not set
CONFIG_CRYPTO_AUTHENC=m
CONFIG_CRYPTO_TEST=m

#
# Authenticated Encryption with Associated Data
#
CONFIG_CRYPTO_CCM=m
CONFIG_CRYPTO_GCM=m
# CONFIG_CRYPTO_CHACHA20POLY1305 is not set
CONFIG_CRYPTO_SEQIV=m
CONFIG_CRYPTO_ECHAINIV=m

#
# Block modes
#
CONFIG_CRYPTO_CBC=m
CONFIG_CRYPTO_CTR=m
CONFIG_CRYPTO_CTS=m
CONFIG_CRYPTO_ECB=m
CONFIG_CRYPTO_LRW=m
CONFIG_CRYPTO_PCBC=m
CONFIG_CRYPTO_XTS=m
# CONFIG_CRYPTO_KEYWRAP is not set

#
# Hash modes
#
CONFIG_CRYPTO_CMAC=m
CONFIG_CRYPTO_HMAC=m
CONFIG_CRYPTO_XCBC=m
CONFIG_CRYPTO_VMAC=m

#
# Digest
#
CONFIG_CRYPTO_CRC32C=m
# CONFIG_CRYPTO_CRC32 is not set
CONFIG_CRYPTO_CRCT10DIF=y
CONFIG_CRYPTO_GHASH=m
# CONFIG_CRYPTO_POLY1305 is not set
CONFIG_CRYPTO_MD4=m
CONFIG_CRYPTO_MD5=y
# CONFIG_CRYPTO_MD5_PPC is not set
CONFIG_CRYPTO_MICHAEL_MIC=m
CONFIG_CRYPTO_RMD128=m
CONFIG_CRYPTO_RMD160=m
CONFIG_CRYPTO_RMD256=m
CONFIG_CRYPTO_RMD320=m
CONFIG_CRYPTO_SHA1=y
# CONFIG_CRYPTO_SHA1_PPC is not set
CONFIG_CRYPTO_SHA256=m
CONFIG_CRYPTO_SHA512=m
CONFIG_CRYPTO_TGR192=m
CONFIG_CRYPTO_WP512=m

#
# Ciphers
#
CONFIG_CRYPTO_AES=y
CONFIG_CRYPTO_ANUBIS=m
CONFIG_CRYPTO_ARC4=m
CONFIG_CRYPTO_BLOWFISH=m
CONFIG_CRYPTO_BLOWFISH_COMMON=m
CONFIG_CRYPTO_CAMELLIA=m
CONFIG_CRYPTO_CAST_COMMON=m
CONFIG_CRYPTO_CAST5=m
CONFIG_CRYPTO_CAST6=m
CONFIG_CRYPTO_DES=m
CONFIG_CRYPTO_FCRYPT=m
CONFIG_CRYPTO_KHAZAD=m
CONFIG_CRYPTO_SALSA20=m
# CONFIG_CRYPTO_CHACHA20 is not set
CONFIG_CRYPTO_SEED=m
CONFIG_CRYPTO_SERPENT=m
CONFIG_CRYPTO_TEA=m
CONFIG_CRYPTO_TWOFISH=m
CONFIG_CRYPTO_TWOFISH_COMMON=m

#
# Compression
#
CONFIG_CRYPTO_DEFLATE=m
CONFIG_CRYPTO_ZLIB=m
CONFIG_CRYPTO_LZO=m
# CONFIG_CRYPTO_842 is not set
# CONFIG_CRYPTO_LZ4 is not set
# CONFIG_CRYPTO_LZ4HC is not set

#
# Random Number Generation
#
CONFIG_CRYPTO_ANSI_CPRNG=m
CONFIG_CRYPTO_DRBG_MENU=m
CONFIG_CRYPTO_DRBG_HMAC=y
# CONFIG_CRYPTO_DRBG_HASH is not set
# CONFIG_CRYPTO_DRBG_CTR is not set
CONFIG_CRYPTO_DRBG=m
CONFIG_CRYPTO_JITTERENTROPY=m
CONFIG_CRYPTO_USER_API=m
CONFIG_CRYPTO_USER_API_HASH=m
CONFIG_CRYPTO_USER_API_SKCIPHER=m
# CONFIG_CRYPTO_USER_API_RNG is not set
# CONFIG_CRYPTO_USER_API_AEAD is not set
CONFIG_CRYPTO_HW=y
# CONFIG_CRYPTO_DEV_NX is not set
# CONFIG_CRYPTO_DEV_VMX is not set
# CONFIG_ASYMMETRIC_KEY_TYPE is not set

#
# Certificates for signature checking
#
CONFIG_SYSTEM_TRUSTED_KEYRING=y
CONFIG_SYSTEM_TRUSTED_KEYS=""
CONFIG_HAVE_KVM_IRQCHIP=y
CONFIG_HAVE_KVM_IRQFD=y
CONFIG_HAVE_KVM_EVENTFD=y
CONFIG_KVM_MMIO=y
CONFIG_KVM_COMPAT=y
CONFIG_VIRTUALIZATION=y
CONFIG_KVM=y
CONFIG_KVM_BOOK3S_HANDLER=y
CONFIG_KVM_BOOK3S_64_HANDLER=y
CONFIG_KVM_BOOK3S_PR_POSSIBLE=y
CONFIG_KVM_BOOK3S_64=m
CONFIG_KVM_BOOK3S_64_PR=m
CONFIG_KVM_XICS=y
```

What hardware are you running? Which driver are you using, radeon or radeonhd?  
Also, in terms of your troubleshooting, so i may understand... your machine is a ppc based amiga with a pcie slot? 
Does your firmware have an x86 emulator built in to execute standard x86 vga bios roms? Can you use standard x86 pcie vga cards or do you require FCODE roms? 
If so, why not try using something other than a RADEON GPU before you come up with the assumption that mesa in total isn't working for anyone?  Don't mean to sound critical, but in a case like this, having another  GPU from a different family and being able to excercise a different code  path can help you isolate and pinpoint where your issue is.
For instance, with nouveau, just because currently mesa 11.0.6 seems to  work on a < NV47 class GPU, doesnt mean it will work with a > NV50  class GPU.  

Don't really deal with RADEON much (only radeon gpu i have ever owned was a hd3870), but wrong colours points to out to some issue with the display format and BE issue. Where are you having the issue, only with 3d apps or with 2d as well. If you are having issues with 2d, what acceleration is Xorg using? XAA, EXA or GLAMOR??? As you can see there is alot to consider. I seem to have some colour issues with egl and not glx. see screenshot below, as you can see the glx game has correct colours, whereas launching the weston compositor (which i believe utilises egl) has issues with the colours, the terminal is meant to be black, not blue... If you have issues with colour in 2d, what acceleration method is in use?

Anyway, posting this here is not the intent of the original thread, perhaps you could start another thread with your issues if you want to discuss further.

---

### Post by luigiburdo on 2015-12-11
Peter  hi, 
i have a quad with a radeonhd x86 in couple with an nvidia 7800gtx  (ppc) 
with lubuntu 14.04.2 everything was working right but was need the mesa patch did by christian for have the right colors in mesa and glx ... i sow you had there the same colors problems that i had in past oo... but after the patch from christian all was good... but the patch is only for radeonhd and on quad right now from 15.04 and up works only in fbdev on radeohd.
this is a video of my quad running mesa and so and so [https://www.youtube.com/watch?v=so35SrThHUs](https://www.youtube.com/watch?v=so35SrThHUs) ...

---

### Post by Peter_Saisanas on 2015-12-11
Luigiburdo,

Clearly, we are NOT talking about the same thing.
For starters referring to distribution derivatives (e.g. Ubuntu, Kubuntu, Lubuntu, etc. ) and release numbers to a Debian user who couldn't care less for Ubuntu is not going to go anywhere.

Please refer to the specific versions of the subsystem, i.e. specifically refer to what version of kernel, what version of xorg, what version of mesa, etc.
Otherwise, frankly this is a waste of time.

Now, I have NO issues with GLX (configured with my kernel, nouveau, nv47 GPU and mesa 11.0.6). Clearly. I have said that the colour issues are for egl or GLES, unless you know exactly what this means please do not mix the two issues.

The oddball config comment, yes im talking to you.
Why do you have a radeon and nvidia gpu? This really will go nowhere.

Please remove your radeon gpu. For starters, if you are trying to diagnose what is going on and what are the issues, why do you seem to persevere with such a bizarre corner case configuration?

Now my original point is, with the following config below;

G5 Quad
Quadro FX4500
Custom Kernel (4.4.0-rc2)
Debian Stretch (Testing repo)
Mesa 11.0.6

KMS is working with nouveau and nv47 class GPU.
2D H/W accel is working with nouveau & Xorg 1:7.7+12.
3D H/W accel is working with nouveau & mesa 11.0.6.

Seeing that what i have described to you seems to be a working configuration, perhaps you should consider trying to get the system running only with your 7800GTX (which also happens to be an nv47 class GPU). 
Yes, KMS works, threre is no xorg.conf, mesa works for glx, there are no kernel command line options. Please note nouveau MSI interrupt issue.

This way, this is more or less an Apple OEM config which more users are likely to have available to test and can provide useful meaningful feedback and hopefully improve a particular your distro of choice...

Your choice really.
And to be fair, this is not right to clutter up a topic on a forum which will basically drift way off topic.

---

### Post by xeno74 on 2015-12-12
Hi all,

I was able to patch the latest Mesa version 11.0.7 because of the problems with the wrong colors. It works with the right colors in 32-bit color depth.

Download: [MesaLib-11.0.7-powerpc-unofficial.tar.bz2]("http://www.xenosoft.de/MesaLib-11.0.7-powerpc-unofficial.tar.bz2")

PLEASE use the [unofficial Mesa version 10.0.4]("http://www.xenosoft.de/MesaLib-10.0.4-powerpc-unofficial.tar.bz2")  if you want a stable and reliable 3D acceleration for Radeon HD graphics cards.

[[IMG]https://lh3.googleusercontent.com/-i17QN_bGJPw/Vmsyr_5z1MI/AAAAAAAABv0/nZAbvcsbKWE/w506-h380/MesaLib-11.0.7_PowerPC_unofficial.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/Hede9nkuYPp")

Cheers,

Christian

> **Peter_Saisanas said:**
> And to be fair, this is not right to clutter up a topic on a forum which will basically drift way off topic.

This sentence isn't very helpful.

---

### Post by luigiburdo on 2015-12-12
> **Peter_Saisanas said:**
> Luigiburdo,

Clearly, we are NOT talking about the same thing.
For starters referring to distribution derivatives (e.g. Ubuntu, Kubuntu, Lubuntu, etc. ) and release numbers to a Debian user who couldn't care less for Ubuntu is not going to go anywhere.

Please refer to the specific versions of the subsystem, i.e. specifically refer to what version of kernel, what version of xorg, what version of mesa, etc.
Otherwise, frankly this is a waste of time.

Now, I have NO issues with GLX (configured with my kernel, nouveau, nv47 GPU and mesa 11.0.6). Clearly. I have said that the colour issues are for egl or GLES, unless you know exactly what this means please do not mix the two issues.

The oddball config comment, yes im talking to you.
Why do you have a radeon and nvidia gpu? This really will go nowhere.

Please remove your radeon gpu. For starters, if you are trying to diagnose what is going on and what are the issues, why do you seem to persevere with such a bizarre corner case configuration?

Now my original point is, with the following config below;

G5 Quad
Quadro FX4500
Custom Kernel (4.4.0-rc2)
Debian Stretch (Testing repo)
Mesa 11.0.6

KMS is working with nouveau and nv47 class GPU.
2D H/W accel is working with nouveau & Xorg 1:7.7+12.
3D H/W accel is working with nouveau & mesa 11.0.6.

Seeing that what i have described to you seems to be a working configuration, perhaps you should consider trying to get the system running only with your 7800GTX (which also happens to be an nv47 class GPU). 
Yes, KMS works, threre is no xorg.conf, mesa works for glx, there are no kernel command line options. Please note nouveau MSI interrupt issue.

This way, this is more or less an Apple OEM config which more users are likely to have available to test and can provide useful meaningful feedback and hopefully improve a particular your distro of choice...

Your choice really.
And to be fair, this is not right to clutter up a topic on a forum which will basically drift way off topic.

Hello man,
my first intention is have g5 quad a machine with a modern gpu up and running , 
my second intention is not have an original configuration because if was like you are writing i will pull off my 7800gtx 512mb never released for quad g5 .
.... last ... we are on ubuntuforums.org  and i write about ubuntu and derivates ... 
the machine working perfect better than quad with only x1900gt .... no problems , zero issue .
kernel? that video was the 4.0 rc3. mesa are the christian mesa unofficial , xorg was the 1.6.... from 1.7 nothing is working as before 

another thing x1000 like is X5000 are modern machine and yes they use uboot who have an x86 emulator inside...
but the gfx issue are not fixed by that emulator are fixed by christian patch ... and this patch work on g5 quad too but is relativ only r600...
for have the colors right working on nvidia ask to Micael Danze and others of x11 devs  to fix it.
wrong colors are because edianess.

ciao e ciao



ps:> .  And to be fair, this is not right to clutter up a topic on a forum which will basically drift way off topic
no one ask you to come and write here, we are all friends here who are sharing our experience with ppc machine new and old with linux for find the best way for have productivity machines.

---

### Post by Peter_Saisanas on 2015-12-12
Perhaps, probably poor choice of wording on my part.

I think you have misunderstood my comment about cluttering the thread.
This in in reference me posting my comments cross referencing the experience of debian testing vs the experience of ubuntu 16.04.

If you want to have some fair cross comparison on what seems to work and not work between the distros, please use the subsystem version numbers, since you posted your comment about lubuntu 14.04.2, doesn't give much info.i.e. what kernel, what xorg, what mesa, etc.. Without giving specific info, It doesn't mean much at all by saying e.g.  Lubuntu 14.04.2 worked better or works.

Also, The thread is about "[X)(L)ubuntu (MATE) 16.04 LTS testing]("http://ubuntuforums.org/showthread.php?t=2301608")".
Since this is the topic, i wont clutter it by adding the specific info about Debian and mesa 11.0.6.

Since it sounds like my comments are not wanted by yourself, if you wanted more info, open up a new thread if you want more info or possibly ask more questions. 
Don't understand what is not "helpful" it is clearly straying off the original topic. And also no reason to get upset to whoever it may concern.

Regarding the x86 emulation in the firmware, nobody actually said it has anything to do with mesa, you are typing this up all by yourself. I merely asked the man if he is in a position to try GPU's from other families and manufacturers.

My original post was that someone claimed that Mesa 11.0.6 doesn't work for anyone on PPC. I have told you otherwise and provided you specific info and logs.

Configure your equipment however you like, i have merely said and explained how it can be made to work easily with what you you have available.
Its your call, i guess you like to complicate things more than need to be. Relax man, nobody's gonna take your radeon card out of your machine... :)

---

### Post by luigiburdo on 2015-12-12
> **Peter_Saisanas said:**
> Perhaps, probably poor choice of wording on my part.

I think you have misunderstood my comment about cluttering the thread.
This in in reference me posting my comments cross referencing the experience of debian testing vs the experience of ubuntu 16.04.

If you want to have some fair cross comparison on what seems to work and not work between the distros, please use the subsystem version numbers, since you posted your comment about lubuntu 14.04.2, doesn't give much info.i.e. what kernel, what xorg, what mesa, etc.. Without giving specific info, It doesn't mean much at all by saying e.g.  Lubuntu 14.04.2 worked better or works.

Also, The thread is about "[X)(L)ubuntu (MATE) 16.04 LTS testing]("http://ubuntuforums.org/showthread.php?t=2301608")".
Since this is the topic, i wont clutter it by adding the specific info about Debian and mesa 11.0.6.

Since it sounds like my comments are not wanted by yourself, if you wanted more info, open up a new thread if you want more info or possibly ask more questions. 
Don't understand what is not "helpful" it is clearly straying off the original topic. And also no reason to get upset to whoever it may concern.

Regarding the x86 emulation in the firmware, nobody actually said it has anything to do with mesa, you are typing this up all by yourself. I merely asked the man if he is in a position to try GPU's from other families and manufacturers.

My original post was that someone claimed that Mesa 11.0.6 doesn't work for anyone on PPC. I have told you otherwise and provided you specific info and logs.

Configure your equipment however you like, i have merely said and explained how it can be made to work easily with what you you have available.
Its your call, i guess you like to complicate things more than need to be. Relax man, nobody's gonna take your radeon card out of your machine... :)

...ok i will say that probably i missunderstand your english because mine is really poor ...
i was thinking you need to know how Christian have the good quality 3D on it machine with mate ... i was reply just say here we use his patch for have on quad g5 equiped with radeonhd with right colors too .
but on quad the last woking release who work with chrisitan patch is the Lubuntu 14.04.2 that i show on the video link. 
Debian is out for my configuration because from the 8 and up the 7800gtx not work and the radeonhd dont work too ... this because the X 1.7 and up.

the only way for have the radeonhd working is with using the FBDEV or install the 4650HD (only this) in the first pcie slot of the quad. with this configuration Ubuntu and sons was working but make the system really unstable . I have to test the last kernels and 4650 in first pcie and check if the freezing stops.
For now The quad working right with "apple boards" in the first pcie 16x and others in 8x gave system perfect working , stable and without issue but repeat only with lubuntu 14.04.2 i test all distros but with not good result like with lubuntu 14.04.2 (and only with it)

add and repeat the colors of mesa and gallium are not right because endianness more stronger with G5 because full big endian and need better fixing .

Different is on X1000 (the machine of Chrisitian) there everything working right  because is a new gen machine and using a totally different firmware compared with apples 


ciao ciao
Luigi

---

### Post by este.el.paz on 2015-12-12
> **luigiburdo said:**
> Gianluca Renzi one of the guy who make the permedia2 drivers for Apus machine confirmed that on debian sid all issue was resolve in ppc side . he have a quad with radeonhd . now on sid last mesa are working too on g5 abd look like without issue.
many issue was resoved from kernel 4.3 and up... we have to hope that mate swap soon to new kernel. right now is 4.2.2x.

@LB:

Interesting, I'm supposed to be subscribed, but got no notifications on these recent posts about Mesa & the G5 . . . .??

But, any thoughts for when the 4.3 kernel will trickle down to the daily's of U-MATE 16.04 PPC??  I'd like to be able to at least boot my G4 ST PM 3,1 with the ATI RAGE card . . . 14.04 Lu seemed to respond to "radeonfb" params . . . but 16.04 gets to a beautiful black screen . . . .

Haven't had a chance to test the 12/08/15 daily in my ***radeon*** G4 iBook . . . to see if that gets beyond the blackness . . . .  : - )

e.

---

### Post by luigiburdo on 2015-12-12
> **este.el.paz said:**
> @LB:

Interesting, I'm supposed to be subscribed, but got no notifications on these recent posts about Mesa & the G5 . . . .??

But, any thoughts for when the 4.3 kernel will trickle down to the daily's of U-MATE 16.04 PPC??  I'd like to be able to at least boot my G4 ST PM 3,1 with the ATI RAGE card . . . 14.04 Lu seemed to respond to "radeonfb" params . . . but 16.04 gets to a beautiful black screen . . . .

Haven't had a chance to test the 12/08/15 daily in my ***radeon*** G4 iBook . . . to see if that gets beyond the blackness . . . .  : - )

e.

Hi este , him chat with me about, look like the 4.3 kernel fixed the issue of mesa with radeon hd and Xorg but for now i didnt test it 
the 16.04 today build gave a strange kernel error on quad and make the installation not possible i had reported to Martin and Company hope they will fix it ..
This error "[COLOR=#404040][FONT=Roboto]Problem  Loading in-kernel X.509 Certificate (-74)"[/FONT][/COLOR]
In any way Christian rise the prize he make the new mesa patch!!! i hope soon i will finally have mate with new mesa working again on quad... Great Christian

---

### Post by este.el.paz on 2015-12-12
> **luigiburdo said:**
> Hi este , him chat with me about, look like the 4.3 kernel fixed the issue of mesa with radeon hd and Xorg but for now i didnt test it 
the 16.04 today build gave a strange kernel error on quad and make the installation not possible i had reported to Martin and Company hope they will fix it ..
This error "[COLOR=#404040][FONT=Roboto]Problem  Loading in-kernel X.509 Certificate (-74)"[/FONT][/COLOR]
In any way Christian rise the prize he make the new mesa patch!!! i hope soon i will finally have mate with new mesa working again on quad... Great Christian

@LB:

Thanks for the reply . . . so, it seems like you are saying that the 4.3 kernel would be in today's daily??  Just a few minutes ago I tested the 12/08/15 daily DVD in my iBook . . . using the boot params I posted earlier and it did boot to a GUI . . . had some fun system sounds ***working*** . . . and I set the time . . . clicked on some stuff, but when I tried to launch FF the window remained blank . . . and then after a minute or so the ****very old*** freezing GUI . . . started to cut in . . . freeze/unfreeze . . . and same with cursor . . . choppy movement . . . .  Took a few tries to get to TTY . . . and then there was a "dump" or "crash" sound and verbose errors . . . "radeon ring stalled" kept repeating . . . .  Assuming that is the "old" kernel . . . and that perhaps today or tomorrow I could zsync the daily and get a clean running system . . . on the iBook??

e

---

### Post by luigiburdo on 2015-12-12
Este yup. on Mate of today and for sure on other ubuntu and sons 16.04 up the kernel is the 4.3.x
I dont know about power book ... the only way to know is test on you machine and if something dont work report .

---

### Post by xeno74 on 2015-12-17
Hi All,

I successfully updated ubuntu MATE 16.04 and 15.10 PowerPC today. After that I have the new Firefox 43 on both systems. :-)

By the way, I have been testing ubuntu MATE PowerPC since December 2014.

[[img]https://lh3.googleusercontent.com/-S-1OdB_ChH4/VnKUVp1vpSI/AAAAAAAABy4/GhfK0TXEYLo/s230-p/ubuntu_MATE_16.04_PowerPC_with_Firefox_43.png[/img]](https://plus.google.com/115515624056477014971/posts/3KjeY2uDtPc)
[[img]https://lh3.googleusercontent.com/-DUklO-OGU3g/VnKU1UsuOXI/AAAAAAAABy8/wbt6cOlwVBg/s115-p/ubuntu_MATE_15.10_PowerPC_with_Firefox_43.png[/img][img]https://lh3.googleusercontent.com/-PyvN4idhEyQ/VnKVrIQG6tI/AAAAAAAABzQ/0-w71rWXl1I/w115-h114-p/ubuntu_MATE_AMIGA_one_X1000.jpg[/img]](https://plus.google.com/115515624056477014971/posts/3KjeY2uDtPc)

On my Intel Mac I use ubuntu MATE 14.04. I like the retrospective future.

Cheers,

Christian&#65279;

---

### Post by este.el.paz on 2015-12-21
Tried to boot the daily from 20151219 on my G4 Powermac 3,1 . . . used 4 different boot params, each got me to some kind of desktop, but, still lots of SQUAHFS errors . . . .  One of them got me to blotchy desktop, but toolbars were there, but when clicked on the menus stayed and overlapped . . . the others, incliuding "abtabt's" method, got a clean desktop image, but no toolbars . . . .  

I'll try it out on my iBook in a few days . . . might be better there . . . the PM has an "ATI RAGE 128" card and it showed an error for "aty128fb" . . . so I tried that out . . . no difference.  U-MATE doesn't seem ready for primetime on PM ST . . . let alone 3-D accel . . . .

e.

---

### Post by xeno74 on 2015-12-25
ubuntu MATE 16.04 PowerPC with DRI3 and the new QupZilla 1.8.9 WebKit web browser:

[[img]https://lh3.googleusercontent.com/-RklxicZd8Zg/Vn0t1h870-I/AAAAAAAAB3s/eez4cFjqbuE/w506-h380/ubuntu_MATE_16.04_PowerPC_with_DRI3_and_QupZilla_1.8.9.png[/img]](https://plus.google.com/115515624056477014971/posts/UzNpW84Kxuh)

I like very much the new ubuntu MATE Welcome screen! Well done!!!!!! :-) Merry Christmas.&#65279;

---

### Post by luigiburdo on 2015-12-28
here continue the issue about the kernel ... but im happy im not the only one 

[https://forums.gentoo.org/viewtopic-p-7852488.html?sid=435ad5dbcbba41808d9e6cc9c6e70b2c](https://forums.gentoo.org/viewtopic-p-7852488.html?sid=435ad5dbcbba41808d9e6cc9c6e70b2c)

[https://forums.suse.com/archive/index.php/t-6987.html](https://forums.suse.com/archive/index.php/t-6987.html)

[https://lkml.org/lkml/2015/12/10/503](https://lkml.org/lkml/2015/12/10/503) 

[http://www.spinics.net/lists/kernel/msg2141123.html](http://www.spinics.net/lists/kernel/msg2141123.html)

---

### Post by este.el.paz on 2015-12-28
@LuigiB:

No, you are not the only one to be having problems with getting it going with U-MATE 16.04 . . . .

---

### Post by luigiburdo on 2015-12-28
> **este.el.paz said:**
> @LuigiB:

No, you are not the only one to be having problems with getting it going with U-MATE 16.04 . . . .

Yes ... i hope the ubuntu team will upgrade the kernel in iso soon!!! im downloading the dayly build every 2 days but the bug continue be there

---

### Post by este.el.paz on 2015-12-28
> **luigiburdo said:**
> Yes ... i hope the ubuntu team will upgrade the kernel in iso soon!!! im downloading the dayly build every 2 days but the bug continue be there

Seems like it, I waited a few days after your post about how the dev had said "they were on it for PPC kernel, done deal" . . . but . . . seemingly no.  It would be good to have some direct word on when, what is it 4.3???  gets injected into the daily iso . . . .  : - 0

e.

---

### Post by luigiburdo on 2015-12-29
> **este.el.paz said:**
> Seems like it, I waited a few days after your post about how the dev had said "they were on it for PPC kernel, done deal" . . . but . . . seemingly no.  It would be good to have some direct word on when, what is it 4.3???  gets injected into the daily iso . . . .  : - 0

e.

Este, look like the bug is not only on ppc ... look like some hw is effected X86 too... and for what i been read here , there and someware ... is because a date in calendar (?).
In any way 4.3.3 and up will fix it ... 
for sure from 10 and more days after my last aptiutude upgrade i loose my 16.04 partition because the kernel and cant install mate 16.04 too...
Now im try to find a way to have 15.10 stable on my G5 quad with 4650HD

---

### Post by este.el.paz on 2015-12-29
> **luigiburdo said:**
> 
In any way 4.3.3 and up will fix it ... 
for sure from 10 and more days after my last aptiutude upgrade i loose my 16.04 partition because the kernel and cant install mate 16.04 too...
Now im try to find a way to have 15.10 stable on my G5 quad with 4650HD

@LB:

Thanks for the follow-up details . . . sounds like a "theme" . . . I had a similar issue with U-MATE 14.04 install where running a normal apt-get upgrade actually dismantled the system by removing packages needed to run the system; that was the first major gaffe I had experienced with ubuntu based distro . . . before that they were pretty much solid . . . .  Still these days I more or less stick with LTS . . . less headache/less often . . . so I'm waiting to see how/when 16.04 pulls together for PPC--first step it has to boot up and run clean on my PM 3,1.  : - )

e..

---

### Post by abtabt on 2015-12-29
> **este.el.paz said:**
> @LB:

Thanks for the follow-up details . . . sounds like a "theme" . . . I had a similar issue with U-MATE 14.04 install where running a normal apt-get upgrade actually dismantled the system by removing packages needed to run the system; that was the first major gaffe I had experienced with ubuntu based distro . . . before that they were pretty much solid . . . .  Still these days I more or less stick with LTS . . . less headache/less often . . . so I'm waiting to see how/when 16.04 pulls together for PPC--first step it has to boot up and run clean on my PM 3,1.  : - )

e..

if you like to try without installing use FW hd OR USB but 1.1 is slow but its work 2.0 is good but FW is fast , Persistent Live 

this save me time 

READ [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

See LiveUsbPendrivePersistent, LiveCDPersistence and this thread for background information.

These instructions demonstrate how a separate boostrap partition can be created using the command mkofboot (this sorts out things like blessing the folder). You could alternatively just extract all the files to a single partition and use the hattrib command (like above) to define the special boot attributes in the /install directory. Use an Apple partition map because it seems yaboot doesn't work with an MS-DOS partition table (use grub2 instead with a MS-DOS partition table).

Use GParted or the command mac-fdisk to partition the drive. Create a boostrap partition, a partition to extract the iso onto and a partition labelled casper-rw. In the example commands below, the usb device is /dev/sdb and has the openfirmware path usb0/@1 .


sudo mac-fdisk /dev/sdb
sudo mkfs.ext4 /dev/sdb3 -L UbuntuUSB
sudo mkfs.ext3 /dev/sdb4 -L casper-rw

sudo mount /dev/sdb3 /mnt
It's easier if we give everybody read/write permissions:

sudo chmod 777 /mnt
Extract the iso contents to the new UbuntuUSB partition. You could use Achive Manager to do this if you prefer.

mkdir UbuntuISO 
sudo mount precise-desktop-powerpc.iso UbuntuISO -o loop
cd UbuntuISO
cp -rf casper dists install pics pool preseed .disk /mnt
Once you have copied the iso, move to the install directory


etc etc etc

 [https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_from_a_USB_drive.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_from_a_USB_drive.3F)

i have a system ready about 10-15 min up and running (like daily build 16.04 ubuntu-mate ,lubuntu etc etc )
and the best is, power up and you have all changes, installs etc  on the FW/USB

---

### Post by este.el.paz on 2015-12-29
@abtabt:  Thanks for those suggestions . . . I haven't had very good luck using the installer to install to an external FW HD in the past . . . it seemed to install partially into the int HD, and then some in the ext HD . . . using GParted to set it up . . . .  So I took that as a message from the cosmos and now I just install into int HD . . . but, I have lately started messing with USB boot . . . however, something still has been showing up as "SQUASHxx error" . . . meaning to me there is a problem with the system itself and wouldn't matter whether I would use "live persistence" or just try to boot from DVD or USB . . . there is a "problem" with the innards/kernel????

But, glad you have it working for you on your iMac . . . mein ist tot or more is less tot . . . .  : - )

e.e.p.

---

### Post by abtabt on 2015-12-29
a starter is to make a usb or FW disk with dd have you done this before ???

like 
Then use the 'dd' command to copy the iso to disk. The terminal command you want will be something like this:

sudo dd if=~/Downloads/ubuntu.iso of=/dev/sdb

 (change Downloads/ubuntu.iso too your iso and check the right /dev/sd?) this erase all at the /dev/sd?

and after that reboot use alt key and choose the USB/FW  drive and then use para when yaboot comes up nomodeset etc etc

---

### Post by luigiburdo on 2015-12-29
> **abtabt said:**
> a starter is to make a usb or FW disk with dd have you done this before ???

like 
Then use the 'dd' command to copy the iso to disk. The terminal command you want will be something like this:

sudo dd if=~/Downloads/ubuntu.iso of=/dev/sdb

 (change Downloads/ubuntu.iso too your iso and check the right /dev/sd?) this erase all at the /dev/sd?

and after that reboot use alt key and choose the USB/FW  drive and then use para when yaboot comes up nomodeset etc etc
thanks for the tips but my intention is have a right working distro from install cd :-) this because will gave to the users more simple installation instructions ;-) 
for now all old versions was working with small tips from the cd ... 
in any way today i make my personal record i make full 15.10 installation on quad with radeon 4650hd without freeze...
i will check tomorrow if the system is usable and not freeze like usual and will write how i did in case of the success.

---

### Post by este.el.paz on 2015-12-29
@abtabt:

Nope . . . no "dd" for me . . . I have LM 17.2 installed on my 09 MBPro and that has "USB Image Writer" . . . GUI . . . very simple to use and it "writes a bootable USB drive."

@Luigi:

Right . . . the iso has to be "OK" before "processing" it in some form . . . .  It has to "work" . . . .  : - )

e

---

### Post by luigiburdo on 2015-12-31
For now the Mate 15.10 with RadeonHD 4650 in the 16x Pcie look like isnt freezing the machine :-) 
Now i will test the mesa last patch from Christian ... letz hope!

---

### Post by luigiburdo on 2016-01-01
Christian ... 15.10 NOT Frizing any more I FOUND THE WAY ... yea! ...
this is the 4650HD 

gigi@gigi-desktop:~$ glxgears 
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
44964 frames in 5.0 seconds = 8992.782 FPS
46205 frames in 5.0 seconds = 9240.932 FPS
45590 frames in 5.0 seconds = 9117.847 FPS
45314 frames in 5.0 seconds = 9062.760 FPS

---

### Post by xeno74 on 2016-01-01
> **luigiburdo said:**
> Christian ... 15.10 NOT Frizing any more I FOUND THE WAY ... yea! ...
this is the 4650HD 

gigi@gigi-desktop:~$ glxgears 
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
44964 frames in 5.0 seconds = 8992.782 FPS
46205 frames in 5.0 seconds = 9240.932 FPS
45590 frames in 5.0 seconds = 9117.847 FPS
45314 frames in 5.0 seconds = 9062.760 FPS

Fantastic values! Well done!!!!!!! :-)

---

### Post by luigiburdo on 2016-01-01
Thanks Christian, 
im using atigpu instead of radeon but in someware the mesa fail in visualizzation  with patch too. will check the mesa 11 patch.
Webgl are spinning like never before


Edit:  Can Play 1080p youtube video too :-)

---

### Post by xeno74 on 2016-01-01
> **luigiburdo said:**
> Thanks Christian, 
im using atigpu instead of radeon but in someware the mesa fail in visualizzation  with patch too. will check the mesa 11 patch.
Webgl are spinning like never before


Edit:  Can Play 1080p youtube video too :-)

Great news! Screenshot  p l e a s e.

---

### Post by luigiburdo on 2016-01-01
Christian did you use the amdgpu on Xorg ? is really much much much much and much faster compared the radeon!

note: the mesa patch are not working right on amdgpu but for what i can have the opportunity to see... wow are incredible!
as i say before webgl are faster like never see before on quad!

---

### Post by xeno74 on 2016-01-02
> **luigiburdo said:**
> Christian did you use the amdgpu on Xorg ? is really much much much much and much faster compared the radeon!

note: the mesa patch are not working right on amdgpu but for what i can have the opportunity to see... wow are incredible!
as i say before webgl are faster like never see before on quad!

I installed the packages **xserver-xorg-video-amdgpu** and **libdrm-amdgpu1** on my ubuntu MATE 16.04. After that I modified the xorg.conf.

```

Section "Device"
  Identifier "Amdgpu"
  Driver "amdgpu"
EndSection

```

Unfortunately there isn't an AMDGPU driver for my Radeon HD6870 available.

Error message:

```
(EE) No devices detected.
```

---

### Post by luigiburdo on 2016-01-02
chistian i m using the stock 4.2.22 kernel 
and installed the firmware not free too. installed the xserver-video amdgpu and removed the radeon, nouveau, fbdev
i just made the amdgpu module load and forced it from xorg.conf set all the dri load and set dri to 1 in options.
dri3 on my xorg is not working i hope in 16.04 if and when the kernel error will fixed.
your 6870 is supported by amdgpu . 
i hope you will have it running you will not recognize your x1000 , finally ppc have the right performances on linux!

---

### Post by luigiburdo on 2016-01-02
> vgigi@gigi-desktop:~$ sudo dmesg | grep amdgpu[    0.000000] Kernel command line: root=UUID=915bd882-043d-4f95-bf7b-8737e7ac5f02 ro amdgpu.powerplay=1 amdgpu.semaphores=1 
[    7.444030] amdgpu: unknown parameter 'powerplay' ignored
[    7.447682] amdgpu: unknown parameter 'semaphores' ignored
[    7.451793] [drm] amdgpu kernel modesetting enabled.

the ignored are because supported by lastest kernel ;-)

Xorg.conf
> Section "Module"        Load  "glx"
        Load  "dri"
        Load  "dri2"
        Load  "dri3"




> 
       #Option     "SWcursor"                  # [<bool>]
        #Option     "HWcursor"                  # [<bool>]
        #Option     "NoAccel"                   # [<bool>]
        #Option     "ShadowFB"                  # [<bool>]
        #Option     "VideoKey"                  # <i>
        #Option     "WrappedFB"                 # [<bool>]
        Option     "GLXVBlank"                  "0"
        #Option     "ZaphodHeads"               # <str>
        Option     "PageFlip"                   "0"
        #Option     "SwapLimit"                 "<i>
        #Option     "AsyncUTSDFS"               # [<bool>]
        #Option     "AccelMethod"               "EXA"
        Option "dri" "1"
        Option "dri2" "1"
        Option "dri3" "1"
        Identifier  "Card0"
        Driver      "amdgpu"
        BusID       "PCI:10:0:0"





---

### Post by luigiburdo on 2016-01-03
Christian, made some test.
installed the Xserver-video radeon ... 
and compared before ... i have the video slower, the audio is not clean and this is glx gears ... 
the  more strange thing is this ! libGL error: failed to load driver: r600
but all is working gigi@gigi-desktop:~$  vblank_mode=0 glxgearslibGL error: image driver extension not found
libGL error: failed to load driver: r600
ATTENTION: default value of option vblank_mode overridden by environment.
6090 frames in 5.0 seconds = 1217.987 FPS
6172 frames in 5.0 seconds = 1234.295 FPS

---

### Post by luigiburdo on 2016-01-03
and New YEAR suprize! ... I made the 6570 Working thanks amdgpu!
Christian .. The 1080p Video on youtube ;-)


[ATTACH=CONFIG]266521[/ATTACH]

Forget Christian a little help here.
On 15.10 there are the mesa 11.02 can i install your patch of 11.x? 
I will use the same way of 10.04 or need to copy the archive unpacked in usr/lib and make the export ld .. so and so ?

---

### Post by xeno74 on 2016-01-03
> **luigiburdo said:**
> 
Forget Christian a little help here.
On 15.10 there are the mesa 11.02 can i install your patch of 11.x? 
I will use the same way of 10.04 or need to copy the archive unpacked in usr/lib and make the export ld .. so and so ?

You could try out some unofficial Mesa packages.

Downloads:

[MesaLib-10.0.4-powerpc-unofficial.tar.bz2]("http://www.xenosoft.de/MesaLib-10.0.4-powerpc-unofficial.tar.bz2")
[MesaLib-11.0.7-powerpc-unofficial.tar.bz2]("http://www.xenosoft.de/MesaLib-11.0.7-powerpc-unofficial.tar.bz2")

Extract them in your home folder and rename the original **r600_dri.so** to **r600_dri.so.bak**:

```
sudo mv /usr/lib/powerpc-linux-gnu/dri/r600_dri.so /usr/lib/powerpc-linux-gnu/dri/r600_dri.so.bak
```

Copy the patched **r600_dri.so** to /usr/lib/powerpc-linux-gnu/dri (for example Mesa 10.0.4):

```
sudo cp mesa-10.0.4/lib/dri/r600_dri.so /usr/lib/powerpc-linux-gnu/dri
```

Afterwards, please logout and then login.

By the way, I removed the package xserver-xorg-video-radeon on ubuntu MATE 16.04.

After that I modified the xorg.conf.

```

Section "Device"
  Identifier "Amdgpu"
  Driver "amdgpu"
EndSection

```

Unfortunately I have only a black box with glxgears.

---

### Post by luigiburdo on 2016-01-03
umm... about your issue   the rendering of windows and video is faster compared before or you dont see any difference there?  

I found another thing with 6570 + Firefox 42 and kernel 4.2.16 i can play 1080p video  , with 6570 + firefox 43 and kernel 4.2.22 i cant play video at all! 
The 6570 Turks dont have audio play on 4650 all was working if i dont count the random freezing of the system. (before amdgpu was not random... was only freezing after couple of seconds)

i had been try your the patches before asking  but all the time it open the software resterized on 6570 and mesa continue be the 11.02 ... this why i had been ask your help ... but unfortunally i was making all right need to investigate better.

after many test i understand one thing the amdgpu Xorg is using the Radeon module too (probably if not drivers present on amdgpu module?) but in my case i have the system working, before  with radeon xorg nothing was going...
In any way it can be a good step lets hope for the future Christian!

---

### Post by rican-linux on 2016-01-04
Hey the Lubuntu devs are looking for testers for their Alpha 1 release. If anyone has the please go through QA tests in ISO tracker. Thanks!

---

### Post by luigiburdo on 2016-01-04
Rican, 
i will test it  :-) in any way better make a new thread about asking for testers!

---

### Post by kotzen.hank on 2016-01-06
> **luigiburdo said:**
> and New YEAR suprize! ... I made the 6570 Working thanks amdgpu!
Christian .. The 1080p Video on youtube ;-)


[ATTACH=CONFIG]266521[/ATTACH]

Hello Luigui, so Ubuntu Mate 15.10 Work 100% in Quad G5? how you do that? Can you described step by step for me ? I need install 15.10 in my Quad G5 With Radeon HD.

---

### Post by luigiburdo on 2016-01-07
> [COLOR=#000000] Ubuntu Mate 15.10 Work 100% in Quad G5[/COLOR]

Yes on RadeonHD 4650HD but random freeze ... > [COLOR=#000000][FONT=Ubuntu Mono] Option      "NoRenderAccel" "True"[/FONT][/COLOR] can be the key for stop random freezing .
with 6570HD i dont have 3d acceleration and audio  but full working without issue .

Im preparing a video for help who need to install mate on PowerMac G5 with RadeonHD

 
Soon i will make a new kernel build i hope will fix the audio problems and hoping the 3d too! and will share it

---

### Post by ernsteiswuerfel on 2016-01-09
Can't boot my Power Mac G5 (7,3) from daily live (08.01.2016). Same error as luigiburdo in #34: [COLOR=#000000]"[/COLOR][COLOR=#404040][FONT=Roboto]Problem Loading in-kernel X.509 Certificate (-74)"[/FONT][/COLOR]

---

### Post by luigiburdo on 2016-01-09
Just build the new kernel im testing it and share with instuction to install mate 15.10 and it

[ATTACH=CONFIG]266632[/ATTACH]


the mate 16.04  continue be problematic for the kernel issue

---

### Post by xeno74 on 2016-01-10
The Alpha1 of ubuntu MATE 16.04 PowerPC works fantastic! After an update I got MATE 1.12.1 and Firefox 43.0.4. :-)&#65279;

[[img]https://lh3.googleusercontent.com/-CV-Sn2-beAw/VpJ-VS22vRI/AAAAAAAAB5k/bUeoxJQjOqE/w506-h380/ubuntu_MATE_16.04_Alpha1_PowerPC_MATE_1.12.1_Firefox_43.0.4.png[/img]](https://plus.google.com/115515624056477014971/posts/aRCr7e4Nb25)

---

### Post by este.el.paz on 2016-01-11
> **xeno74 said:**
> The Alpha1 of ubuntu MATE 16.04 PowerPC works fantastic! After an update I got MATE 1.12.1 and Firefox 43.0.4. :-)&#65279;


Based on this hopeful data I zsync'd the 16.04 daily (1/10/16 'merican dating) and Brasero'd it to a DVD.  Trying "live" and then the longer boot params that have worked for my Powermac 3,1 . . . brought like a mile long list of "SQUASHFS" errors . . . leading to a "kernel panic" . . . .  Gave up on it.

A little while later on my iBook G4 lower spec unit using the "xxxxxxxxxxxxxxxxxx radeon.agpmode=-1" boot params . . . got me into a working GUI that didn't freeze . . . I'll have to spend some more time with it to see if it's fantastic or just . . . working.  : - )

---

### Post by kotzen.hank on 2016-01-11
> **luigiburdo said:**
> Yes on RadeonHD 4650HD but random freeze ...  can be the key for stop random freezing .
with 6570HD i dont have 3d acceleration and audio  but full working without issue .

Im preparing a video for help who need to install mate on PowerMac G5 with RadeonHD

 
Soon i will make a new kernel build i hope will fix the audio problems and hoping the 3d too! and will share it

Thank you So Much Luigi! I am waiting for your video tutorial!

---

### Post by xeno74 on 2016-01-14
Hi All,

There is the latest kernel 4.4 available for the Power Mac G5. Very impressive!

Cheers,

Christian

On 14 January 2016 at 09:42 AM, Peter Saisanas wrote:
> Hi Logan,
> The kernel version is quite old (3.16.7). Perhaps you can try something newer. Nouveau continually has improvements practically with each newer kernel version.
>
> Perhaps something to consider, try the easy way out and use a pre-compiled kernel deb package that i have available. I have kernels as new as 4.4.0 available suitable for Powermac G5's.
> At least these could perhaps be a better baseline as these kernels are known to be working for many Powermac G5's (AGP & PCIe GPU's along with a few generations of nVidia GPU's (some even older than yours). Makes it easier to have a side by side comparison.
> Your call, link is below if interested.
>
> [https://drive.google.com/folderview?id=0B8pqd5Ots1vfT2puX09CYjEwcFk&usp=drive_web](https://drive.google.com/folderview?id=0B8pqd5Ots1vfT2puX09CYjEwcFk&usp=drive_web)
>
> Many have used them successfully in the past and have got their G5 Powermacs running with nouveau.
>
> I'm not so sure that MSI interrupts are ever enabled on AGP GPU's in the first place (PCIe based GPU's are a different story).
> It would be interesting to see your cat /proc/interrupts log as well.
>
> Regarding your EDID issue, can you try the other DVI connector of your video card or cable or alternatively try another display out if the issue still persists.
>
> Most Apple OEM ATI Radeon GPU's have their own issues as well. But that's another story.
>
> Regards,
> Peter

---

### Post by luigiburdo on 2016-01-16
Christian check :-)

[https://www.youtube.com/watch?v=5P2HtBfVdwY](https://www.youtube.com/watch?v=5P2HtBfVdwY)


im sure will be need a new Xeno parch :-P :-P

---

### Post by este.el.paz on 2016-01-16
> **luigiburdo said:**
> Christian check :-)

[https://www.youtube.com/watch?v=5P2HtBfVdwY](https://www.youtube.com/watch?v=5P2HtBfVdwY)


im sure will be need a new Xeno parch :-P :-P

@LB:

Music . . . over the top . . . very funny . . . .  Perhaps next time, "Faces come out in the rain" by the Doors?????

e.e.p.

---

### Post by xeno74 on 2016-01-21
We are already testing the Linux Git merge updates for the kernel 4.5. :-)&#65279;

[IMG]https://lh3.googleusercontent.com/-Q_-iOrOyylw/Vp-G2ZT7OiI/AAAAAAAAB-4/BENr2JJ_BGk/w955-h523-no/ubuntu_MATE_16.04_PowerPC_kernel_4.5.0alpha7.png[/IMG]

**Explanation about the unofficial Mesa version**

In my point of view, the problem is in the source file **p_format.h** in the directory **src/gallium/include/pipe/**.  There is some code for translating colors for big-endian machines. The  problem is, this code is only for the CPU. I mean for LLVMpipe for the  CPU. The Radeon graphics cards don't need this translating code but IBM  pSeries machines without graphics cards need this code. This code  translates the colors in a wrong way for Radeon graphics cards. I  removed this code and after compiling Mesa again, the colors are  displayed correct. The Mesa guys told me, that I have broken their  LLVMpipe translating code. But it doesn't matter me because we have the  right colors. [IMG]http://forum.hyperion-entertainment.biz/images/smilies/icon_e_smile.gif[/IMG] I released some unofficial Mesa versions with this patch.

Downloads: [http://www.supertuxkart-amiga.de/amiga/mesalib-unofficial.html](http://www.supertuxkart-amiga.de/amiga/mesalib-unofficial.html)

---

### Post by ernsteiswuerfel on 2016-01-23
Still the same [COLOR=#000000][COLOR=#000000]"[/COLOR][/COLOR][COLOR=#404040][FONT=Roboto]Problem Loading in-kernel X.509 Certificate (-74)"[/FONT][/COLOR] error with the daily .iso and thus unable to boot my Powermac 7,3... :( It seems I will have to wait for the 4.4.-kernel series to magically resolve this issue?

---

### Post by este.el.paz on 2016-01-23
> **ernsteiswuerfel said:**
> Still the same [COLOR=#000000][COLOR=#000000]"[/COLOR][/COLOR][COLOR=#404040][FONT=Roboto]Problem Loading in-kernel X.509 Certificate (-74)"[/FONT][/COLOR] error with the daily .iso and thus unable to boot my Powermac 7,3... :( It seems I will have to wait for the 4.4.-kernel series to magically resolve this issue?

@ernstw:

Burned the daily today as well, using boot params got me to a bunch of "fails" and SQUASHFS, errors . . . so I shut down and just hit "return" key on the reboot . . . I got the same error as you are showing here, then it went to a "force TTY" . . . and it showed a "log in" prompt . . . not remembering what I should put I thought it was failing again, so I typed "sudo reboot" . . . and the screen went black for a minute or more, it "flashed" black, then the cursor appeared and a then a somewhat low resolution desktop appeared!!!!  But, it was asking me to log in as "other" . . . asking for a "name" seemed to accept "ubuntu" . . . but I couldn't get the password . . . so I shut down.  A little while later I thought that maybe "live" would be the "password" . . . .

So, possibly this live DVD will work on my PM 3,1 . . . ATI Rage 128 card . . . .  We'll see in a bit . . . .

e....

[Edit:  Success!!!!  This time I typed "live" . . . and I got the same error as ernstw . . . but, I just sat there and stared at the screen . . . and took a couple minutes to load the next error line . . . which again ended with "forcing tty" . . . and a tty login screen opened . . . which I stared at for a few seconds, then I hit "return" . . . nothing typed in . . . and waited for what might have been a couple minutes . . . and voila . . . the cursor . . . and awhile later the live desktop started "populating" . . . took a while, but, I'm typing this in the live desktop . . . no boot params . . . and only the background image is a little low resolution . . . everything else is pretty good . . . so far no freezes, etc . . . .  Don't take "no" for an answer . . . wait for it to change its mind . . . .  Kernel 4.3.0-7-powerpc . . . MATE 1.12.1 . . . today's daily.]

---

### Post by luigiburdo on 2016-01-24
Este,
it means that just need wait for make it running ? Will test it soon. I make a new build of kernel 4.4 stable . I will check if swapping it will make stop have that error after installing. 
Just bored because yesterday i make another time installation of 15.10 after my usuals experiments

---

### Post by luigiburdo on 2016-01-24
Kernel 4.4 stable optimized for G5 Quads with RadeonHD . The nuoveau module is not compiled for not have issue with RadeonHD (drm-kms-helper)
[https://www.dropbox.com/s/eqw6nhr6pxd6tim/kernel4.4.tar.gz?dl=0](https://www.dropbox.com/s/eqw6nhr6pxd6tim/kernel4.4.tar.gz?dl=0)

---

### Post by luigiburdo on 2016-01-24
Este here on quad g5 i type live-powerpc64 and have the "x.509 error etc etc" after waiting ... 
... with the Quad start spin the fans like a turbo jet 
i face the busybox ..Unable to find a medium contaning a live file system

.  (initrd isnt aligned with kernel? probably  this is  why we are facing this problem)
In any way no Desktop at all here ... only big noises by the fans and pump spinning!

---

### Post by este.el.paz on 2016-01-24
@LB:

Well, I know nothing about G5, but on my G4 I just typed "live" . . . or before that time I didn't type anything, I just hit the return key . . . .  When I put the "live-nosplash-powerpc video=aty128fb:1024x768-32@60" boot params in that worked for 14.04 on this same computer . . . it gave me a bunch of SQUASHFS errors . . . .  

So, later today I might try again with the boot params and see if I wait long enough will it "break on through to the other side" . . . and get to to a desktop . . . or, error out . . . .  Haven't played with 15.10 . . . I basically only do LTS in PPC . . . .

e....

---

### Post by ernsteiswuerfel on 2016-01-24
> **este.el.paz said:**
> Success!!!!  This time I typed "live" . . . and I got the same error as ernstw . . . but, I just sat there and stared at the screen . . . and took a couple minutes to load the next error line . . . which again ended with "forcing tty" . . . and a tty login screen opened . . . which I stared at for a few seconds, then I hit "return" . . . nothing typed in . . . and waited for what might have been a couple minutes . . . and voila . . . the cursor . . . and awhile later the live desktop started "populating" . . . took a while, but, I'm typing this in the live desktop . . . no boot params . . . and only the background image is a little low resolution . . . everything else is pretty good . . . so far no freezes, etc . . . .  Don't take "no" for an answer . . . wait for it to change its mind . . . .  Kernel 4.3.0-7-powerpc . . . MATE 1.12.1 . . . today's daily.
Ah, I would not have expected that! Thanks for checking out! So at least I can use this method as a last resort in the case kernel 4.4 still exhibits the same problem... Will have to compile my own kernel then?

interestingly enough on my amd64-gentoo-box I never had this problem with 4.3.x-kernels.

---

### Post by luigiburdo on 2016-01-25
i m thinking that isnt a kernel problem...i have a 4.3-rc5 installed in my quad and is full working.
something is not going right in the distros on powerpc side.

---

### Post by xeno74 on 2016-01-25
Hi All,

I updated ubuntu MATE 16.04 LTS PowerPC yesterday and it works with the kernel 4.5-rc1 and with the kernel 4.5-alpha10 without any problems.

[[IMG]https://lh3.googleusercontent.com/-9__xjwqSoPo/VqX19fCy--I/AAAAAAAACAc/48givWwqT5Q/w506-h380/ubuntu_MATE_16.04_PowerPC_with_kernel_4.5-rc1.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/6gNzrxjUTqp")

Have a nice week! :-)

Rgds,

Christian

Edit: Screenshot of the alpha10:

[IMG]http://zzd10h.amiga-ng.org/X1000/Linux/X1000_16_04_Kernel45rc10.png[/IMG]

---

### Post by este.el.paz on 2016-01-25
Since things seemed to go "OK" on my G4 PM 3,1 with just typing "live" . . . and eventually getting into a "decent" GUI . . . I tried it out on my G4 iBook 933 MHz/646MB RAM . . . I tried "live" and I tried "live-nosplash-powerpc video=ofonly radeon.agp mode=-1" terms that I used for 14.04.  Both ways did get me into a GUI, but everything was slow acting, numerous "system error" windows, couldn't open "Time and Date" to set the time, tried to launch FF and the icon "flashed" . . . but it didn't launch . . . basically it "wasn't working" on the iBook . . . .

Later this week I'll try some more testing on the PM 3, 1 . . . .

e...

---

### Post by abtabt on 2016-01-25
Old G3 Begie 333mz with Mach64 driver and ubuntu -mate 16.04 still going strong

---

### Post by luigiburdo on 2016-01-25
i make a a test here in Qemu ppc 64 kvm dont boot ..
qmu ppc 32 kvm dont boot 

booting without kvm  enabled and have the error in x504 bla bla bla with 32 emulation ... 

with 64 emulation the kernel totally crash

Christian let me know there

edit: Guys can you check if in the firefox 43.0.4 you are able to watch youtube videos ?... here loading forever 

edit2: making the 4.5-rc1 for Quad G5 with RadeonHD support too.... G5 is cooking

---

### Post by este.el.paz on 2016-01-25
> **abtabt said:**
> Old G3 Begie 333mz with Mach64 driver and ubuntu -mate 16.04 still going strong

@abtabt:

Good to know . . . you clearly know what you are doing with linux installs . . . like you are a "G3/G4 whisperer" . . . know how to massage an iso or tweak the boot params to get it to do what you want . . . .  My iBook is "not listening to my commands" as far as 16.04 is concerned . . . .  Seems like the PM ***might*** be willing to listen to me . . . .

e...

---

### Post by xeno74 on 2016-01-27
ubuntu MATE 16.04 PowerPC. It's going to be the release of 16.04 Alpha2 tomorrow.&#65279;

[[img]https://lh3.googleusercontent.com/-C0Hw9OKA4Lc/Vqh7LeKxMXI/AAAAAAAACDo/dW_ESytlF-g/w506-h380/ubuntu_MATE_16.04_PowerPC_with_Firefox_44.png[/img]](https://plus.google.com/115515624056477014971/posts/CLCiGcFWx2R)

New: Firefox 44 and the new Welcome screen.

---

### Post by xeno74 on 2016-01-30
**Ubuntu MATE 16.04 Alpha 2 Released as the Biggest Update Ever**

Links:

- [news.softpedia.com](http://news.softpedia.com/news/ubuntu-mate-16-04-alpha-2-released-as-the-biggest-update-ever-499632.shtml)
- [ubuntu-mate.org](https://ubuntu-mate.org/blog/ubuntu-mate-xenial-alpha2/)

[[img]https://lh3.googleusercontent.com/-aON7UNgs8A8/VqyKZY6GCyI/AAAAAAAACEY/_OHcAJJTxj4/w506-h380/ubuntu_MATE_16.04_Alpha2_PowerPC_1.png[/img]](https://plus.google.com/115515624056477014971/posts/GXzwZZtXqxD)  [[img]https://lh3.googleusercontent.com/-2TVic4F9_HQ/Vqyts9SCBnI/AAAAAAAACFI/sy2qBzQCwrc/w506-h380/ubuntu_MATE_16.04_Alpha2_PowerPC_in_QEMU_KVM.png[/img]](https://plus.google.com/115515624056477014971/posts/6gDJMiV7jAB)

Lubuntu 16.04 Alpha 2 is also available for PowerPC computers: [lubuntu/releases/xenial/alpha-2/xenial-desktop-powerpc.iso](http://cdimage.ubuntu.com/lubuntu/releases/xenial/alpha-2/xenial-desktop-powerpc.iso)

---

### Post by luigiburdo on 2016-01-30
i will check Christian ... lets hope alpha two will work....
I hope soon Mate will run on X5000 too

---

### Post by luigiburdo on 2016-01-30
Tested ... i continue have the kernel Certificate Issue ... No Mate 16.04 for me

---

### Post by este.el.paz on 2016-01-31
> **luigiburdo said:**
> Tested ... i continue have the kernel Certificate Issue ... No Mate 16.04 for me

@LB:

Had some problems doing a "do-release-upgrade" on my PM w/ATI Rage 128 card yesterday . . . so did a "nuke-n-pave" and used the 20160123 MATE Alpha1 install disk I had burned to DVD already to run the install . . . no boot params . . . .  Still shows the "kernel cert" error but moves to log in window quickly . . . and "good" resolution display . . . .  I'll play around with it for awhile . . . .  Seems like there was an issue using "restart" from the desktop drop down menu, that got lost in blackness, but from logged out . . . and from Terminal "reboot" works to move me back into OSX, etc.

I do like the GNOME Floating Feet screensaver . . . very funny . . . .  : - ))))

e...

[Edit:  My usual complaint, "suspend" from the GUI desktop makes the screen go black, but computer keeps spinning . . . and clicking key or mouse doesn't "revive" from suspend . . . have to shut down by power button????  This morning on boot still the "kernel cert" and "aty128fb" error shows, but also a series of "clearing orphaned inode" . . . complaints show up. before quickly loading the log in window . . . .  Perhaps logging out might get "suspend" to work??? probably not.]

---

### Post by luigiburdo on 2016-02-01
> [COLOR=#000000]but moves to log in window quickly . . . and "good" resolution display . . . . I'll play around with it for awhile . . . .[/COLOR]
you lucky here all stop working.... 4ever

---

### Post by ernsteiswuerfel on 2016-02-02
Kernel 4.4.x landed in daily-live so I gave it a try. Unfortunately still the kernel certificate issue. :sad: Even though when I wait for some time I am not able to boot my Powermac 7,3.

After countless "stdin: not a typewriter"-errors the boot process stops after a while dropping me into a busy box shell with:```
(initramfs) unable to find a medium containing a live file system.
```

---

### Post by luigiburdo on 2016-02-02
> **ernsteiswuerfel said:**
> Kernel 4.4.x landed in daily-live so I gave it a try. Unfortunately still the kernel certificate issue. :sad: Even though when I wait for some time I am not able to boot my Powermac 7,3.

After countless "stdin: not a typewriter"-errors the boot process stops after a while dropping me into a busy box shell with:```
(initramfs) unable to find a medium containing a live file system.
```

Exactly what im facing too.

---

### Post by este.el.paz on 2016-02-02
@ernst & LB:

I get the "not a typewriter" lines as well . . . and then it kicks to a "force TTY" . . . now that I've installed the system now it moves faster to the lightdm log in . . . .  So far, as far as I have had time to check, no boot params, and no Xorg.conf file . . . .

I filed a LP bug report, two of them . . . one for the "no suspend"   [https://bugs.launchpad.net/ubuntu-mate/+bug/1541078](https://bugs.launchpad.net/ubuntu-mate/+bug/1541078)

and another for the "blotchy" graphics rendering for images    [https://bugs.launchpad.net/ubuntu-mate/+bug/1541082](https://bugs.launchpad.net/ubuntu-mate/+bug/1541082)

If anyone else has found these problems please click the "This bug effects me too" button . . . or, if other problems such as described here . . . file a bug report on Launchpad.

e....

---

### Post by ernsteiswuerfel on 2016-02-02
@este.el.paz:
Good idea! When I am able to get to desktop I may check if your bugs affect me too. ;)

@luigiburdo and all the others facing that error:
I filed the following bug report for the "Problem Loading in-kernel X.509 Certificate (-74)" & "stdin: not a typewriter" thingy:
[https://bugs.launchpad.net/ubuntu-mate/+bug/1541151](https://bugs.launchpad.net/ubuntu-mate/+bug/1541151)

Please support it if you face the same (non-)booting problem!

---

### Post by este.el.paz on 2016-02-02
> **ernsteiswuerfel said:**
> @este.el.paz:
Good idea! When I am able to get to desktop I may check if your bugs affect me too. ;)

@luigiburdo and all the others facing that error:
I filed the following bug report for the "Problem Loading in-kernel X.509 Certificate (-74)" & "stdin: not a typewriter" thingy:
[https://bugs.launchpad.net/ubuntu-mate/+bug/1541151](https://bugs.launchpad.net/ubuntu-mate/+bug/1541151)

Please support it if you face the same (non-)booting problem!
@Ernst IWfel:

I added my comment to your bug . . . the more people that report their issues via LP the better chances of having something actually change . . . [in theory] . . . but the MATE guys seem pretty motivated to get their system working well for as many systems as possible.  I guess the other thing to do is to go to the QA tracker and add your machine and tag your LP bug numbers there . . . .

e...

---

### Post by ernsteiswuerfel on 2016-02-03
> **este.el.paz said:**
> @ernsteiswuerfel:
I added my comment to your bug . . . the more people that report their issues via LP the better chances of having something actually change . . . [in theory] . . . but the MATE guys seem pretty motivated to get their system working well for as many systems as possible.  I guess the other thing to do is to go to the QA tracker and add your machine and tag your LP bug numbers there . . . .
Thanks!  Being mainly a gentoo user (on amd64) I did not even know the Ubuntu QA tracker. Seems pretty easy and straightforward to use! Only "orks" or "does not work".

I added my issue now:
[http://iso.qa.ubuntu.com/qatracker/milestones/351/builds/111685/testcases](http://iso.qa.ubuntu.com/qatracker/milestones/351/builds/111685/testcases)

---

### Post by este.el.paz on 2016-02-03
> **ernsteiswuerfel said:**
> Thanks!  Being mainly a gentoo user (on amd64) I did not even know the Ubuntu QA tracker. Seems pretty easy and straightforward to use! Only "orks" or "does not work".

I added my issue now:
[http://iso.qa.ubuntu.com/qatracker/milestones/351/builds/111685/testcases](http://iso.qa.ubuntu.com/qatracker/milestones/351/builds/111685/testcases)

@et al:

Well, the QA is really where the devs are paying attention . . . like so far I've gotten no response/request for "apport-collect" from my two bug reports.  So I will try to get over there to the MATE QA tomorrow and post my feedback as well as getting the bugs up there . . . looks like your bug is the only one listed there so far????  There should be more stuff from PPC folks there . . . traditionally there is a little hassle to get the PPC computers listed; but once done shouldn't be too problematic, especially if bug reports are already filed on LP.

e...

[Edit: PS: I added a bug report to report what I believe was an issue with the installer; on the window to "install Fluendo, and other stuff for MP3"  (from memory) there was/is also an "install latest updates" checkbox.  Checking that box usually extends the install time by a bit, but my install went fairly fast.  Afterward, trying to do some ineffectual things to fix the background image, I tried to run "apt update/upgrade" command . . . and a huge list of updates showed up . . . I installed them.  But, seems like if the "latest update" checkbox was working, it would not have been so many packages to install???
[https://bugs.launchpad.net/ubuntu-mate/+bug/1542411](https://bugs.launchpad.net/ubuntu-mate/+bug/1542411)]

---

### Post by luigiburdo on 2016-02-05
i add me in the bug tracker

---

### Post by este.el.paz on 2016-02-05
> **luigiburdo said:**
> i add me in the bug tracker

@LB:

Very cool . . . if you get a chance to add your issues on the QA tracker I think that is ***better**** as far as getting it on the radar screen of anyone who can or will actually do something.  I'm not sure why the Xenial Daily tracker says "archived" . . . in the list with the Alpha 1 & 2 it doesn't say that, only on its own page . . . but, that is where Ernstei & I have both made our stand as far as reporting issues and/or official bugz and such . . . .  He has ***one*** and I have ***three*** . . . that's three times as many . . . .  I think I found a problem with "RhythmBox" today as well . . . not playing tunes from Libre.fm or Last.fm . . . .  Also had to use "alsamixer" to get the sound in the speaker up to where it could be heard . . . but, at least there are sounds straight outa Compton . . . or linux . . . .  : - )

[http://iso.qa.ubuntu.com/qatracker/milestones/351/builds/111685/testcases](http://iso.qa.ubuntu.com/qatracker/milestones/351/builds/111685/testcases)

---

### Post by ernsteiswuerfel on 2016-02-06
> **este.el.paz said:**
> I'm not sure why the Xenial Daily tracker says "archived" . . . in the list with the Alpha 1 & 2 it doesn't say that, only on its own page . . .
Well, don't know that either. Also Alpha 2 bug tracker shows now "released" and I can't add any issues. It seems you have to add issues before a release happens? Have to check out how this QA system works in details when I have time...

---

### Post by este.el.paz on 2016-02-06
> **ernsteiswuerfel said:**
> Well, don't know that either. Also Alpha 2 bug tracker shows now "released" and I can't add any issues. It seems you have to add issues before a release happens? Have to check out how this QA system works in details when I have time...

@ernst:

Well, that is the general idea of what I was talking about, getting the comments posted can be a chore in and of itself . . . .  There was or is an added element of complication, as, in the past they also wanted the machine you were reporting on listed or ID'd in another list . . . but, seemingly this time I just had to be booted up in linux to make my comments and list my bugs . . . I couldn't do it from the OSX side.  I could make the LP bug reports via OSX . . . so, indeed lots of subtle differences and things to learn . . . if only there was more time . . . .  : - )

---

### Post by xeno74 on 2016-02-06
Hi All,

I created an installation initial ramdisk for the installation of ubuntu MATE 16.04 PowerPC with the stable longterm kernel 4.1.17 on the AmigaONE X1000.

[list=1]
[*] Download and extract the kernel image, vmlinux-4.1.17
Download: [vmlinux-4.1.17-AmigaONE_X1000.tar.bz2](http://www.xenosoft.de/vmlinux-4.1.17-AmigaONE_X1000.tar.bz2)
[*] Download the new installation initial ramdisk. I suggest to download it with a right click on the link and then with the menu point "Save target as" or something like this.
Download: [initrd-4.1.17-1.ubuntu16.04-ppc64.gz](http://www.xenosoft.de/initrd-4.1.17-1.ubuntu16.04-ppc64.gz)
[*] Copy them to a USB pen drive or to the CF card
[*] Turn on the AmigaONE X1000 and press F to boot to enter CFE prompt. Insert the USB pen drive.
[*] You can boot the installer using the commands below:
[list=1]
[*] From a USB pen drive:
```
CFE> ramdisk –z –addr=0x24000000 –fatfs usbdisk0:initrd-4.1.17-1.ubuntu16.04-ppc64.gz
```
From the CF card:
```
CFE> ramdisk –z –addr=0x24000000 –fatfs cf0:initrd-4.1.17-1.ubuntu16.04-ppc64.gz
```

[*]```
CFE> setenv bootargs "root=/dev/ramdisk"
```

[*]From a USB pen drive:
```
CFE> boot -elf -noints -fatfs usbdisk0:vmlinux-4.1
```
From the CF card:
```
CFE> boot -elf -noints -fatfs cf0:vmlinux-4.1
```[/list]
[*] Select Language
[*] Select Your Locatation
[*] Detect Keyboard Layout. Select No and Pick from the list
[*] Configure Network
[*] Enter Hostname
[*] Select the Ubuntu Archive Mirror Country - [it is configured for the UK]
[*] Select the Ubuntu archive mirror "ports.ubuntu.com"
[*] Leave the HTTP Proxy parameter blank
[*] When prompted that no kernel modules were found select Yes to continue 
without loading them.
[*] The installer components will be retrieved from the Ubuntu mirror [this will take a
long time]
[*] Enter your Full Name
[*] Enter your username for your account
[*] Enter your password and confirm
[*] Select No to Encrypt your home directory
[*] Confirm your time zone
[*] When prompted for module dm-mod leave the parameter blank and select 
continue
[*] Click Continue at the warning of "Software RAID not available"
[*] Click Continue at the warning of "Logical Volume Manager not available"
[*] You can now partition your disk
**[size=4][color=#FF0000]You must exercise caution when modifying your partition tables![/color][/size]**
[*] The base system will now be retrieved from the mirror site and installed
[*] Select “Install security updates automatically"
[*] At the software selection screen you will be asked to select which *buntu 
flavour(s) you would like to install. You can install as many as you like. To install 
ubuntu MATE arrow down to the “Ubuntu MATE desktop” option and press the 
space bar to mark the option. Now press return to continue.
[*] The additional packages required to install the full desktop will be retrieved and
installed. - [this will take some time to complete depending on the speed of your 
internet connection ]
[*] At “Continue without boot loader” take note of your root partition.
[*] Select Yes to set confirm the system clock is set as UTC.
[*] Select Continue to finish the installation and reboot!
[*] Press F to boot to enter CFE prompt. Remove if necessary and re-insert the USB 
pen drive containing the vmlinux-4.1 kernel. Enter the following commands replacing 
the root partition (sdb9) with the ID of the partition where you installed ubuntu 
MATE.
```
CFE> setenv bootargs "root=/dev/sdb9"
```
From a USB pen drive:
```
CFE> boot -elf -noints -fatfs usbdisk0:vmlinux-4.1
```
From the CF card:
```
CFE> boot -elf -noints -fatfs cf0:vmlinux-4.1
```
[*] Later, you could copy the kernel vmlinux-4.1 to the CF card and configure a CFE menu entry.
```
CFE> setenv -p MENU_2_LABEL "ubuntu MATE 16.04 with kernel 4.1"
```
```
CFE> setenv -p MENU_2_COMMAND 'set pmu -astate=A4 ; setenv bootargs "root=/dev/sdb9 quiet ro splash" ; boot -elf -noints -fatfs cf0:vmlinux-4.1' 
```[/list]

I successfully tested the new installation initial ramdisk for the installation of ubuntu MATE 16.04 with the stable longterm kernel 4.1.17 today.

**PLEASE** test the new installation initial ramdisk.

Cheers,

Christian

---

### Post by josh164 on 2016-02-06
I am using a PM 7,3, 2Ghz DP, Radeon 9600XT.

As of right now I am having the same problems as  				 				 					 						 	[**[COLOR=#000000]ernsteiswuerfel[/COLOR]**]("http://ubuntuforums.org/member.php?u=1997586") and  				 				 					 						 	[**[COLOR=#000000]luigiburdo[/COLOR]**]("http://ubuntuforums.org/member.php?u=1921200") with the 16.04 daily builds.

---

### Post by este.el.paz on 2016-02-06
> **josh164 said:**
> I am using a PM 7,3, 2Ghz DP, Radeon 9600XT.

As of right now I am having the same problems as                                                                                      [**[COLOR=#000000]ernsteiswuerfel[/COLOR]**]("http://ubuntuforums.org/member.php?u=1997586") and                                                                                      [**[COLOR=#000000]luigiburdo[/COLOR]**]("http://ubuntuforums.org/member.php?u=1921200") with the 16.04 daily builds.

@josh:

Historically, in 14.04, the radeon driver wasn't "supported" so some "radeonfb" boot params had to be added . . . ***possibly*** 16.04 has overcome that issue . . . .  But, same thing offered to you, add your data and comments to their bug report, I think they have it linked in their posts as #1541151 . . . and add same data on QA tracker . . . .

I have had problems getting the liveDVD to boot on my radeon driver iBook; but haven't had time to throw at trying to make it work, so I have no "answers" for you . . . at this time.  As mentioned, I waited for several minutes on my PM 3,1 and it ***eventually*** logs in, just using "live" as the boot params . . . .

e...

---

### Post by luigiburdo on 2016-02-06
unhappy you intird isnt compatible with X5000 ... have it working will be great

---

### Post by este.el.paz on 2016-02-06
Filed a bug report on the issues I found booting the liveDVD on my iBook G4 with a radeon card . . . it got me into a clean GUI desktop . . . but launching system monitor, FF, and then trying to launch T-bird . . . seemed to overwhelm the system and the GUI essentially "crashed" or froze . . . had to use power button to get out of it.

[https://bugs.launchpad.net/ubuntu-mate/+bug/1542749](https://bugs.launchpad.net/ubuntu-mate/+bug/1542749)

---

### Post by josh164 on 2016-02-08
I'm downloading today's build (2/08) so I can report this bug in the "daily" QA. 

16.04 seems to be doing well on my iMac G4 with Nvidia graphics, I have only watched it boot a few times, I have not had a lot of time to play with it.

---

### Post by xeno74 on 2016-02-09
ubuntu MATE 16.04 PowerPC with the RC3 of kernel 4.5 and with LibreOffice 5.0.2.2.

[[IMG]https://lh3.googleusercontent.com/-k38JdnEgWfU/VriXkiP4WbI/AAAAAAAACKA/F7ngb_u023U/w506-h380/ubuntu_MATE_16.04_PowerPC_with_kernel_4.5-rc3.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/BgRPacXaKFc")

---

### Post by luigiburdo on 2016-02-09
Im in but with x5000 :-)

[ATTACH=CONFIG]267214[/ATTACH]

---

### Post by Spectre660 on 2016-02-10
Sam460ex

[[IMG]http://forum.hyperion-entertainment.biz/download/file.php?id=1864&mode=view[/IMG]]("http://forum.hyperion-entertainment.biz/download/file.php?id=1864&mode=view")

---

### Post by lowtech2 on 2016-02-10
Hi,

installed Ubuntu Mate 16.04a2 from DVD on my **PowerBook5,8** (15" G4, 2 GB RAM and ATI **Radeon 9700** 128 MB RAM).

Most things work very well on this old mac, really awesome :KS:KS:KS:KS:KS 

_Had this problems:_
- only black screen after booting the installed system from harddisk
  -> have to press F1 or F2 after boot is finished (~30 sec), to see the desktop (no big deal)

- no WLAN
-> sudo apt-get install firmware-b43-installer **solved** this

- battery not detected
-> sudo modprobe pmu_battery and line pmu_battery added to /etc/modules **solved** this

Followed the notes from the Ubuntu PowerpcFAQ, but _could not fix this issues:_
- no 3D
- no sound
- no keyboard backlight (sudo modprobe i2c-dev didn't help)
- installed software (i.e. Gparted) from the "Welcome to Ubuntu MATE" window (Software/Accessories) does not show up in the application menue after install is finished (and reboot)
- are these boot messages normal?
[    2.776923] Loading compiled-in X.509 certificates
[    2.780433] Problem loading in-kernel X.509 certificate (-74)
..
[    7.318885] ata1.00: READ LOG DMA EXT failed, trying unqueued
[    7.318892] ata1.00: failed to get Identify Device Data, Emask 0x40
[    7.318933] ata1.00: failed to set xfermode (err_mask=0x40)
..
[    8.448641] radeon 0000:00:10.0: Invalid ROM contents
[    8.448669] radeon 0000:00:10.0: Invalid ROM contents
[    8.448865] [drm:radeon_get_bios [radeon]] *ERROR* Unable to locate a BIOS ROM

Any hints or ideas?

---

### Post by lowtech2 on 2016-02-10
> **lowtech2 said:**
> 
- installed software (i.e. Gparted) from the "Welcome to Ubuntu MATE" window (Software/Accessories) does not show up in the application menue after install is finished (and reboot)
..**solved**, sorry looked at the wrong place. Gparted shows up in System.

---

### Post by luigiburdo on 2016-02-10
Spectre are you Julian?

... another think we have to ask the ubuntuforums.org to make another thread for PowerPc users ... not only apple :-P

---

### Post by Spectre660 on 2016-02-10
I am.:p
> **luigiburdo said:**
> Spectre are you Julian?

... another think we have to ask the ubuntuforums.org to make another thread for PowerPc users ... not only apple :-P

---

### Post by lowtech2 on 2016-02-11
> **lowtech2 said:**
> Hi,

installed Ubuntu Mate 16.04a2 from DVD on my **PowerBook5,8** (15" G4, 2 GB RAM and ATI **Radeon 9700** 128 MB RAM).
...
...
- no sound
...
**sound works** now after adding line **snd-aoa-i2sbus** to /etc/modules

---

### Post by lowtech2 on 2016-02-12
VLC (media player 2.2.2 Weatherwax (revision 2.2.2-0-g6259d80)) does not display video encoded with **mpeg-2**, only audio. The videos are not css-encrypted. Other formats like mpeg4, h.264 or x.265 work well with VLC! 

DVD playback with VLC failed.

Did I miss something to install?

---

### Post by luigiburdo on 2016-02-13
i think there are some problems with codecs ... im facing really big issues on X5000 with vlc ... there crash after loading

---

### Post by ernsteiswuerfel on 2016-02-14
> **lowtech2 said:**
> Followed the notes from the Ubuntu PowerpcFAQ, but _could not fix this issues:_
- no 3D
- no sound
- no keyboard backlight (sudo modprobe i2c-dev didn't help)
- installed software (i.e. Gparted) from the "Welcome to Ubuntu MATE" window (Software/Accessories) does not show up in the application menue after install is finished (and reboot)
- are these boot messages normal?

Regarding 3D this may be the related bugs (and a workaround):
[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1432949](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1432949)
[https://bugs.freedesktop.org/show_bug.cgi?id=71789](https://bugs.freedesktop.org/show_bug.cgi?id=71789)

And thanks for the detailed description how you solved your driver problems! Done all that before but forgot to write down that stuff properly and then forgot about it. ;)

---

### Post by ernsteiswuerfel on 2016-02-14
Finally got around to try the daily live (13.02.2016) on a PowerBook 5.6. This machine was able to boot the iso, despite some errors:

[COLOR=#333333][FONT=monospace]Errors displayed on the PB:[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]/init: line 7: can't open /dev/sr0: no medium found[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace](repeated 34 times)[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]pwconv: failed to change the mode of /etc/passwd- to 600
[/FONT][/COLOR]
In the end I got to the desktop and was able to install it. For my PowerMac 7,3 the issue still persists. I updated the bug ([https://bugs.launchpad.net/ubuntu-mate/+bug/1541151](https://bugs.launchpad.net/ubuntu-mate/+bug/1541151)) accordingly.

The "no 3D-acceleration for 24bpp screenmodes with ATI Radeon r300-driver" is still around it seems.
[https://bugs.launchpad.net/ubuntu/+s...a/+bug/1432949](https://bugs.launchpad.net/ubuntu/+s...a/+bug/1432949)
[https://bugs.freedesktop.org/show_bug.cgi?id=71789](https://bugs.freedesktop.org/show_bug.cgi?id=71789)

---

### Post by lowtech2 on 2016-02-15
> **luigiburdo said:**
> i think there are some problems with codecs  ... im facing really big issues on X5000 with vlc ... there crash after  loadingVLC works really well on the PowerBook5,8 - except for the MPEG2 problem, but there is a workaround.
Created a bug report for the mpeg-2 issue at [https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/1544936](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/1544936)


Developer response was:
> In that log, MPEG2 Video is decoded  by your GPU, so there is very little to nothing that VLC can do about  the performance.

 Quite possibly your drivers are broken
My workaround with VLC settings:
> Found a solution/workaround by changing Setting - Input/Codec from Decode=Auto to Decode=VA-API

VLC 2.2.2 can playback my test video clips encoded with

- **h.265** and a resolution of 640x360 @ 25fps
- **h.264, theora, vp8** and a resolution of 960x540 @ 25fps
- **mpeg4 (XviD)** and a resolution of 1280x720 @ 25fps
- **mpeg2 (DVD)** and a resolution of 1280x720 @ 25fps

with a cpu load of ~80% on the PowerBook5,8.

---

### Post by lowtech2 on 2016-02-15
> **ernsteiswuerfel said:**
> Regarding 3D this may be the related bugs (and a workaround):
[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1432949](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1432949)
[https://bugs.freedesktop.org/show_bug.cgi?id=71789](https://bugs.freedesktop.org/show_bug.cgi?id=71789)

And thanks for the detailed description how you solved your driver problems! Done all that before but forgot to write down that stuff properly and then forgot about it. ;)
Yes, I noticed the 3D-bug at freedesktop.org in the meantime (comment #10 is from me). 
Is there any info, why they didn't solve this issue?

---

### Post by ernsteiswuerfel on 2016-02-15
> **lowtech2 said:**
> Yes, I noticed the 3D-bug at freedesktop.org in the meantime (comment #10 is from me). 
Is there any info, why they didn't solve this issue?

IMHO this is not considered as important enough. For the most part the developement of xf86-video-ati is done by AMD employees. The main focus is on *radeonsi*, *r600* at least gets some attention and fixes. I guess *r300* very rarely gets attention by the core developers, r300 problems on aged PPC-hardware even less. ;)

As for the VLC-problem: If you look through you Xorg.0.log you should find that MPEG2 can be decoced via xvmc on r300 hardware. Maybe this is the default setting? In theory any other driver but xvmc should work then. I will check this out on my PowerBook too.

---

### Post by este.el.paz on 2016-02-18
> **Spectre660 said:**
> Sam460ex

@Spectre660:

My background/desktop image looks just like yours, with the blotchy transitions between color densities . . . I can't tell if that's on my end, video rendering of images, or, that's the way it looks to you as well??  Just did a large 330 package upgrade this am, still have the blotchy images . . . text rendered very crisply . . . .

e...

[Edit:  Erased the image because back in OSX the image looks much smoother, so it was/is the image rendering in 16.04 that shows all photos as blotchy . . . there is a bug report already linked in this thread.  On another front, I think someone else noticed that apport-collect wasn't "collecting" . . . I filed a bug report . . . and I'm holding my breath until there is a solution for it . . . .  : - 0
[https://bugs.launchpad.net/ubuntu-mate/+bug/1547568](https://bugs.launchpad.net/ubuntu-mate/+bug/1547568)  ]

---

### Post by kate-libby on 2016-02-20
I install the Daily-Build of 16.04.

I boot 16.04 in Live Session and it works fine. Then, i install 16.04 and get reboot. After reboot the Desktop freezes when complete loaded.

---

### Post by este.el.paz on 2016-02-20
> **kate-libby said:**
> I install the Daily-Build of 16.04.

I boot 16.04 in Live Session and it works fine. Then, i install 16.04 and get reboot. After reboot the Desktop freezes when complete loaded.

@Kate-libby:

I have a similar problem with 16.04 on my iBook, but, in the live session the GUI runs fine until I open 3 or 4 apps . . . then the GUI slows down and freezes.  It's possible that is relating to the same issue . . . I filed a bug report on Launchpad--#1542749 . . . I have it linked in another post on this thread, or, you can search google for "bug 1542749" . . . that should get you to the page.  It's hard to know if the bug reports are doing anything, but, the more people who make them the more that it shows PPC spins are still being used . . . .

In terms of your problem . . . did you use any boot params?  What machine are you installed on, specs . . . and, are you dual-booting or whole disking one system???  Those kind of questions.  In the case of my iBook I believe that in 16.04 using boot params did not get me into a live session, or, trying out the various radeonfb options did not make a difference in my problem . . . I'm just assuming that my iBook is not meeting the specs for 16.04; although another experienced linux guy said he was running 16 on a machine that had half the specs of mine?????

e...

---

### Post by kate-libby on 2016-02-21
I installed 16.04 without any boot params. No Dual-boot. It is a PB Model 5,8 with 1,67 GHz, 2GB RAM, 64GB SSD, 128MB VRAM.

---

### Post by xeno74 on 2016-02-21
ubuntu MATE 16.04 PowerPC with MATE Tweak and the openSUSE panel:

[[IMG]https://lh3.googleusercontent.com/-1ilkW6s1Dik/VseHYRoQVeI/AAAAAAAACLU/YflLhnQQiMs/w506-h380/ubuntu_MATE_16.04_PowerPC_kernel_4.5-rc4-2_openSUSE_panel.png[/IMG]](https://plus.google.com/115515624056477014971/posts/WQ4t8HFvZxY)
 
[URL="http://forum.hyperion-entertainment.biz/viewtopic.php?f=35&t=2983&p=36932#p36932"] 
N e w installation instructions for installing ubuntu MATE 16.04 PowerPC on the AmigaONE X1000[/URL]

[[IMG]https://lh3.googleusercontent.com/-B6WK9PImbZ8/VsmRbsBkR3I/AAAAAAAACMI/eQ_7_gsPoyY/w506-h378/Ubuntu_Mate_install_Sam_PowerPC.jpg[/IMG]]("https://plus.google.com/115515624056477014971/posts/S3Dt1jXSrW5")

---

### Post by luigiburdo on 2016-02-21
On quad G5 i continue have the hell certificate kernel issue...
on X5000 everything is working right

---

### Post by este.el.paz on 2016-02-21
> **kate-libby said:**
> I installed 16.04 without any boot params. No Dual-boot. It is a PB Model 5,8 with 1,67 GHz, 2GB RAM, 64GB SSD, 128MB VRAM.

@k-l:

Well, you should have plenty of computer hardware to run MATE, it's doing fine on my 1.2 GHz/2GB RAM PM 3,1 . . . but not so well on my iBook . . . with the radeon card.  What video card do you have those 128MB of VRAM on?

Have you run any update/upgrades since you did your install?

e...

---

### Post by lowtech2 on 2016-02-22
> **kate-libby said:**
> I installed 16.04 without any boot params. No Dual-boot. It is a PB Model 5,8 with 1,67 GHz, 2GB RAM, 64GB SSD, 128MB VRAM.
Got the same PowerBook and Ubuntu Mate runs nice there. But started with an older iso (alpha 2) and have dual-boot OSX as an option. After booting the installed system (without any boot parameter too) only a black screen is presented and need pressing F1 or F2 to see the desktop. Caused by some power management i2c-dev issue?! 

Look at my post earlier in this thread [http://ubuntuforums.org/showthread.php?t=2301608&p=13437477#post13437477](http://ubuntuforums.org/showthread.php?t=2301608&p=13437477#post13437477)

---

### Post by xeno74 on 2016-02-23
Hi All,

I updated ubuntu MATE 16.04 PowerPC today.

New:

[list]
[*] GCC-6
[*] libwebkit2gtk-4.0-37
[*] Firefox 44.0.2
[*] LibreOffice 5.1.0.3
[*] Mutiny (new panel layout - topmenu - mate-dock-applet)[/list]

After the update I had to copy the **r600_dri.so** to **/usr/lib/powerpc-linux-gnu/dri**.

```
sudo cp /usr/local/mesa-10.0.4/lib/dri/r600_dri.so /usr/lib/powerpc-linux-gnu/dri
```

Then I logged on again and the 3D acceleration works again.

Screenshots of ubuntu MATE 16.04 with the new panel layout Mutiny:

[[img]https://lh3.googleusercontent.com/-CquWt-1oSP0/VsyHmhPV8fI/AAAAAAAACNo/9_CKuVmfFps/w506-h380/ubuntu_MATE_16.04_PowerPC_with_Mutiny_2.png[/img]](https://plus.google.com/115515624056477014971/posts/axeCyHMbmFh) [[img]https://lh3.googleusercontent.com/-W8BITqz1FeA/Vsx3g-zjhEI/AAAAAAAACM8/H9e6aqPbYJ4/w506-h380/ubuntu_MATE_16.04_PowerPC_with_Mutiny.png[/img]](https://plus.google.com/115515624056477014971/posts/251S5PV8xNu)

Cheers,

Christian

---

### Post by xeno74 on 2016-02-24
ubuntu MATE 16.04 PowerPC on the new AmigaONE 1222 (Tabor board):&#65279;

[[IMG]https://lh3.googleusercontent.com/-WEHJ9Z102sM/Vs2SR4sMdmI/AAAAAAAACOY/OKBiaslebJw/w506-h285/Tabor_Ubuntu-Mate_16.04-2.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/7g46hx7159K")

[http://a-eon.biz/news/News_Release_A1222.pdf](http://a-eon.biz/news/News_Release_A1222.pdf)

---

### Post by ernsteiswuerfel on 2016-02-24
> **luigiburdo said:**
> On quad G5 i continue have the hell certificate kernel issue...
on X5000 everything is working right

Yep, same here. Had no luck with yesterdays iso on PM 7,3 but it worked (as usual) on PB 5,6.

---

### Post by xeno74 on 2016-02-25
[img]https://upload.wikimedia.org/wikipedia/commons/thumb/5/53/Ubuntu_MATE_logo.svg/372px-Ubuntu_MATE_logo.svg.png[/img]

Hi All,

Spectre660 has released a lot of ISOs and initrds for installing **ubuntu MATE 16.04 PowerPC** on NG Amigas.

New: 

- Auto selecting and installing the official ubuntu MATE desktop
- Installing the xorg.conf automatically
- Copying the kernel modules automatically

Downloads:

**A-EON AmigaONE X1000**: [initrd-4.1.18_ubuntu-mate_16.04-ppc64-1.gz](http://www.xenosoft.de/initrd-4.1.18_ubuntu-mate_16.04-ppc64-1.gz) (You need additionally the [stable longterm kernel 4.1.18](http://www.xenosoft.de/vmlinux-4.1.18-AmigaONE_X1000.tar.gz))

**A-EON AmigaONE X5000**: uRamdisk_Ubuntu-Mate_16.04_cyrus_net-1 (You need additionally the kernel 4.4.1. Downloads for beta testers only)

**A-EON AmigaONE A1222**: uRamdisk_Ubuntu-Mate_16.04_tabor_net-1 (You need additionally the kernel 4.1.18. Downloads for beta testers only)

**ACube Sam440ep( Flex)**: [Sam440ep_Ubuntu-Mate_16.04_Netinstall-1.iso](http://www.xenosoft.de/Sam440ep_Ubuntu-Mate_16.04_Netinstall-1.iso)

**ACube AmigaONE 500/Sam460ex( Lite)**: [Sam460ex_Ubuntu-Mate_16.04_Netinstall-1.iso](http://www.xenosoft.de/Sam460ex_Ubuntu-Mate_16.04_Netinstall-1.iso)

Many many thanks to Spectre660 for his hard work! :-)

Cheers,

Christian

---

### Post by luigiburdo on 2016-02-25
i continue have the Kernel Certificate ERROR! when will they will fix it :-( :-( today tooooooooo...
I suppose is a kernel problem plus a cdrom filesystem issue!

---

### Post by QIII on 2016-02-25
Let's at least make a passing attempt at keeping the language family-friendly.  The Forum community is populated by people of varying degrees of sensitivity to vulgarity and profanity.

Thanks.

---

### Post by ernsteiswuerfel on 2016-02-25
> **luigiburdo said:**
> i continue have the Kernel Certificate ERROR! when will they will fix it :-( :-( today tooooooooo...
I suppose is a kernel problem plus a cdrom filesystem issue!
Could also be a systemd issue. Or an issue caused by the kernel or systemd interacting with OpenFirmware data.

---

### Post by xeno74 on 2016-02-26
Hi All,

Martin Wimpress released the **Beta 1** of ubuntu MATE 16.04 yesterday.

Link: [http://ubuntu-mate.org/blog/](http://ubuntu-mate.org/blog/)

ISOs and initrds for installing ubuntu MATE 16.04 PowerPC:


[LIST]
[*] **PowerPC-based Macs and IBM-PPC (POWER5)**: [ubuntu-mate-16.04-beta1-desktop-powerpc.iso]("http://cdimage.ubuntu.com/ubuntu-mate/releases/16.04/beta-1/ubuntu-mate-16.04-beta1-desktop-powerpc.iso") 
[*] **A-EON AmigaONE X1000**: [initrd-4.1.18_ubuntu-mate_16.04-ppc64-1.gz]("http://www.xenosoft.de/initrd-4.1.18_ubuntu-mate_16.04-ppc64-1.gz") (You need additionally the stable longterm kernel 4.1.18: [vmlinux-4.1.18-AmigaONE_X1000.tar.gz]("http://www.xenosoft.de/vmlinux-4.1.18-AmigaONE_X1000.tar.gz")) 
[*] **A-EON AmigaONE X5000**: uRamdisk_Ubuntu-Mate_16.04_cyrus_net-1 (You need additionally the kernel 4.4.1. Downloads for beta testers only) 
[*] **A-EON AmigaONE A1222**: uRamdisk_Ubuntu-Mate_16.04_tabor_net-1 (You need additionally the kernel 4.1.18. Downloads for beta testers only) 
[*] **ACube Sam440ep( Flex)**: [Sam440ep_Ubuntu-Mate_16.04_Netinstall-1.iso]("http://www.xenosoft.de/Sam440ep_Ubuntu-Mate_16.04_Netinstall-1.iso") 
[*] **ACube AmigaONE 500/Sam460ex( Lite)**: [Sam460ex_Ubuntu-Mate_16.04_Netinstall-1.iso]("http://www.xenosoft.de/Sam460ex_Ubuntu-Mate_16.04_Netinstall-1.iso") 
[/LIST]


I successfully updated my ubuntu MATE 16.04 PowerPC to the Beta 1 on my AmigaONE X1000 today.

[[IMG]https://lh3.googleusercontent.com/--kZZYkBoGIA/VtAF6y4i44I/AAAAAAAACPg/tFZJbaB3NrA/w506-h380/ubuntu_MATE_16.04_beta1_PowerPC_AmigaONE_X1000.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/5eu7N5t7GVu")

**PLEASE** test it.

Many thanks in advance,

Christian

---

### Post by xeno74 on 2016-02-26
Julian has recently successfully updated ubuntu MATE 16.04 PowerPC to the Beta 1 on the Sam460ex and on the AmigaONE A1222.&#65279;

[[IMG]https://lh3.googleusercontent.com/-Poekc1fiSlc/VtApLnH9gJI/AAAAAAAACQs/fNOA84qohYY/s253-p/Tabor_Ubuntu-Mate_16.04-Beta1.png[/IMG][IMG]https://lh3.googleusercontent.com/-sIktjXc9E_4/VtApSllhR2I/AAAAAAAACQs/gWs1qLcmr1g/w252-h253-p/Sam460ex_Ubuntu-Mate_16.04-Beta1.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/jLz75t8hZyS")

---

### Post by xeno74 on 2016-02-26
I can boot a virtual Power Mac G3 beige with QEMU/KVM on my AmigaONE X1000. I successfully tested the official ubuntu MATE 16.04 Beta 1 ISO in this virtual machine.&#65279;

[[img]https://lh3.googleusercontent.com/-3tD8-iEZtt8/VtBBUZXFKbI/AAAAAAAACRQ/bCcCcrorMmM/w506-h380/ubuntu_MATE_16.04_Beta_1_PowerPC_on_a_virtual_G3_beige_PowerMac.png[/img]](https://plus.google.com/115515624056477014971/posts/iE1oRHwTNng)

---

### Post by xeno74 on 2016-02-26
The Beta 1 of ubuntu MATE 16.04 PowerPC on the AmigaONE X5000:&#65279;

[[img]https://lh3.googleusercontent.com/-m4V2jRoZi48/VtC1f3XoFxI/AAAAAAAACR4/6vgPuk8k4Zo/w506-h285/matex5000.png[/img]](https://plus.google.com/115515624056477014971/posts/45oyLqHEpFR)

**PLEASE** test the Beta 1 of ubuntu MATE 16.04 PowerPC.

---

### Post by luigiburdo on 2016-02-26
> **ernsteiswuerfel said:**
> Could also be a systemd issue. Or an issue caused by the kernel or systemd interacting with OpenFirmware data.

Este, the same kernel problem come with alternate installer ....
im lost.

---

### Post by xeno74 on 2016-02-27
Spectre660 updated the ubuntu MATE 16.04 PowerPC X1000 ramdisk for the 4.4.3 kernel as well as the 4.1.18 Kernel.

Download: [initrd-4.1.18_ubuntu-mate_16.04-ppc64-2.gz](http://www.xenosoft.de/initrd-4.1.18_ubuntu-mate_16.04-ppc64-2.gz) (I propose to download it with a right click on the link and then with the menu point "Save target as" or something like this.)

---

### Post by abtabt on 2016-02-27
IMAC G4 800 Mhz Iglob working with 16.04 Beta 1 live   (  some tweaks needed )

---

### Post by este.el.paz on 2016-02-27
Found a problem with optical drive now seemingly ejecting all DVDs . . . trying to "blank" a DVD+ and latest dist-upgrade on 16.04 will not hold the DVD or spin it such that Brasero can "recognize it . . . .  Anyone else had this issue??  Took a couple hours to download the daily, went for the linix side of the PM 3,1 so that I could zsync the next Beta . . . and, now, no optical drive function???  : - )))

I'll post back with the bug report number . . . .
[Edit2: Yep, switched back to OSX side, put the DVD into op drive . . . and used DU to erase it . . . seems like a problem in MATE vis optical drive.]
e...

[URL="https://bugs.launchpad.net/ubuntu-mate/+bug/1550842"]https://bugs.launchpad.net/ubuntu-mate/+bug/1550842


[/URL]

---

### Post by xeno74 on 2016-02-28
ubuntu MATE 16.04 PowerPC with a 1080p video:

[[IMG]https://lh3.googleusercontent.com/-EFep4Urv9U4/VtMsF_gMTFI/AAAAAAAACSg/E7Y0JTAm_II/w506-h285/ubuntu_MATE_16.04_PowerPC_with_a_1080p_video.jpg[/IMG]]("https://plus.google.com/115515624056477014971/posts/UuNedxfAhCm")

---

### Post by xeno74 on 2016-02-29
Today, I tested QEMU/KVM with the [RC6 of kernel 4.5](http://www.xenosoft.de/vmlinux-4.5-rc6-AmigaONE_X1000.tar.gz) on ubuntu MATE 16.04 PowerPC. I successfully booted the Beta 1 of Lubuntu 16.04 PowerPC on a virtual Power Mac G3.&#65279;

[[img]https://lh3.googleusercontent.com/-yXdRzniCtG4/VtQKLcyx6vI/AAAAAAAACTc/rp1hUktDvVk/w506-h380/ubuntu_MATE_16.04_PPC_with_Lubuntu_16.04_PPC_in_a_virtual_PowerMac_G3_QEMU_KVM_machine.png[/img]](https://plus.google.com/115515624056477014971/posts/Z9iEQce37LX)

---

### Post by Lastic on 2016-03-01
After following Ubuntu Mate from the start, I wanted to report on the progress that was made and for which I wish to thank the many developers.

Up to the 16.04 Beta 1 , I always had to add boot parameters , had to choose between HW acceleration or not , now everything works out of the box except the usuals tweaks 
( i2c-dev, pmu_battery,snd-aoa-i2sbus , b43 fw ) .

My specs : Powerbook G4 12 inch , 1.5 Ghz with Nvidia Geforce FX Go5200, 1.25 Gb RAM and a SSD. (Powerbook 6,8)

[ATTACH=CONFIG]267591[/ATTACH]

Only 2 cherries missing on top of the cake : screen brightness control ( pbbuttonsd (pommed) + nv no luck ) + suspend-to-(ram/disk)

---

### Post by ernsteiswuerfel on 2016-03-01
Out of curiosity I also tried Lubuntu powerpc on my PowerMac7,3. But as expected here too bug 1541151 prevents booting.

But, in contratry to Ubuntu MATE the qa-tracker for the beta is still open to report issues:
[http://iso.qa.ubuntu.com/qatracker/milestones/351/builds/113685/testcases/1303/results](http://iso.qa.ubuntu.com/qatracker/milestones/351/builds/113685/testcases/1303/results)

---

### Post by xeno74 on 2016-03-03
For NG Amigas: There is an issue with the downloaded components while the  installation of ubuntu MATE with the initrds. Spectre660 will release  some installation ISOs. These ISOs will have the correct working  components for installing ubuntu MATE 16.04.

---

### Post by este.el.paz on 2016-03-03
Anyone else with ATI Rage 128 card having problems with blotchy graphics for images?

[https://bugs.launchpad.net/ubuntu-mate/+bug/1541082](https://bugs.launchpad.net/ubuntu-mate/+bug/1541082)

Anyone else with Powermac having issues with DVDs not mounting on desktop, and optical drive tray opening after inserting DVD and trying to get it to mount, etc?

[https://bugs.launchpad.net/ubuntu-mate/+bug/1550842](https://bugs.launchpad.net/ubuntu-mate/+bug/1550842)

There are others, but, these seem to have gotten some replies from dev-like people . . . if you have that issue, please add your name to the Bugz.

---

### Post by Casey_C on 2016-03-04
Not necessarily about testing, but very relevant to the PPC community, has anyone heard of the Talos workstation project by Raptor Engineering?  It would be exciting to welcome a new high-performance system into the PPC community!

---

### Post by bug67 on 2016-03-04
So, I finally got 16.04 MATE to install on my 15" PowerBook G4 1.67 GHz, 2 GB RAM and Radeon 9700GPU.  I had to run this to get it to boot to the live CD:
```
live video=offb:off video=radeonfb:off video=1280x854-32
```

However, upon reboot, I am confronted with a locked up black screen with a white cursor arrow that does nothing.  Is there something I am supposed to be a boot parameter I am supposed to be entering at yaboot?  Everything I have tried returns "no such file found."  

Admittedly, I have no idea what I'm doing.  I'd just like to have a functional OS at this point.  OS X is long gone on this machine.

---

### Post by xeno74 on 2016-03-05
[img]http://www.omgubuntu.co.uk/wp-content/uploads/2015/10/flavors.jpg[/img]

Hi All,

Spectre660 has recently released an img for a USB pen drive with a Ubuntu 16.04 base installation. This img is for all AmigaONEs. ;-)

Download: [Amigaone_Ubuntu_16.04-Base-1.img.7z](http://www.xenosoft.de/Amigaone_Ubuntu_16.04-Base-1.img.7z)

@Spectre660: Many thanks for this img. It's really small.

I will try it out today. First, I will install the Lubuntu desktop. After that I will try to install the ubuntu MATE desktop. I am looking forward to my installation party.

Have a nice day. :-)

Cheers,

Christian

---

### Post by xeno74 on 2016-03-05
The Beta 1 of Lubuntu 16.04 PowerPC&#65279;

[[IMG]https://lh3.googleusercontent.com/-msymjV2-Zwo/Vttjm6lL18I/AAAAAAAACW8/PBrnf3GX4rM/w506-h380/2016-03-05-184920_1600x1200_scrot.png[/IMG]](https://plus.google.com/115515624056477014971/posts/dGpnvmsja7o)

---

### Post by xeno74 on 2016-03-06
Lubuntu 16.04 PowerPC in action with the new stable longterm kernel 4.1.19  :-)&#65279;

[[IMG]https://lh3.googleusercontent.com/-DRRUWPunpZg/Vtv20LHgFpI/AAAAAAAACYk/j3fU7jb2StE/w506-h380/2016-03-06-051817_1600x1200_scrot.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/ZNFFz9VS7Fo")

---

### Post by ernsteiswuerfel on 2016-03-06
> **bug67 said:**
> So, I finally got 16.04 MATE to install on my 15" PowerBook G4 1.67 GHz, 2 GB RAM and Radeon 9700GPU.  I had to run this to get it to boot to the live CD:
```
live video=offb:off video=radeonfb:off video=1280x854-32
```

However, upon reboot, I am confronted with a locked up black screen with a white cursor arrow that does nothing.  Is there something I am supposed to be a boot parameter I am supposed to be entering at yaboot?  Everything I have tried returns "no such file found."  

Admittedly, I have no idea what I'm doing.  I'd just like to have a functional OS at this point.  OS X is long gone on this machine.
If you want to boot with your kernel parameters every time, you need to edit your /etc/yaboot.conf and add these parameters. In your case this would be something like this:

```

[...]
image=/vmlinux
    label=Linux
    read-only
    initrd=/initrd.img
    append="video=offb:off video=radeonfb:off video=1280x854-32 quiet splash"
[...]
```

And don't forget to write your yaboot.conf back to disk with **sudo ybin -v**.

---

### Post by eastone on 2016-03-06
Half success :) on PM G4 MDD 1.5GHz, 2GB RAM, Ati9650 256MB VRAM
-sound works
-wifi works
-native resolutions (after weird  problems) works
[https://plus.google.com/u/0/113510686010520773635/posts/3s23Qy9GEZv?pid=6259049367541659026&oid=113510686010520773635](https://plus.google.com/u/0/113510686010520773635/posts/3s23Qy9GEZv?pid=6259049367541659026&oid=113510686010520773635)
The biggest problem is very looong startup about 2min 30sec when load kernel and ramdisk...
And ofcourse no 2/3D

---

### Post by bug67 on 2016-03-06
> **ernsteiswuerfel said:**
> If you want to boot with your kernel parameters every time, you need to edit your /etc/yaboot.conf and add these parameters. In your case this would be something like this:

```

[...]
image=/vmlinux
    label=Linux
    read-only
    initrd=/initrd.img
    append="video=offb:off video=radeonfb:off video=1280x854-32 quiet splash"
[...]
```

And don't forget to write your yaboot.conf back to disk with **sudo ybin -v**.

Thanks.  I figured it out by pouring over the PPC FAQs and known issues.  You beat me to it though.  What wound up working was this:
```
image=/vmlinux
    label=Linux
    read-only
    initrd=/initrd.img
    append="Linux radeon.modeset=1 video=offb:off video=radeonfb:off video=1280x854-32 radeon.agpmode=-1"
```
And then, sudo ybin -v

Now, sound.  I have none.  The quest continues...

---

### Post by xeno74 on 2016-03-07
**Firefox 45** is available for Ubuntu 16.04.

[url=https://plus.google.com/115515624056477014971/posts/U9irraS2GP5]
[img]https://lh3.googleusercontent.com/-uO6s7naIx0Q/VtxiUP4CxoI/AAAAAAAACZM/_LJLU2YV288/w506-h380/Firefox_45_ubuntu_MATE_16.04_PowerPC.png[/img][/url]

Firefox build status: [launchpad.net](https://launchpad.net/ubuntu/+source/firefox/)

---

### Post by lowtech2 on 2016-03-07
> **bug67 said:**
> Now, sound.  I have none.  The quest continues...

Did you add the line **snd-aoa-i2sbus** to /etc/modules and check your mixer volume settings?

---

### Post by bug67 on 2016-03-07
> **lowtech2 said:**
> Did you add the line **snd-aoa-i2sbus** to /etc/modules and check your mixer volume settings?

Yes.  I got it sorted.  Thanks!  :)

Amazing that I have a fully functional computer again.  It seems a little resource heavy.  
for example, it will not run the ProjectM visualizer via Clementine at all.

Oh, and I am REALLY missing Chromium.

---

### Post by bug67 on 2016-03-09
When I run glxgears in terminal, I get this in return:
```
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: r300
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
Error: couldn't get an RGB, Double-buffered visual
```
I have the following set as a yaboot startup parameter:
```
image=/vmlinux
    label=Linux
    read-only
    initrd=/initrd.img
    append="Linux radeon.modeset=1 video=offb:off video=radeonfb:off video=1280x854-32 radeon.agpmode=-1"
```
Any ideas what I need to do to get everything working right?  Thanks in advance.

---

### Post by lowtech2 on 2016-03-09
> **bug67 said:**
> When I run glxgears in terminal, I get this in return:
```
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: r300
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
Error: couldn't get an RGB, Double-buffered visual
```
I have the following set as a yaboot startup parameter:
```
image=/vmlinux
    label=Linux
    read-only
    initrd=/initrd.img
    append="Linux radeon.modeset=1 video=offb:off video=radeonfb:off video=1280x854-32 radeon.agpmode=-1"
```
Any ideas what I need to do to get everything working right?  Thanks in advance.

Look at post [#123 ]("http://ubuntuforums.org/showthread.php?t=2301608&p=13439757#post13439757")and [#127]("http://ubuntuforums.org/showthread.php?t=2301608&p=13440308#post13440308").

---

### Post by bug67 on 2016-03-09
> **lowtech2 said:**
> Look at post [#123 ]("http://ubuntuforums.org/showthread.php?t=2301608&p=13439757#post13439757")and [#127]("http://ubuntuforums.org/showthread.php?t=2301608&p=13440308#post13440308").

Basically, what this is telling me is, is the workaround is to change the default resolution in xorg.conf to 16.  However, when I look in /etc/X11/, there is no xorg.conf to edit.  So...   ???

I don't understand what I'm supposed to do to change the default depth to 16.

---

### Post by xeno74 on 2016-03-09
ubuntu MATE 16.04 PowerPC booted from a USB thumb drive&#65279;:

[[IMG]https://lh3.googleusercontent.com/-9A5Vmy2PCKs/VuCCwwhSxVI/AAAAAAAACZ4/9qS1YdWfE9c/w506-h285/Sam460ex-USB_Thumbdrive.png[/IMG]](https://plus.google.com/115515624056477014971/posts/JmhNogJ7o2c)

---

### Post by rican-linux on 2016-03-10
add this entry 

```
radeon.agpmode=-1
```

---

### Post by eastone on 2016-03-11
Finally :)
[https://plus.google.com/113510686010520773635/posts/JtdLSh8wv5u?utm_source=embedded&utm_medium=googleabout&utm_campaign=link&pid=6260836508992863842&oid=113510686010520773635](https://plus.google.com/113510686010520773635/posts/JtdLSh8wv5u?utm_source=embedded&utm_medium=googleabout&utm_campaign=link&pid=6260836508992863842&oid=113510686010520773635)

---

### Post by bug67 on 2016-03-11
Success!  Thanks for everyone's patience.  Got it working by opening a terminal and:

```
sudo nano /etc/X11/xorg.conf
```
Then:
```
Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 16
EndSection
```
Then saved and closed:  save (ctrl+o) exit (ctrl+x)

[IMG]https://bug67.smugmug.com/Computers/Linux/Linux-Misc/i-9n9kVVS/0/L/Screenshot%20at%202016-03-11%2013%3A09%3A45-L.png[/IMG]

---

### Post by xeno74 on 2016-03-12
ubuntu MATE 16.04 PowerPC booted from a USB flash drive with the AmigaONE X1000&#65279;:

[[IMG]https://lh3.googleusercontent.com/-J2BKh8u7yoY/VuRfLShusBI/AAAAAAAACag/pf90GUitcj8/w506-h380/ubuntu_MATE_16.04_PowerPC_X1000_booted_from_USB_flash_drive.png[/IMG]](https://plus.google.com/115515624056477014971/posts/4SjqkiVuc4N)

ubuntu MATE 16.04 PowerPC booted from a USB flash drive with the AmigaONE A1222 (Tabor board)&#65279;:

[[IMG]https://lh3.googleusercontent.com/-AVbm66qYT-M/VuSUne7_CcI/AAAAAAAACbM/TlzawLQ2NSg/w506-h380/ubuntu_MATE_16.04_PowerPC_A1222_booted_from_USB_flash_drive.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/2RHc8rgrRvZ")

---

### Post by xeno74 on 2016-03-14
Lubuntu 16.04 PowerPC with the kernel 4.5 final. :-)&#65279;

[[IMG]https://lh3.googleusercontent.com/-wPfBV8tknoc/VuZ_d3SIa_I/AAAAAAAACb0/a8NAnL-y3HI/w506-h380/Lubuntu_16.04_PowerPC_with_kernel_4.5_final.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/2KoSXYFQ4un")

---

### Post by este.el.paz on 2016-03-17
Did a major dist-upgrade today, about 200-300MB of "stuff" . . . generally OK; a few minutes ago I was rifling through the Applications list opening things to see what they were, and Synapse crashed on opening . . . 4 times . . . .  Seems like the "apport collect" is now via GUI, a bug report has been filed . . . for some reason marked as "private" . . . .  If you have the same experience and want to add yr name and can't . . . let me know. > [h=1]synapse crashed with SIGSEGV in gdk_x11_window_get_xid()[/h]

e...

---

### Post by xeno74 on 2016-03-18
ubuntu MATE 16.04 PowerPC with the Cupertino panel layout&#65279;:

[[IMG]https://lh3.googleusercontent.com/-7VJPRswEhIw/VuwOMGSEPsI/AAAAAAAACfM/YojSRnVx_sc/w506-h380/ubuntu_MATE_16.04_PowerPC_with_the_Cupertino_panel_layout.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/g2dmonzwzvT")

---

### Post by xeno74 on 2016-03-22
[img]http://isebaro.com/viewtube/include/images/viewtube.png[/img]

[size=6]YouTube videos in HD with ViewTube[/size]

Installation instructions for ubuntu MATE 16.04 PowerPC

[list=1]
[*] Install VLC and the VLC browser plugin with the following command:
```
sudo apt-get install browser-plugin-vlc
```
[*] Start Firefox and install the add-on [Greasemonkey](https://addons.mozilla.org/en-US/firefox/addon/greasemonkey/)
[*] Restart Firefox
[*] After that, add the [ViewTube script](http://isebaro.com/viewtube/?ln=en) to [Greasemonkey](https://addons.mozilla.org/en-US/firefox/addon/greasemonkey/)[/list]

[[img]https://lh3.googleusercontent.com/-Aw7eXCDcnN4/VvEbkm95ctI/AAAAAAAACjA/x00b8Y6P9D44C7qU3RQGeIx_B0BPR2adg/w506-h380/YouTube_HD_with_ViewTube_PowerPC.png[/img]](https://plus.google.com/115515624056477014971/posts/M1yy6nchrfC)

---

### Post by lowtech2 on 2016-03-22
Following Problem
> **lowtech2 said:**
> [    2.780433] Problem loading in-kernel X.509 certificate (-74)
is now gone with latest update to kernel 4.4.0-**15**-powerpc-smp

---

### Post by ernsteiswuerfel on 2016-03-22
Yep, I can confirm this. ^^ Now able to boot with my PowerMac7,3. Yay! :-)

---

### Post by xeno74 on 2016-03-26
**[SIZE=5]ubuntu MATE 16.04 Final Beta PowerPC is out![/SIZE]**

New: [ubuntu-mate.org]("https://ubuntu-mate.org/blog/ubuntu-mate-xenial-beta2/")

Download for PowerPC-based Macs and IBM-PPC (POWER5): [ubuntu-mate-16.04-beta2-desktop-powerpc.iso]("http://cdimage.ubuntu.com/ubuntu-mate/releases/16.04/beta-2/ubuntu-mate-16.04-beta2-desktop-powerpc.iso")

Julian has recently released a new image of the final beta for the AmigaONE X1000 with Radeon HD Northern Islands graphics cards.

Download: [Ubuntu-Mate_16.04-X1000-NI-2.img.7z]("https://www.dropbox.com/s/vo8d1plwhh87wrp/Ubuntu-Mate_16.04-X1000-NI-2.img.7z?dl=0")

Screenshot of ubuntu MATE 16.04 PowerPC (final beta):

[[IMG]https://lh3.googleusercontent.com/-due1sxNTyd4/VvV_Jv1MedI/AAAAAAAAClQ/FOIGyAlzYgY/w506-h380/ubuntu_MATE_16.04_beta2_PowerPC.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/KFodBSbnj9S")

**PLEASE** test the final beta.

---

### Post by eastone on 2016-03-26
How to get mouse scrolling in Qupzilla? I can use auto scroll plugin but that is not so elegance for me ;)

---

### Post by ernsteiswuerfel on 2016-03-26
Anyone got a Radeon X800 working?

I got a Mac flashed one, the open firmware prompt works. Using *live-nosplash* I can see the boot process running. Unfortunately when the desktop should appear I only get a garbled screen. So far I tried *video=ofonly radeon.agpmode=-1* and *video=offb:off radeon.agpmode=-1* as boot parameters but had no success. It's an AGP card running in a PowerMac 7,3.

---

### Post by xeno74 on 2016-03-27
Hi All,

I successfully tested the ubuntu MATE 16.04 Beta2 PowerPC live DVD in a virtual PR KVM QEMU 2.5 machine. It boots and works without any problems.

[[IMG]https://lh3.googleusercontent.com/-NZlF_wmRoqQ/Vvczc4AbpyI/AAAAAAAACl4/fMh9wXLqNPMLy1GcPhWk_B_U8acbR2Z7A/w506-h380/ubuntu_MATE_16.04_beta2_PowerPC_QEMU_PR_KVM.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/7NHQG2cXzjQ")

Cheers,

Christian&#65279;

---

### Post by xeno74 on 2016-03-27
Important information from the Lubuntu team:

> 
Walter Lapchynski wrote:

We didn't have any formal tests being reported on the ISO tracker for the all the ppc images with the final version of the beta2 milestone, but we decided to pass it. since you seem to be so active testing after the fact, why don't you become a tester ahead of time? we could really use the help. at the very least with the final version. i won't be so willing to give it the thumbs up if formal tests aren't done during our last push.


Please test Lubuntu 16.04 PowerPC. I successfully tested the beta2 of Lubuntu 16.04 PowerPC with the RC1 of the kernel 4.6 today.

[[IMG]https://lh3.googleusercontent.com/-0LFdgzaPXl4/VvfJPfAEunI/AAAAAAAACmk/UlvjBxCn-FQ9XZhldKVVF3fBjO-7UyjsQ/w506-h380/Lubuntu_16.04_beta2_PowerPC.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/PT2BWWbhjYf")

---

### Post by luigiburdo on 2016-03-28
yes it is booting on my Quad G5 finally.
but the worst xorg bug with double graphic cards still there... 
this bug effected all the PPC world i think because it is in the X5000 too.

What i discovered :
if i set radeon.modeset=0 nouveau.modeset=1
xorg turn on the radeon driver and turn off the nouveau.... 
but because the radeon driver is off by the kernel the result is the black screen.

same is if i set radeon.modeset=1 nouveau.modeset=0

setting the two boards as 1 .... i have te fbdev working on radeon (?) but xorg dont find no video board.
if i set the two as 0 nothing woking but xorg --configure set the new xorg with the two video board.... 

This bug was present since 15.0 of (X) (L) (mate)ubuntu  ... and now one had been fixed it ...

---

### Post by xeno74 on 2016-03-30
A screenshot of the beta2 of ubuntu MATE 16.04 PowerPC with the RC1 of kernel 4.6 on Luigi's AmigaONE X5000.

[[IMG]https://lh3.googleusercontent.com/-rZjpM-hVMug/VvjukiTG5lI/AAAAAAAAAW4/tn3n8_coabwmG0ijnSTCSSpUGhC2YYNyg/w506-h285/Screenshot%2Bat%2B2016-03-28%2B10%253A41%253A49.png[/IMG]]("https://plus.google.com/+LuigiBurdo/posts/R9Udy5Et6vf")

---

### Post by eastone on 2016-03-30
Sweet nothing ;) on my G4 with Lubuntu 16.04
[http://youtu.be/3TQl6yDBml8](http://youtu.be/3TQl6yDBml8)

---

### Post by xeno74 on 2016-03-31
> **eastone said:**
> Sweet nothing ;) on my G4 with Lubuntu 16.04
[http://youtu.be/3TQl6yDBml8](http://youtu.be/3TQl6yDBml8)

Thank you very much for this video! :-)

@All

I successfully tested [Julian's latest image of ubuntu MATE 16.04 final beta PowerPC for the AmigaONE X1000 with Radeon HD Northern Islands graphics cards](https://www.dropbox.com/s/vo8d1plwhh87wrp/Ubuntu-Mate_16.04-X1000-NI-2.img.7z?dl=0) today.

I was able to boot ubuntu MATE 16.04 final beta PowerPC with the [kernel 4.6-rc1](http://www.xenosoft.de/vmlinux-4.6-rc1-AmigaONE_X1000.tar.gz) from my 64GB USB flash drive. It works fantastic with my AMD Radeon HD6870.

Screenshot:

[[img]https://lh3.googleusercontent.com/-TFpsaF5-9zU/Vv0FGA3qq5I/AAAAAAAACn0/tdIO07diaJw4clx24RJVxcpjDO8tJy5Ew/w506-h380/ubuntu_MATE_16.04_beta2_PowerPC_booted_from_a_USB_flash_drive.png[/img]](https://plus.google.com/115515624056477014971/posts/Hrr6AE1Jyht)

Please test Julian's images.

---

### Post by xeno74 on 2016-03-31
Hi All,

Today I updated my Lubuntu 16.04 PowerPC on my USB flash drive and after that I changed this installation to **xubuntu 16.04 PowerPC** with the following commands:

[LIST=1]
[*] ```
sudo su
```

[*] ```
apt-get update
```

[*] ```
apt-get upgrade
```

[*] ```
apt-get install xubuntu-desktop
```

[*] There is a problem with the brltty package. The configuration doesn't work. I had to remove the package brltty.

```
apt-get remove brltty
```
[/LIST]

After a new login I was surprised. This is really a nice desktop.

[[IMG]https://lh3.googleusercontent.com/-qjySar_TcIs/Vv1CVhb6V-I/AAAAAAAACoE/EU6sQ0f73oE5pKdNcF_q7vlPEKl8Lbdfw/w506-h380/xubuntu_16.04_PowerPC.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/2Mb9fp71YT9")

Cheers,

Christian

---

### Post by xeno74 on 2016-04-01
Dhewm 3 1.4.0.1304 linux-ppc Nov 22 2015 05:14:33 using SDL v2.0.4 on ubuntu MATE 16.04 PowerPC with the unofficial Mesa 10.0.4:

[[img]https://lh3.googleusercontent.com/-zld4DMdZXzw/Vv4-g-p38mI/AAAAAAAACp0/PvUnmnEsZmQCeQCkKAMZd71kqWP4lhr7w/w506-h380/dhewm3_on_ubuntu_MATE_16.04_PowerPC.png[/img]](https://plus.google.com/115515624056477014971/posts/F491L7b7LFh)

---

### Post by xeno74 on 2016-04-03
New ubuntu MATE system info:

[IMG]https://lh5.googleusercontent.com/-lzVo2ygWTZo/VwFwoj0EzXI/AAAAAAAACqc/KZLtNYovc0kB7ZtyO3SBqoCcshMCVgl9w/w1009-h632-no/ubuntu_MATE_16.04_PowerPC_with_kernel_4.6-rc2.png[/IMG]

---

### Post by ernsteiswuerfel on 2016-04-12
The good thing. :)

[ATTACH=CONFIG]268352[/ATTACH]

---

### Post by ernsteiswuerfel on 2016-04-12
I was hoping mesa 11.2 will resolve the "r300 Mesa driver not loading with KMS enabled"- issue too but this was unfortunately not the case. Still 16bit Xorg only.

The people affected may report this in the following bugs to get some attention:
[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1432949](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1432949)
[https://bugs.freedesktop.org/show_bug.cgi?id=71789](https://bugs.freedesktop.org/show_bug.cgi?id=71789)

---

### Post by luigiburdo on 2016-04-13
Try to build your self the mesa from lastest 11.2 git , i do it on X5000 and this fix the mesa distro bug.
Plus: the lastest 11.2 rc4 fix many wrong color issue on powerpc

---

### Post by ernsteiswuerfel on 2016-04-14
> **luigiburdo said:**
> Try to build your self the mesa from lastest 11.2 git , i do it on X5000 and this fix the mesa distro bug.
Plus: the lastest 11.2 rc4 fix many wrong color issue on powerpc
Good to hear! But I will wait until it's in the next point release of 11.2. Too lazy to build it from git. ;)

---

### Post by este.el.paz on 2016-04-14
[https://bugs.launchpad.net/ubuntu-mate/+bug/1570474](https://bugs.launchpad.net/ubuntu-mate/+bug/1570474)

Bug report filed to report the problem of "home" and "desktop" folders failing to open from dropdown "Places" menu--instead Gdebi package installer opens with an error saying "file may be corrupted or you don't have permission to open."

However, "home" folder opens from desktop icon and "computer" opens from Places menu . . . U-MATE 16.04 PPC with latest updates as of today.

e...

PS: Haven't been getting the notifications on the posts from this thread lately . . . .

---

### Post by Tim_Brendel on 2016-04-14
Hello everyone. I need some help and I am hoping I can find it here. I just received a very nice G5 PowerPC that I want to put Ubuntu Mate on but I am having the hardest time with it. I am no stranger to Linux but I am indeed new to working with PowerPC hardware. I tried booting 16.04 LTS just by hitting Enter and no luck. Then I tried the recommended approach of live video=ofonly. No luck with either of those.... All I get is a solid black screen. 

I started digging and found a bunch of other parameters to pass at boot and got mixed results which I will share below. I'm almost positive my issue is related to my video card which a Radeon X1900 (RV570 / RV80). Problem is, I couldn't any info specifically stating how to boot and install newer distros with this video card.

Mac G5 (dual PPC 2.0GHz)
16GB RAM
500GB SATA HDD
ATI Radeon X1900 video card

If pass this parameter at boot "live video=offb:off video=radeonfb:off video=noueaufb:off radeon.modset=1 nouveau.modeset=0" I get the this

[IMG]http://i.imgur.com/qkFlFq9.jpg[/IMG]



At the recommendation of another post, if I pass only this parameter at boot "radeon.modeset=0" It boots and I get this hot mess:

[IMG]http://i.imgur.com/uvrDkfb.jpg[/IMG]



Please help.

Thanks!

---

### Post by ernsteiswuerfel on 2016-04-15
@Tim_Brendel:

Try "radeon.agpmode=-1" as boot parameter. Gets my machines to the desktop without freezing. The only machine not needing this is my PowerBook 5,8.

---

### Post by Tim_Brendel on 2016-04-15
That did not work for me.... unless I did it wrong. Here's what I typed, minus the quotations "live radeon.agpmode=-1"

---

### Post by eastone on 2016-04-16
@Tim_Brendel
Unfortunately, you're not the only one with unsupported hardware :(

---

### Post by este.el.paz on 2016-04-16
> **Tim_Brendel said:**
> That did not work for me.... unless I did it wrong. Here's what I typed, minus the quotations "live radeon.agpmode=-1"

@Tim:

A few extra words might get you there, on my iBook with radeon driver, to boot the system "Linux video=ofonly radeon.agpmode=-1"  [minus the quotes].  To add it to Yaboot.conf file just the "video=ofonly radeon.agpmode=-1" as the "Linux" part is auto-filling in Yaboot . . . follow the instruction that "ernstei" provided on editing the Yaboot.config file . . . .

e...

---

### Post by Tim_Brendel on 2016-04-16
> **eastone said:**
> @Tim_Brendel
Unfortunately, you're not the only one with unsupported hardware :(

Bummer. I got this free so I'm not complaining. Just gotta figure out how to get it booted


> **este.el.paz said:**
> @Tim:

A few extra words might get you there, on my iBook with radeon driver, to boot the system "Linux video=ofonly radeon.agpmode=-1"  [minus the quotes].  To add it to Yaboot.conf file just the "video=ofonly radeon.agpmode=-1" as the "Linux" part is auto-filling in Yaboot . . . follow the instruction that "ernstei" provided on editing the Yaboot.config file . . . .

e...


I'll try that. I'm booting the Live disk though so I'll have do "Live video=ofonly radeon.agpmode=-1" If I ever get it booted and installed I'll be sure to add that to the Yaboot.conf.

Thank you all for your help!

---

### Post by Tim_Brendel on 2016-04-16
That string didn't work for me. I also tried the one here:[http://ricanlinux.blogspot.com/2015/03/ubuntu-mate-on-my-ibook-g4.html?m=1](http://ricanlinux.blogspot.com/2015/03/ubuntu-mate-on-my-ibook-g4.html?m=1). 

No luck either :( 

I read somewhere that switching from PCI16x to PCI8x may be worth a try? Thought I'd ask before moving it though.

---

### Post by luigiburdo on 2016-04-17
Guys ... it is simple :
nouveau work with the Debian wheezy 7.x no problem there
Radeon is better on ubuntu. 
but lubuntu try with a 14.04.3 dount use the last revisions because the xorg is full of issue.
Tim 
use:
```
live radeon.modeset=1 radeon.agpmode=-1 
```
if you have a console working without glitches 
switch to tty1
sudo /etc/init.d/lightdm stop
sudo Xorg -configure
sudo nano xorg.conf.new
swap "radeon" with fbdev  and save

after
sudo cp xorg.conf.new /etc/X11/xorg.conf
sudo /etc/init.d/lightdm start

and start install your linux

---

### Post by Tim_Brendel on 2016-04-17
> **luigiburdo said:**
> Guys ... it is simple :
nouveau work with the Debian wheezy 7.x no problem there
Radeon is better on ubuntu. 
but lubuntu try with a 14.04.3 dount use the last revisions because the xorg is full of issue.
Tim 
use:
```
live radeon.modeset=1 radeon.agpmode=-1 
```
if you have a console working without glitches 
switch to tty1
sudo /etc/init.d/lightdm stop
sudo Xorg -configure
sudo nano xorg.conf.new
swap "radeon" with fbdev  and save

after
sudo cp xorg.conf.new /etc/X11/xorg.conf
sudo /etc/init.d/lightdm start

and start install your linux


Thank you @luigiburdo! I tried ```
live radeon.modeset=1 radeon.agpmode=-1
``` and I got the solid black screen. I waited about 10 mins and could not any tty consoles. Just nothing. I did this with Ubuntu Mate 16.04 though, not Lubuntu 14.04. I will try that next however I am away from home for a few days so I will do that when I return on this Thursday and update the thread. Thank you.

---

### Post by ernsteiswuerfel on 2016-04-18
I opened a new bug concerning the desktop freezes when using a r300-class graphics card (eg. Radeon 9600 Pro, Mobility Radeon 9600/9700) in a PPC Mac. The freezes occur if you boot the live iso without any boot-parameters:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1571416](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1571416)

Anyone affected may join the bug. 2 of my 3 machines are affected, my PowerBook 5,8 works.

There's also a hint for boot options from Martin Wimpress in this bug. Though I didn't try them as on my machines [COLOR=#333333][FONT=monospace]radeon.agpmode=-1 is sufficient.[/FONT][/COLOR]

---

### Post by ernsteiswuerfel on 2016-04-18
@Tim_Brendel:

If you do not succeed at installing Ubuntu MATE you may try [http://www.morphos-team.net/](http://www.morphos-team.net/). It should support your Radeon X1900 properly.

---

### Post by rgs2 on 2016-04-22
I have an eMac with Radeon 9200. After update to Ubuntu Mate 16.04 the desktop is partially outside the screen (see attached picture). The command I have to put in yaboot in order to display the screen is:
"Linux radeon.modeset=1 video=radeonfb:off video=offb:off video=1024x768-32@89 radeon.agpmode=-1"
With Mate 14.04 I didn't have any problem with command "Linux video=radeonfb:1024x768-32@89"

Do you have any suggestion?


Thank you very much for your support

[IMG]http://i64.tinypic.com/25pixah.jpg[/IMG]

---

### Post by ernsteiswuerfel on 2016-04-24
Just a guess, but the "@89" in [COLOR=#000000]1024x768-32@89[/COLOR] means the VSync in Hz I suppose? Maybe you can try another value whichs suits better to your monitor? Don't know what the VESA defaults are for 1024x768..

---

### Post by rgs2 on 2016-04-25
Thank you for the suggestion. I've already fixed it using xrandr.

---

### Post by ernsteiswuerfel on 2016-05-03
"wrong colours", "no 24bpp screendepth", "no 3d-acceleration on r300 hardware", "desktop freezes on r300 hardware" bugs are being worked on by upstream devs. See:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1571416](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1571416)
[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1432949](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1432949)

I applied the patch from upstream [https://bugs.freedesktop.org/show_bug.cgi?id=71789](https://bugs.freedesktop.org/show_bug.cgi?id=71789) on mesa 11.2.1 and the r300 mesa driver is finally working on my PowerMac G5 7,3 (w. Radeon 9600 Pro, AGP) without reverting to 16bpp screendepth!

---

### Post by ptoki on 2016-05-07
Hello.
I have powerbook g4 A1010 (1GB ram, nvidia).
Ubuntu 10.04 installed and working ok. it uses nouveau video module.
I am trying to install some newer version with no luck :(

I tried mate 15.10, 16.04, lubuntu 16.04 current (todays build)
All with no success.


In most cases I get the disk to boot, it shows some message about  i2c-powermac problem and then flickers a couple of times and stays like that.
For a couple of minutes cd drive is making some noise so I guess installer works ok but does not get image on screen.

Flickering is black to black with no backlight. No cursor, no image on screen. Backlight works. I tried to do ctrl-alt-fx with no success.

Any suggestions?

I would love to give some life back to that laptop.

[edit]
A bit better after booting with:
live video=offb[IMG]http://ubuntuforums.org/images/smilies/icon_surprised.gif[/IMG]ff nouveau.modeset=0 single
I can see some text boot information and get into single user mode.
[edit2]
Booted live installer, screen is horribly garbled (pinkish whitey with stripes).

[edit3]
Installer does not allow to do anything sensible. Install ubuntu opens new window, content of that window is not visible (garbled as desktop).
Desktop properties show refresh rate as 116Hz.

---

### Post by ernsteiswuerfel on 2016-05-08
> **ptoki said:**
> Hello.
In most cases I get the disk to boot, it shows some message about  i2c-powermac problem and then flickers a couple of times and stays like that.
For a couple of minutes cd drive is making some noise so I guess installer works ok but does not get image on screen.

Flickering is black to black with no backlight. No cursor, no image on screen. Backlight works. I tried to do ctrl-alt-fx with no success.

Sounds similar to bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1571416](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1571416).

Try booting with [COLOR=#000000]nouveau.agpmode=0 [/COLOR]as boot parameter. If this works you could file a bug like the one above, noting that your PowerBook with a NVIDIA card is affected in a similar way.

If this does not work, there are other nouveau.[...] boot parameters you also may have a look at.

---

### Post by xeno74 on 2016-05-11
ubuntu MATE 16.04 LTS PowerPC with kernel 4.6-rc7. :-)

[[IMG]https://lh3.googleusercontent.com/-HQQGQVgwD2M/VzJFhZu9mnI/AAAAAAAAC6A/mGjSzT8z1csH1vpIBkyis1Caf-DDsyTsA/w506-h380/ubuntu_MATE_16.04_LTS_PowerPC_kernel_4.6-rc7.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/AXmHYNpLtw5")

---

### Post by kate-libby on 2016-05-14
Your Machine is not a "Apple Hardware". And your postings isn´t helpful for Apple Hardware / (X)(L)ubuntu Issus... [-(

> **xeno74 said:**
> ubuntu MATE 16.04 LTS PowerPC with kernel 4.6-rc7. :-)

[[IMG]https://lh3.googleusercontent.com/-HQQGQVgwD2M/VzJFhZu9mnI/AAAAAAAAC6A/mGjSzT8z1csH1vpIBkyis1Caf-DDsyTsA/w506-h380/ubuntu_MATE_16.04_LTS_PowerPC_kernel_4.6-rc7.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/AXmHYNpLtw5")

---

### Post by luigiburdo on 2016-05-15
The only Thread with PPC hardware is Apple Hardware ... I think will be best have a generic thread PowerPC Ubuntu User for apples, ibm and other powerpc hw

---

### Post by este.el.paz on 2016-05-19
> **luigiburdo said:**
> The only Thread with PPC hardware is Apple Hardware ... I think will be best have a generic thread PowerPC Ubuntu User for apples, ibm and other powerpc hw

@et al:

I haven't gotten any notifications on this thread in quite awhile, but, I'm with LB on this one, the topic "Apple users" is for the most part already a generally ignored topic in the ubuntu forums . . . and PPC is even more "niche" than "apple" . . . so any "PPC" machine issue should have no worries about posting in this sub-forum . . . just sayin' . . . there is enough "overlap" that general directions should be helpful to all users of PPC cpu.

OK, the reason I'm posting back here, running Lu 16.04 on an PPC iBook, and MATE/XFCE 16.04 on a PM ST. . . did a dist-upgrade today, so new "22" kernel and saw in the list upgrades to FF and T-bird . . . on both machines after reboot FF window frame loads . . . and then crashes . . . .  The iBook "doesn't have enough memory to report the problem" . . . and on the PM . . . apparently the error report was "corrupted" . . . .  Tried to revert to old kernel in the iBook, seemingly failed . . . shut it down; went to the PM tried there, failed . . . installed Midori to make this post.  I ran "apt-get -f install" in the iBook . . . nothing showed up.  No "comment" in the terminal during the upgrade asking any questions or reporting "problems" . . . FF is kaput!!!!

e...

[edit: bug report filed: [https://bugs.launchpad.net/ubuntu/+bug/1583849]](https://bugs.launchpad.net/ubuntu/+bug/1583849])

---

### Post by ptoki on 2016-05-20
Hello again.
After installing ubuntu from alternete iso (text mode install) I have working linux with not very usable xorg.
After booting without additional parameters it gives black screen (backlight on) after a few blinks.

After setting nouveau.modeset=0 it boots to color corrupted screen with only cursor on it.
When startx is started by hand it gives color garbled screen (pinkish-blueish) and most windows are not draw correctly.

I have tried to use nouveau.agpmode=0 with no success.

Can anyone point me how to set up proper graphics mode and generate xorg.conf?
I guess only this is neccessary to solve this issue.

---

### Post by este.el.paz on 2016-05-20
@ptoki:

Search Google for "PowerPCFAQ" and when you get there to the FAQ scroll through "How to set up your xorg,conf file" . . . it gives instructions on how to use a TTY console to configure your xorg.conf file . . . which you then may have to add some stuff.  It all depends on which video card you have . . . and then of course that would be which "driver" should be listed in the xorg.conf.

e...

---

### Post by ptoki on 2016-05-20
Thanks for info.
I have been through this already.
Now I know this:
No graphics without nouveau.modeset=0 for option in yaboot. I have tried all sorts of parameters but only this gives me any visible console.
After setting this I can boot xorg in fbdev ugly colors mode. And even then most of windows are just black.

I tried to set fbdev explicitly in xorg.conf. It does not change color depth or does not heal this pinkish-blueish colors.

I even compiled nv driver (with success) but it just locks the machine with black screen and no possibility to kill the xorg.

here is my dmesg: [http://pastebin.com/4YuemhNn](http://pastebin.com/4YuemhNn)
my xorg.conf [http://pastebin.com/QmA673z6](http://pastebin.com/QmA673z6)

and some other files attached to this post.

Xorg.txt is the Xorg log.

I am a bit confused:
Since nouveau.modeset=0 disables nouveau ability to set mode and fbdev does not change mode to anything else than its failsafe 8bit (the one which is pinkish-blueish) then how to solve this issue.

I dont think that my config is too fancy. Its powerbook g4 with nvidia nv17m Geforce 440 go 64MB.
It must be something simple. :)
I have tried all previous ubuntu and lubuntu install isos with the same result.

---

### Post by ptoki on 2016-05-21
After booting it with static IP and loading ssh-server I am able to see the logs.
here is dmesg: [http://pastebin.com/5LRZFnsM](http://pastebin.com/5LRZFnsM)
And here is xorg.log [http://pastebin.com/vVMHJkcs](http://pastebin.com/vVMHJkcs)

It looks ok to me but does not work. I have black screen.

---

### Post by rsavage on 2016-05-21
Phantom output?

---

### Post by ptoki on 2016-05-21
@rsavage, What do you mean?
I have nothing else connected to this laptop.
It worked before with yellowdog and ubuntu 10.04.
Since ubuntu 11 it does not work, all distributions after 10.04 behave in the same manner.

I did launched some xnest and remote X sessions to do some stuff on this laptop. It works ok but no image on screen.

I am puzzled to the limit with that :)

---

### Post by rsavage on 2016-05-21
> **ptoki said:**
> 
I have nothing else connected to this laptop.
Yeah, but your computer thinks you do.  A phantom output.  It's in the FAQ, but the gentoo and arch nouveau pages have stuff on it too.

---

### Post by ernsteiswuerfel on 2016-05-22
> **ptoki said:**
> 
here is my dmesg: [http://pastebin.com/4YuemhNn](http://pastebin.com/4YuemhNn)
my xorg.conf [http://pastebin.com/QmA673z6](http://pastebin.com/QmA673z6)

and some other files attached to this post.

Xorg.txt is the Xorg log.

I am a bit confused:
Since nouveau.modeset=0 disables nouveau ability to set mode and fbdev does not change mode to anything else than its failsafe 8bit (the one which is pinkish-blueish) then how to solve this issue.

I dont think that my config is too fancy. Its powerbook g4 with nvidia nv17m Geforce 440 go 64MB.
It must be something simple. :)
I have tried all previous ubuntu and lubuntu install isos with the same result.

Maybe this is of some help:
[https://wiki.ubuntu.com/X/Quirks](https://wiki.ubuntu.com/X/Quirks)
[https://wiki.ubuntu.com/X/Troubleshooting](https://wiki.ubuntu.com/X/Troubleshooting)

But sounds like you should file a bug at [https://bugs.launchpad.net/](https://bugs.launchpad.net/) with "ubuntu-bug xorg":
[https://help.ubuntu.com/community/ReportingBugs#How_to_report_bugs](https://help.ubuntu.com/community/ReportingBugs#How_to_report_bugs)

---

### Post by ptoki on 2016-05-22
Hello again :)
Following this suggestion: [http://gentoo-en.vfose.ru/wiki/Nouveau#Phantom_and_unpopulated_output_connector_issues](http://gentoo-en.vfose.ru/wiki/Nouveau#Phantom_and_unpopulated_output_connector_issues)
I have disabled two outputs at yaboot stage (video=TV-1:d video=VGA-1:d)
Also edited xorg.conf:

Section "Monitor"
     Identifier   "LVDS-1"
     VendorName   "Monitor Vendor"
     ModelName    "Monitor Model"
EndSection
Section "Monitor"
     Identifier   "TV-1"
     Option "Ignore" "True"
EndSection
Section "Monitor"
     Identifier   "DVI-D-1"
     Option "Ignore" "True"
EndSection
Section "Monitor"
     Identifier   "VGA-1"
     Option "Ignore" "True"
EndSection


So, under /sys/class/drm I have:

card0
card0-LVDS-1
card0-TV-1
card0-VGA-1
controlD64
renderD128
ttm
version

I have disabled VGA-1 and TV-1. Now their status is as follows:
root@japko:/sys/class/drm/card0-TV-1# cat enabled 
disabled
root@japko:/sys/class/drm/card0-TV-1# pwd
/sys/class/drm/card0-TV-1

root@japko:/sys/class/drm/card0-VGA-1# cat enabled 
disabled
root@japko:/sys/class/drm/card0-VGA-1# pwd
/sys/class/drm/card0-VGA-1

It all is the same. Black screen and no cursor.
Now Xorg log is like this: [http://pastebin.com/vrC9Gyk2](http://pastebin.com/vrC9Gyk2)

I can see that  LVDS-1 is the laptops screen. When screensaver kicks in
/sys/class/drm/card0-LVDS-1/dpms contains Off. Other two do not change its state and are On all the time.
If I move mouse then it goes into On state. So I have proper display pinpointed.

I will try to debug more into plymouth and drm to see what happens.

---

### Post by abtabt on 2016-05-22
ptoki

you can try nvidiafb

short version

boot option live nomodeset video=offb:off single

wait   (black screen you dont see anyting )
then when boot is ended 

enter

type modprobe nvidiafb (if you see CLI its ok )

make a xorg.conf

Xorg -configure

edit xorg.confnew 

Hash driver and add DefaultDepth 16

cp xorg.confnew /etc/X11/xorg.conf 

then ctrl+D    (exit and continue boot and if all is ok you will have GUI )

and install or test

---

### Post by ptoki on 2016-05-22
Still no luck.
After enabling drm debug I dont see any obvious reasons for this problem.
Here is full log with drm.debug=0x4 enabled [http://pastebin.com/vvjRu7fQ](http://pastebin.com/vvjRu7fQ)
I tried to use nv module for xorg. It crashes. I compiled it from debian repository sources and from main source. Similar behaviour.
I also reseted PRAM, and tried various mixes of parameters, xorg modules etc.

I think I will file a bug, maybe there is some advanced way to diagnose what is wrong.


[edit]
I will try now abtabt solution.

---

### Post by rsavage on 2016-05-22
That's disappointing.

Couple of things.... have you tried increasing the screen brightness? Not sure if you have to have the function key pressed for that to work.  I guess you've tried ctrl-alt-f1 etc and switching back to tty7?  Some times repeated tries at this can get something on the screen.

Are you sure you used nouveau in 10.04?  I'm quite surprised 12.04 doesn't work since that was quite well tested at the time.  I'm sure somebody had your machine working of sorts.

Nv driver doesn't ordinarily work past 12.04 as far as I know, although I compiled the 12.04 xorg stack for 14.04 so that it does work in 14.04 (packages available on the forum). You can also use the nvidiafb/rivafb framebuffers.  Basically look for imac g4 stuff since that also has problems with nouveau.  That's been done to death and I'm not going to repeat any of it!  So don't even ask me!

The best thing to do is report a bug here [https://bugs.freedesktop.org/](https://bugs.freedesktop.org/) so you can speak to a nouveau developer.  Don't waste your time on Launchpad.  There are a few PowerBook quirks already coded into the nouveau driver (actually for your card already I think) so they may need reviewing.  If you need help applying patches and compiling the kernel driver then give us a shout.

---

### Post by ptoki on 2016-05-22
After trying the solution with nomodeset offb:off and changed xorg.conf I ended up with restarting xorg:
Log is here: [http://pastebin.com/pKJSsKb6](http://pastebin.com/pKJSsKb6)

Basically it finished with:
[    96.870] (EE) FBDEV(0): FBIOPUT_VSCREENINFO succeeded but modified mode

 [    96.870] (EE) FBDEV(0): mode initialization failed

 [    96.870] (EE) 
 Fatal server error:
 [    96.870] (EE) AddScreen/ScreenInit failed for driver 0
 [    96.870] (EE) 
 [    96.870] (EE)

To recap:
When booted with no options it goes into black screen with backlight. It flickers three times.
Xorg seems to be quite happy with that. Here is its log in such case: [http://pastebin.com/WqyJUqms](http://pastebin.com/WqyJUqms)

Other options - using nv module unloading nouveau etc does not work either.

I am not sure how it was configured in 10.04. I did not messed with it. It just worked straight form install iso.
I may try to boot it from cd and peek how it was done there.

I tried to change brightness - no change. 
When I have it booted normaly I dont have working tty. During kernel boot just after first line shows up display goes into this black state.
If I boot with nomodeset or nouveau.modeset=0 then I have "psychodelic" garbled screen with cursor and no lightdm controls (but lightdm process works). In this case I have working text console and I am able to switch them and use them. After killing lightdm it starts again and switches again into psychodelic graphics screen. And again I can switch to tty console.

So that is it :)
I will look to file a bug and contact the developer.
Thanks a lot for support and nice ride through Xorg and nouveau driver :)

---

### Post by ptoki on 2016-05-22
One more quiestion:
Does anyone succesfully installed and use ubuntu 15 or 16 on such G4 machines?
I mean something around powerbook g4 with GeForce4 440 Go 64M?

---

### Post by rsavage on 2016-05-22
I think you have misunderstood abtabt's instructions.  You should definitely be able to get something working with a legacy framebuffer (I think rivafb for you but don't hold me to that).  But like I say I've explained it too many times already on this forum! The psychedelic colours are to be expected with the openfirmware framebuffer since it has a very limited colour palette.

---

### Post by rsavage on 2016-05-22
Are you sure you have the right card listed?  Is it this machine [http://www.everymac.com/systems/apple/powerbook_g4/specs/powerbook_g4_867_12.html](http://www.everymac.com/systems/apple/powerbook_g4/specs/powerbook_g4_867_12.html) ?

---

### Post by este.el.paz on 2016-05-22
> **ptoki said:**
> One more quiestion:
Does anyone succesfully installed and use ubuntu 15 or 16 on such G4 machines?
I mean something around powerbook g4 with GeForce4 440 Go 64M?

ptoki:

I think abtabt has 16 running on his iMac 800, so his advice should get you in the ballpark . . . .  The fact that you can even see "psychedelic" colors is a sign that you are "close" . . . .  But as rsavage suggests this topic has been well covered historically on the forum, easier to find it using Google rather than forum search engine . . . .

Also, you could try other "flavors" of ubuntu, or even whole other linux choices and just go with what works best/easiest on your machine.  I found it "harder" to get straight "ubuntu" to run on my three G4 units . . . right now have Lubuntu 16 running on radeon iBook, and U-MATE running on ATI/Rage PowerMac . . . and like I mentioned was able to get fbdev going on my Nvidia iMac, but, then with help from rsavage and str8bs I was able to "configure" nv, which was "better" than fbdev . . . in 12.04.

Don't give up, drink the Kool-aid . . . drink deeply.  : - )

e...

---

### Post by ptoki on 2016-05-23
@rsavage.
I have this machine however lspci gives me different specs about graphics card.
I got it more or less accidentally so I dont know what is exactly inside. osx was wiped from it quite long time ago.
I will try some of your suggestions. 
The reason I came here was because I saw that a lot of people know similar issues so you could point me in right direction.

I ordered this video cable to see if that would help with diagnostics. Will try some other ways to make it run :)

Thanks for help.

---

### Post by abtabt on 2016-05-23
ptoki look at post [http://ubuntuforums.org/showthread.php?t=2301608&p=13493268#post13493268](http://ubuntuforums.org/showthread.php?t=2301608&p=13493268#post13493268) one more time,i have edit post

i see in your xorg.log that offb not is off and memory is 768 kb, if you try one more time  
96.808] (II) FBDEV(0): hardware: OFfb NVDA,Displ (video memory: 768kB)
95.753] Kernel command line: root=UUID=aa80e24d-17b4-461e-9c61-7c8b1c1f25d7 ro quiet splash nomodeset

post your xorg log and your xorg.conf

---

### Post by ernsteiswuerfel on 2016-07-24
Due to an update mesa-11.2.1 -> **mesa-12.0.1** in Yakkety's daily iso the nasty [bug #1432949]("https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1432949") is gone!  KMS works now on my PowerBook 5,6, 3D with r300 works on bit depths > 16 bit , GPU compositors work, even compiz can be enabled and works so far. 

I hope mesa-12.0.1 will find its way into Xenial 16.04.2 LTS!

---

### Post by este.el.paz on 2016-08-14
@et al:

Never mind; operator error . . . question "answered" on U-MATE forum . . . 

e..

---

### Post by xeno74 on 2016-08-16
Just for info.

I have figured out, that it is very important to set the **BusID** _correctly_. Without the BusID or with the incorrect BusID, Xorg doesn't start with my **Radeon HD6870**.

xorg.conf:

```
BusID "PCI:1:0:0"
```

Sometimes I have to set

```
Option "RenderAccel" "false"
```

additionally.

[IMG]https://lh5.googleusercontent.com/-b4K0suvJ-ro/V5cW3AhrNwI/AAAAAAAADMw/rk9yhJsBYlUPpd-dm6uY41pUj_RHn8-GQCL0B/w721-h539-no/ubuntu_MATE_16.04.1_LTS_PowerPC_with_kernel_4.7.0.png[/IMG]

---

### Post by xeno74 on 2016-08-17
[IMG]http://static.xubuntu.org/xubuntu_brand/Logo/PNG/xubuntu_logo_black.png[/IMG] [IMG]https://upload.wikimedia.org/wikipedia/commons/thumb/2/27/Lubuntu_logo.svg/320px-Lubuntu_logo.svg.png[/IMG]

Hi All,

Yesterday, I successfully updated my xubuntu PPC and Lubuntu PPC to version 16.04.1 LTS on my USB flash drive.

```
setenv bootargs "root=/dev/sdd2 quiet ro splash rootdelay=5"
```

```
boot -elf -noints -fatfs cf0:vmlinux-4.8
```

```
apt-get update
```

```
apt-get upgrade
```

Screenshots of xubuntu and Lubuntu 16.04.1 LTS PowerPC with the **[RC2]("http://www.xenosoft.de/vmlinux-4.8-rc2-AmigaONE_X1000.tar.gz")** of **kernel 4.8**:

[[IMG]https://lh3.googleusercontent.com/-HTExuGTUw8Y/V7L0cF2urbI/AAAAAAAADQg/n2xdvu8rO2E3YJmAapLZJId1Q1oc7Gc5QCL0B/w506-h380/xubuntu_16.04.1_LTS_PowerPC.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/VsHr2ASh7mC") [[IMG]https://lh3.googleusercontent.com/-CZgVlE8c9DQ/V7L4cgfEFeI/AAAAAAAADRI/Oa3y0rgDSucq9rG_aDvs-lKgsAknIGfRACL0B/w506-h380/Lubuntu_16.04.1_LTS_PowerPC.png[/IMG]]("https://plus.google.com/115515624056477014971/posts/dskUNAtAQEZ")

Cheers,

Christian

---

### Post by chdrsto on 2016-08-20
Hi xeno74
Can you post/share your full xorg.conf?

---

### Post by Casey_C on 2016-08-21
> **Tim_Brendel said:**
> That string didn't work for me. I also tried the one here:[http://ricanlinux.blogspot.com/2015/03/ubuntu-mate-on-my-ibook-g4.html?m=1](http://ricanlinux.blogspot.com/2015/03/ubuntu-mate-on-my-ibook-g4.html?m=1). 

No luck either :( 

I read somewhere that switching from PCI16x to PCI8x may be worth a try? Thought I'd ask before moving it though.

Hey sorry this is coming a little late but... 
I also had unresolvable issues trying to get any Linux distro to work with my Apple/OpenFirmware Radeon X1900.  I think its because the Radeon X1900 is an aftermarket card, flashed with OpenFirmware but xorg expects it to be x86.  You'd have much better luck with an Apple/OpenFirmware NVidia 6600 or 6600LE in the PCIe 16X, and then if you want put a Radeon HD in the PCIe 8X. This is what I do, and I'm pretty sure Luigi does also.  I'm pretty sure I have a few extra 6600s laying around actually if you need one.

---

### Post by xeno74 on 2016-08-22
> **chdrsto said:**
> Hi xeno74
Can you post/share your full xorg.conf?

Yes, of course.

```

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "EnablePageFlip"         # [<bool>]
        #Option     "ColorTiling"            # [<bool>]
        #Option     "ColorTiling2D"          # [<bool>]
        Option     "RenderAccel"    "false"
        #Option     "SubPixelOrder"          # [<str>]
        #Option     "AccelMethod"            # <str>
        #Option     "EXAVSync"               # [<bool>]
        #Option     "EXAPixmaps"             # [<bool>]
        #Option     "ZaphodHeads"            # <str>
        #Option     "EnablePageFlip"         # [<bool>]
        #Option     "SwapbuffersWait"        # [<bool>]
    Identifier  "Card0"
    Driver      "radeon"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "Rotate"                 # <str>
        #Option     "fbdev"                  # <str>
        #Option     "debug"                  # [<bool>]
    Identifier  "Card1"
    Driver      "radeon"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    Monitor    "Monitor1"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```

ubuntu MATE 16.04.1 PowerPC: Pure 3D :-)&#65279;

[[IMG]https://lh3.googleusercontent.com/-MmL2s52Habg/V7rM1CT8htI/AAAAAAAADTg/EULP8CruHOk-oLlE92QtDMwka3l5xLr-ACJoC/w506-h380/ubuntu_MATE_16.04.1_PowerPC_kernel_4.8-rc3.png[/IMG]](https://plus.google.com/115515624056477014971/posts/AaMDSsig1L1)

---

### Post by luigiburdo on 2016-08-23
Hi Christian, did you have two video cards there ?

---

### Post by xeno74 on 2016-08-23
> **luigiburdo said:**
> Hi Christian, did you have two video cards there ?

No, only one but with two DVI connections.

---


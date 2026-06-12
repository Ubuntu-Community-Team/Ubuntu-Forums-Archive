---
title: "weird openGL issue"
date: 2012-09-03
forum: Any Other OS
---

### Post by tesla.coil on 2012-09-03
Hi lads,

This is something not specific to ubuntu,so i thought of posting it over here.

I have a peculiar issue where openGL on my machine is broken. When i run glxgears i get a terrible frame rate of 2-3.The more i maximize the glxgear window,terrible the rate.If i were to reduce the size of the window i see a drastic improvement in the frame rate,though i cannot see the spinning gears.

All OpenGL applications exhibit some sort of sluggish behavior,and also full screen flash video refuse to play with hardware acceleration on.Basically,it looks like some sort screen draw/render issue.

Just wondering if there is any openGL expert in here,who might have an idea on what aspect of OpenGL or Nvidia driver could be the cause of this weirdness

This is on a Nvidia Quadro 4000 + 304.43 drivers running on a 2.6.32.Other Quadro cards do not have this issue.

# glxgears

```

13 frames in 5.1 seconds =  2.568 FPS
12 frames in 5.1 seconds =  2.352 FPS
```

# glxinfo

```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_EXT_swap_control, GLX_EXT_swap_control_tear,
    GLX_EXT_texture_from_pixmap, GLX_ARB_create_context,
    GLX_ARB_create_context_profile, GLX_EXT_create_context_es_profile,
    GLX_EXT_create_context_es2_profile, GLX_ARB_create_context_robustness,
    GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_fbconfig_float,
    GLX_NV_swap_group, GLX_EXT_framebuffer_sRGB, GLX_NV_multisample_coverage,
    GLX_NV_copy_image, GLX_NV_video_capture
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync,
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGI_swap_control, GLX_EXT_swap_control, GLX_EXT_swap_control_tear,
    GLX_ARB_create_context, GLX_ARB_create_context_profile,
    GLX_NV_float_buffer, GLX_ARB_fbconfig_float,
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap,
    GLX_EXT_framebuffer_sRGB, GLX_NV_present_video, GLX_NV_copy_image,
    GLX_NV_multisample_coverage, GLX_NV_video_capture,
    GLX_EXT_create_context_es2_profile, GLX_ARB_create_context_robustness
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_EXT_swap_control, GLX_EXT_swap_control_tear,
    GLX_EXT_texture_from_pixmap, GLX_ARB_create_context,
    GLX_ARB_create_context_profile, GLX_EXT_create_context_es2_profile,
    GLX_ARB_create_context_robustness, GLX_ARB_multisample,
    GLX_NV_float_buffer, GLX_ARB_fbconfig_float, GLX_NV_swap_group,
    GLX_EXT_framebuffer_sRGB, GLX_NV_multisample_coverage, GLX_NV_copy_image,
    GLX_NV_video_capture, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: Quadro 4000/PCIe/SSE2
OpenGL version string: 4.2.0 NVIDIA 304.43
OpenGL extensions:
    GL_AMD_multi_draw_indirect, GL_ARB_base_instance,
    GL_ARB_blend_func_extended, GL_ARB_color_buffer_float,
    GL_ARB_compatibility, GL_ARB_compressed_texture_pixel_storage,
    GL_ARB_conservative_depth, GL_ARB_copy_buffer, GL_ARB_depth_buffer_float,
    GL_ARB_depth_clamp, GL_ARB_depth_texture, GL_ARB_draw_buffers,
    GL_ARB_draw_buffers_blend, GL_ARB_draw_indirect,
    GL_ARB_draw_elements_base_vertex, GL_ARB_draw_instanced,
    GL_ARB_ES2_compatibility, GL_ARB_explicit_attrib_location,
    GL_ARB_fragment_coord_conventions, GL_ARB_fragment_program,
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader,
    GL_ARB_framebuffer_object, GL_ARB_framebuffer_sRGB,
    GL_ARB_geometry_shader4, GL_ARB_get_program_binary, GL_ARB_gpu_shader5,
    GL_ARB_gpu_shader_fp64, GL_ARB_half_float_pixel, GL_ARB_half_float_vertex,
    GL_ARB_imaging, GL_ARB_instanced_arrays, GL_ARB_internalformat_query,
    GL_ARB_map_buffer_alignment, GL_ARB_map_buffer_range, GL_ARB_multisample,
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_occlusion_query2,
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite,
    GL_ARB_provoking_vertex, GL_ARB_robustness, GL_ARB_sample_shading,
    GL_ARB_sampler_objects, GL_ARB_seamless_cube_map,
    GL_ARB_separate_shader_objects, GL_ARB_shader_atomic_counters,
    GL_ARB_shader_bit_encoding, GL_ARB_shader_image_load_store,
    GL_ARB_shader_objects, GL_ARB_shader_precision, GL_ARB_shader_subroutine,
    GL_ARB_shader_texture_lod, GL_ARB_shading_language_100,
    GL_ARB_shading_language_420pack, GL_ARB_shading_language_include,
    GL_ARB_shading_language_packing, GL_ARB_shadow, GL_ARB_sync,
    GL_ARB_tessellation_shader, GL_ARB_texture_border_clamp,
    GL_ARB_texture_buffer_object, GL_ARB_texture_buffer_object_rgb32,
    GL_ARB_texture_compression, GL_ARB_texture_compression_bptc,
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_cube_map,
    GL_ARB_texture_cube_map_array, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_float, GL_ARB_texture_gather,
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_multisample,
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_query_lod,
    GL_ARB_texture_rectangle, GL_ARB_texture_rg, GL_ARB_texture_rgb10_a2ui,
    GL_ARB_texture_storage, GL_ARB_texture_swizzle, GL_ARB_timer_query,
    GL_ARB_transform_feedback2, GL_ARB_transform_feedback3,
    GL_ARB_transform_feedback_instanced, GL_ARB_transpose_matrix,
    GL_ARB_uniform_buffer_object, GL_ARB_vertex_array_bgra,
    GL_ARB_vertex_array_object, GL_ARB_vertex_attrib_64bit,
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader,
    GL_ARB_vertex_type_2_10_10_10_rev, GL_ARB_viewport_array,
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_texture_float,
    GL_ATI_texture_mirror_once, GL_S3_s3tc, GL_EXT_texture_env_add,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_bindable_uniform, GL_EXT_blend_color,
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array,
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_direct_state_access,
    GL_EXT_draw_buffers2, GL_EXT_draw_instanced, GL_EXT_draw_range_elements,
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample,
    GL_EXTX_framebuffer_mixed_formats, GL_EXT_framebuffer_object,
    GL_EXT_framebuffer_sRGB, GL_EXT_geometry_shader4,
    GL_EXT_gpu_program_parameters, GL_EXT_gpu_shader4,
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil,
    GL_EXT_packed_float, GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object,
    GL_EXT_point_parameters, GL_EXT_provoking_vertex, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_shader_objects,
    GL_EXT_separate_specular_color, GL_EXT_shader_image_load_store,
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap,
    GL_EXT_texture3D, GL_EXT_texture_array, GL_EXT_texture_buffer_object,
    GL_EXT_texture_compression_dxt1, GL_EXT_texture_compression_latc,
    GL_EXT_texture_compression_rgtc, GL_EXT_texture_compression_s3tc,
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_format_BGRA8888,
    GL_EXT_texture_integer, GL_EXT_texture_lod, GL_EXT_texture_lod_bias,
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object,
    GL_EXT_texture_shared_exponent, GL_EXT_texture_sRGB,
    GL_EXT_texture_sRGB_decode, GL_EXT_texture_storage,
    GL_EXT_texture_swizzle, GL_EXT_texture_type_2_10_10_10_REV,
    GL_EXT_timer_query, GL_EXT_transform_feedback2, GL_EXT_vertex_array,
    GL_EXT_vertex_array_bgra, GL_EXT_vertex_attrib_64bit,
    GL_EXT_x11_sync_object, GL_EXT_import_sync_object,
    GL_NVX_shared_sync_object, GL_IBM_rasterpos_clip,
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_alpha_test,
    GL_NV_blend_minmax, GL_NV_blend_square, GL_NV_complex_primitives,
    GL_NV_conditional_render, GL_NV_copy_depth_to_color, GL_NV_copy_image,
    GL_NV_depth_buffer_float, GL_NV_depth_clamp, GL_NV_ES1_1_compatibility,
    GL_NV_explicit_multisample, GL_NV_fbo_color_attachments, GL_NV_fence,
    GL_NV_float_buffer, GL_NV_fog_distance, GL_NV_fragdepth,
    GL_NV_fragment_program, GL_NV_fragment_program_option,
    GL_NV_fragment_program2, GL_NV_framebuffer_multisample_coverage,
    GL_NV_geometry_shader4, GL_NV_gpu_program4, GL_NV_gpu_program4_1,
    GL_NV_gpu_program5, GL_NV_gpu_program_fp64, GL_NV_gpu_shader5,
    GL_NV_half_float, GL_NV_light_max_exponent, GL_NV_multisample_coverage,
    GL_NV_multisample_filter_hint, GL_NV_occlusion_query,
    GL_NV_packed_depth_stencil, GL_NV_parameter_buffer_object,
    GL_NV_parameter_buffer_object2, GL_NV_path_rendering,
    GL_NV_pixel_data_range, GL_NV_point_sprite, GL_NV_primitive_restart,
    GL_NV_register_combiners, GL_NV_register_combiners2,
    GL_NV_shader_atomic_counters, GL_NV_shader_atomic_float,
    GL_NV_shader_buffer_load, GL_NV_texgen_reflection, GL_NV_texture_barrier,
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4,
    GL_NV_texture_expand_normal, GL_NV_texture_lod_clamp,
    GL_NV_texture_multisample, GL_NV_texture_rectangle, GL_NV_texture_shader,
    GL_NV_texture_shader2, GL_NV_texture_shader3, GL_NV_transform_feedback,
    GL_NV_transform_feedback2, GL_NV_vdpau_interop, GL_NV_vertex_array_range,
    GL_NV_vertex_array_range2, GL_NV_vertex_attrib_integer_64bit,
    GL_NV_vertex_buffer_unified_memory, GL_NV_vertex_program,
    GL_NV_vertex_program1_1, GL_NV_vertex_program2,
    GL_NV_vertex_program2_option, GL_NV_vertex_program3, GL_NV_video_capture,
    GL_NVX_sysmem_buffer, GL_NVX_conditional_render, GL_NVX_gpu_memory_info,
    GL_OES_compressed_paletted_texture, GL_OES_depth24, GL_OES_depth32,
    GL_OES_depth_texture, GL_OES_element_index_uint, GL_OES_fbo_render_mipmap,
    GL_OES_get_program_binary, GL_OES_mapbuffer, GL_OES_packed_depth_stencil,
    GL_OES_point_size_array, GL_OES_point_sprite, GL_OES_rgb8_rgba8,
    GL_OES_read_format, GL_OES_standard_derivatives, GL_OES_texture_3D,
    GL_OES_texture_float, GL_OES_texture_float_linear,
    GL_OES_texture_half_float, GL_OES_texture_half_float_linear,
    GL_OES_texture_npot, GL_OES_vertex_array_object, GL_OES_vertex_half_float,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, GL_SGIX_depth_texture,
    GL_SGIX_shadow, GL_SUN_slice_accum
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess
```

---

### Post by tesla.coil on 2012-09-04
*bump*

---


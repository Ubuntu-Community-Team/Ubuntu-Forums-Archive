---
title: "Compiz Fusion Effects"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by scondrel on 2008-04-03
HI GUYS HAVE TRIED UBUNTU FOR THE FIRST TIME ..I HAVE A SAPPHIRE  HD 2600 XT RADEON CARD.INSTALLED THE LATEST ATI DRIVER ati-driver-installer-8-3-x86.x86_64. FROM THE GUIDE  ON THE FORUMS AND DONE EVERYTHING PERFECTLY ..BUT STILL CANNOT GET COMPIZ EFFECTSTO BE ENABLED OR TO WORK.. IS THERE ANY SUGGESTIONS..HERE IS MY INFO FROM MY PC 
```
 fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Brian Paul
OpenGL renderer string: Mesa X11
OpenGL version string: 2.1 Mesa 7.0.1

$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: Brian Paul
server glx version string: 1.4 Mesa 7.0.1
server glx extensions:
    GLX_MESA_copy_sub_buffer, GLX_MESA_pixmap_colormap, 
    GLX_MESA_release_buffers, GLX_ARB_get_proc_address, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer
client glx vendor string: Brian Paul
client glx version string: 1.4 Mesa 7.0.1
client glx extensions:
    GLX_MESA_copy_sub_buffer, GLX_MESA_pixmap_colormap, 
    GLX_MESA_release_buffers, GLX_ARB_get_proc_address, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer
GLX version: 1.4
GLX extensions:
    GLX_MESA_copy_sub_buffer, GLX_MESA_pixmap_colormap, 
    GLX_MESA_release_buffers, GLX_ARB_get_proc_address, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer
OpenGL vendor string: Brian Paul
OpenGL renderer string: Mesa X11
OpenGL version string: 2.1 Mesa 7.0.1
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_shader, GL_ARB_half_float_pixel, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_shading_language_120, GL_ARB_shadow, GL_ARB_shadow_ambient, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements, 
    GL_EXT_framebuffer_object, GL_EXT_framebuffer_blit, GL_EXT_fog_coord, 
    GL_EXT_gpu_program_parameters, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_timer_query, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_APPLE_vertex_array_object, GL_ATI_blend_equation_separate, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_ATI_fragment_shader, GL_ATI_separate_stencil, 
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_program_debug, GL_MESA_resize_buffers, 
    GL_MESA_ycbcr_texture, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_fragment_program, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGI_texture_color_table, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow, 
    GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x25 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x27 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x28 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x29 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x2a 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x2b 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x2c 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x2d 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x2e 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x2f 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x30 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x31 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x32 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x33 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x34 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x35 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x36 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x37 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x38 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x39 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x3a 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x3b 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x3c 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x3d 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x3e 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x3f 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x40 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x41 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x42 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x43 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x44 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x45 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x46 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x47 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x48 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x49 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x4a 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x4b 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x4c 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x4d 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x4e 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x4f 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x50 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x51 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x52 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x53 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x54 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x55 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x56 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x57 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x58 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x59 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x5a 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x5b 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x5c 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x5d 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x5e 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x5f 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x60 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x61 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x62 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x63 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x64 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x65 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x66 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x67 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x68 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x69 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x6a 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x6b 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x6c 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x6d 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x6e 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x6f 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x70 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x71 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x72 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x88 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
```
 GUYS I M A NEWBIE SO I REALLY DONT KNOW WHAT T O  DO  NEXT

---

### Post by medley on 2008-04-03
Do you have the compiz configuration manager installed? If not, you'll need to so that you can enable the specifics effects you want.

---

### Post by hellomoto on 2008-04-03
Is your graphics card installed or are you just strugling to enable the desktop effects.

Go to system>preferences>appearance>visual effects

then click on extra.

Does this enable or return an error?

---

### Post by scondrel on 2008-04-03
the compiz manager is installed and so is the ati video card.. i followed a guide and did everything possible that was required t o install the propietary drivers

---

### Post by medley on 2008-04-04
> **scondrel said:**
> the compiz manager is installed and so is the ati video card.. i followed a guide and did everything possible that was required t o install the propietary drivers

What happens if you launch compiz from the console? (type 'compiz --replace' without the quotes)?

Also, try the same for the configuration manager (ccsm). You should see some error messages. Try posting them here.

---

### Post by scondrel on 2008-04-05
WHEN I TYPE (ccsm) THE COMPIZ MANAGER OPENS UP AND WHEN I TYPE THE OTHER COMMAND 'compiz --replace' I GET THIS ERROR 

~$ compiz --replace

Checking for Xgl: not present. 

Detected PCI ID for VGA: 03:00.0 0300: 1002:9588 (prog-if 00 [VGA])

Checking for texture_from_pixmap: not present. 

Trying again with indirect rendering:

Checking for texture_from_pixmap: not present. 

aborting and using fallback: /usr/bin/metacity

---

### Post by Martje_001 on 2008-04-05
Please don't typ with CAPS LOCK on, it's annoying and might scare people away.

Have you tried installing *xserver-xgl* with synaptic (please press CTRL - ALT - BACKSPACE when it's installed)?

---

### Post by Crafty Kisses on 2008-04-05
> **Martje_001 said:**
> Please don't typ with CAPS LOCK on, it's annoying and might scare people away.

Have you tried installing *xserver-xgl* with synaptic (please press CTRL - ALT - BACKSPACE when it's installed)?

It appears you don't have XGL enabled.

---

### Post by Mazza558 on 2008-04-05
Do this in the terminal 

> sudo apt-get install xserver-xgl

and after installing, do CTRL + ALT + Backspace and login again.

---

### Post by shillizzle on 2008-04-05
I have been following this post as i too wanted to get the desktop effects enabled. i get the compiz manager installed, then found out that i also needed the xgl. I got that installed fine and restarted, but now my scrolling up and down when viewing a page is all choppy and new pages pop up in a diagonal wipe.. basically i am not happy with my system but dont know how to unistall this xgl thingy, lol guess, thats what i get for riding on the coat-tails of others posts:(

---

### Post by scondrel on 2008-05-13
i have installed hardy heron after i finally got the compiz fusion to work on gutsy gibbon..but now its back to the same problem..cannot enable effects ..i hope the solution is the same to install xgl or the new xorg.. what is your advice guys ..here is my error readouts

scondrel@CHAOS:~$  fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Brian Paul
OpenGL renderer string: Mesa X11
OpenGL version string: 2.1 Mesa 7.0.3-rc2

scondrel@CHAOS:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: Brian Paul
server glx version string: 1.4 Mesa 7.0.3-rc2
server glx extensions:
    GLX_MESA_copy_sub_buffer, GLX_MESA_pixmap_colormap, 
    GLX_MESA_release_buffers, GLX_ARB_get_proc_address, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer
client glx vendor string: Brian Paul
client glx version string: 1.4 Mesa 7.0.3-rc2
client glx extensions:
    GLX_MESA_copy_sub_buffer, GLX_MESA_pixmap_colormap, 
    GLX_MESA_release_buffers, GLX_ARB_get_proc_address, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer
GLX version: 1.4
GLX extensions:
    GLX_MESA_copy_sub_buffer, GLX_MESA_pixmap_colormap, 
    GLX_MESA_release_buffers, GLX_ARB_get_proc_address, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer
OpenGL vendor string: Brian Paul
OpenGL renderer string: Mesa X11
OpenGL version string: 2.1 Mesa 7.0.3-rc2
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_fragment_program, 
    GL_ARB_fragment_shader, GL_ARB_half_float_pixel, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_shading_language_120, GL_ARB_shadow, GL_ARB_shadow_ambient, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements, 
    GL_EXT_framebuffer_object, GL_EXT_framebuffer_blit, GL_EXT_fog_coord, 
    GL_EXT_gpu_program_parameters, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal, 
    GL_EXT_secondary_color, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_shared_texture_palette, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_timer_query, GL_EXT_vertex_array, GL_APPLE_packed_pixels, 
    GL_APPLE_vertex_array_object, GL_ATI_blend_equation_separate, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_ATI_fragment_shader, GL_ATI_separate_stencil, 
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_program_debug, GL_MESA_resize_buffers, 
    GL_MESA_ycbcr_texture, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_fragment_program, GL_NV_light_max_exponent, GL_NV_point_sprite, 
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGI_texture_color_table, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow, 
    GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x25 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x27 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x28 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x29 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x2a 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x2b 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x2c 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x2d 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x2e 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x2f 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x30 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x31 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x32 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x33 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x34 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x35 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x36 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x37 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x38 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x39 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x3a 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x3b 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x3c 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x3d 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x3e 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x3f 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x40 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x41 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x42 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x43 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x44 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x45 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x46 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x47 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x48 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x49 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x4a 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x4b 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x4c 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x4d 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x4e 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x4f 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x50 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x51 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x52 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x53 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x54 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x55 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x56 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x57 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x58 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x59 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x5a 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x5b 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x5c 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x5d 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x5e 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x5f 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x60 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x61 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x62 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x63 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x64 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x65 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x66 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x67 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x68 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x69 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x6a 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x6b 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x6c 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x6d 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x6e 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x6f 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x70 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x71 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x72 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16 16  0 0 None
0x85 32 tc  0 32  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None


scondrel@CHAOS:~$ compiz --replace 
Checking for Xgl: not present. 
Detected PCI ID for VGA: 03:00.0 0300: 1002:9588 (prog-if 00 [VGA controller]) 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering: 
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing 
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0 
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

---

### Post by thevikingking on 2008-05-14
ooook so i am having some problems activating compiz on my own... i need to download some stuff for the restricted drivers, but when i hit enable this error message shows up...

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.12-16.34_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.12-16.34_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

so i dont know what this is about or how to fix it... it isnt letting me enable my nvidia graphics card and would like to know why. 

thanx 

please help!

---

### Post by durableapostle on 2008-05-15
Try this in terminal:
> sudo apt-get install compizconfig-settings-manager simple-ccsm
Then open it, and look under "animations." This might be what you are looking for.

---


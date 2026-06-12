---
title: "Is my driver working?"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by ITdrummer on 2007-06-29
Hello,

Specs:

Pentium 4 - 2.2 Ghz
512Mb RAM
30GB Hd
Dual-boot: XP/Ubuntu 7.04

I just completed a successful dual-boot installation and i was wondering if i have the correct graphics driver installed.  Is there an easy way to tell.  My display seems to work perfectly, although, i havent played any graphically intense games yet to tell if its REALLY working.  Any suggestions?

Glxinfo:>  $ glxinfo
name of display: :0.0
display: :0 screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap,
GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer,
GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control,
GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
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
GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control,
GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read,
GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample,
GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 845G 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 6.5.2
OpenGL extensions:
GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture,
GL_ARB_point_parameters, GL_ARB_texture_border_clamp,
GL_ARB_texture_compression, GL_ARB_texture_cube_map,
GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3,
GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle,
GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object,
GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra,
GL_EXT_blend_color, GL_EXT_blend_equation_separate,
GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array,
GL_EXT_convolution, GL_EXT_copy_texture, GL_EXT_draw_range_elements,
GL_EXT_fog_coord, GL_EXT_histogram, GL_EXT_multi_draw_arrays,
GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset,
GL_EXT_rescale_normal, GL_EXT_secondary_color,
GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture,
GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp,
GL_EXT_texture_env_add, GL_EXT_texture_env_combine,
GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle,
GL_EXT_vertex_array, GL_3DFX_texture_compression_FXT1,
GL_APPLE_client_storage, GL_APPLE_packed_pixels,
GL_ATI_blend_equation_separate, GL_IBM_rasterpos_clip,
GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate,
GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos,
GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle,
GL_NV_texgen_reflection, GL_NV_vertex_program, GL_NV_vertex_program1_1,
GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table,
GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

visual x bf lv rg d st colorbuffer ax dp st accumbuffer ms cav
id dep cl sp sz l ci b ro r g b a bf th cl r g b a ns b eat
----------------------------------------------------------------------
0x23 16 tc 0 16 0 r y . 5 6 5 0 0 16 0 0 0 0 0 0 0 None
0x24 16 tc 0 16 0 r . . 5 6 5 0 0 16 0 0 0 0 0 0 0 None
0x25 16 tc 0 16 0 r y . 5 6 5 0 0 16 8 0 0 0 0 0 0 Slow
0x26 16 tc 0 16 0 r . . 5 6 5 0 0 16 8 0 0 0 0 0 0 Slow
0x27 16 tc 0 16 0 r y . 5 6 5 0 0 16 0 16 16 16 0 0 0 Slow
0x28 16 tc 0 16 0 r . . 5 6 5 0 0 16 0 16 16 16 0 0 0 Slow
0x29 16 tc 0 16 0 r y . 5 6 5 0 0 16 8 16 16 16 0 0 0 Slow
0x2a 16 tc 0 16 0 r . . 5 6 5 0 0 16 8 16 16 16 0 0 0 Slow
0x2b 16 dc 0 16 0 r y . 5 6 5 0 0 16 0 0 0 0 0 0 0 None
0x2c 16 dc 0 16 0 r . . 5 6 5 0 0 16 0 0 0 0 0 0 0 None
0x2d 16 dc 0 16 0 r y . 5 6 5 0 0 16 8 0 0 0 0 0 0 Slow
0x2e 16 dc 0 16 0 r . . 5 6 5 0 0 16 8 0 0 0 0 0 0 Slow
0x2f 16 dc 0 16 0 r y . 5 6 5 0 0 16 0 16 16 16 0 0 0 Slow
0x30 16 dc 0 16 0 r . . 5 6 5 0 0 16 0 16 16 16 0 0 0 Slow
0x31 16 dc 0 16 0 r y . 5 6 5 0 0 16 8 16 16 16 0 0 0 Slow
0x32 16 dc 0 16 0 r . . 5 6 5 0 0 16 8 16 16 16 0 0 0 Slow
0x4b 32 tc 0 32 0 r . . 8 8 8 8 0 0 0 0 0 0 0 0 0 Ncon


and my lspci:
> 

~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02)
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:04.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller


---

### Post by chamberlain2006 on 2007-06-29
Seems so, it says you have direct rendering enabled.  Seems to be all good.

---

### Post by misconfiguration on 2007-06-29
do the command 

```
glxgears
```

if you see the gears rotate you should be set!

---

### Post by ITdrummer on 2007-07-16
Ok, umm... i dont know exactly what i am looking for, but my direct rendering is : yes  but i still think im having a problem with my graphics.  Please see this thread for my issue.  If the problem stated is not clear or vague, let me know.  [http://ubuntuforums.org/showthread.php?p=3028321#post3028321](http://ubuntuforums.org/showthread.php?p=3028321#post3028321)

---


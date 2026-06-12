---
title: "Where to find Video Drivers"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by happybill on 2006-11-10
Can anyone suggest where I might find drivers for the on-board video on my Asrock K7VM2 motherboard?  

The details in my XP system for the Video Card are
Model:   S3 Graphics ProSavageDDR
Driver:  s3gnbm.sys dated 17 August 2006

---

### Post by nereid on 2006-11-10
Normally you don't need an extra driver for your cards. Linux comes with them, the only drivers you may need to install extra are the original drivers for ATI or NVIDIA.

---

### Post by happybill on 2006-11-10
Thanks, that is what I understood.  

However, when I play a solitaire game from those automatically installed, the card movement is horribly jerky. I do not particularly want to play these games but I thought that this poor performance might indicate that the drivers needed attention. 

If the drivers can be assumed to be OK, can anything be done to cure this "defect"?

---

### Post by nereid on 2006-11-10
I'm sorry but I don't know much about your video card, so I can't help you there very much. Maybe there is another driver available, beside the standard driver. Have you searched the web for another driver?

---

### Post by happybill on 2006-11-12
I did search the web.  As far as I can see, i already have the suitable drivers.

---

### Post by nereid on 2006-11-12
Ok, under Windows you have 3d acceleration, haven't you? It would be nice if you could run *glxinfo*. It will display a lot of text about your 3d acceleration and your video card. If a *glxinfo | grep direct* returns "direct rendering: yes" you have 3d acceleration enabled. Maybe you could post the output here.

---

### Post by happybill on 2006-11-13
Hello,

Thanks for your patience.

Running glxinfo produces the following report:-

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group,
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: S3 Graphics Inc.
OpenGL renderer string: Mesa DRI ProSavageDDR 20050829 AGP 1x
OpenGL version string: 1.2 Mesa 6.4.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture,
    GL_ARB_texture_compression, GL_ARB_texture_env_add,
    GL_ARB_texture_mirrored_repeat, GL_ARB_transpose_matrix,
    GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture,
    GL_EXT_draw_range_elements, GL_EXT_histogram, GL_EXT_packed_pixels,
    GL_EXT_polygon_offset, GL_EXT_rescale_normal,
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture,
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_add, GL_EXT_texture_lod_bias, GL_EXT_texture_object,
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_IBM_rasterpos_clip,
    GL_IBM_texture_mirrored_repeat, GL_MESA_window_pos,
    GL_NV_light_max_exponent, GL_NV_texgen_reflection, GL_OES_read_format,
    GL_SGI_color_matrix, GL_SGI_color_table, GL_SGIS_texture_edge_clamp,
    GL_SGIS_texture_lod
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x23 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x24 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x25 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x26 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x27 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x28 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x29 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow

Running glxinfo | grep direct resulted in the answer YES

---

### Post by nereid on 2006-11-14
This is a little bit strange. You've got direct rendering enabled and glxinfo says that your video card is a ProSavage, so far everything looks alright.

Maybe you would like to run glxgears (this is not a benchmark program, but it tells some things about your video card). It could be, that other programs are hogging your resources.

---

### Post by happybill on 2006-11-14
No problem at all with the gears.

The effect is only apparent in the solitaire games.  In Windows, the cards can be dragged quite slowly and the aminations are smooth even when slowed down.  In Ubuntu, the cards flick fron the starting to the ending places, and slow animation is jerky.  I suppose I'll just live with it.  Thanks very much for your help and interest.  On to my next problem.

---


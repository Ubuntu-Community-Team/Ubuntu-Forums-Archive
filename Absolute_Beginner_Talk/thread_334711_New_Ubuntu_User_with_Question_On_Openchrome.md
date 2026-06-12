---
title: "New Ubuntu User with Question On Openchrome"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by DaneDog on 2007-01-09
Hi Everyone,

I posted this question in Multimedia but i didn't recieve any replies, I figured maybe it was in the wrong forum and it was too much of a newb question for that section... Ok basically I bought a cheap (DUMB IDEA) motherboard to be the backbone of my secondary PC which I wanted to experiment with Linux, So i bought a P4M800 but the major problem is it's intergrated Video and it's that horrible VIA TECH/S3G Unichrome card... OMG i wish i would have known this before... 
Started with Mandriva 2007 and I couldn't get it working correctly, Fedora 6.... haha that wouldn't even start after 6 cds... AH!!, xubuntu edgy... I got it working somewhat but was so worried i screwed the linux filesystem up i started over with ubuntu 6.10... OK... Compiled the source, installed the modules, but i'm still getting a wierd error anytime I open a game and use the software renderer or when I run glxinfo...

```
name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x46
display: :0  screen: 0
direct rendering: Yes
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: VIA Technology
OpenGL renderer string: Mesa DRI UniChrome 20060710
OpenGL version string: 1.2 Mesa 6.5.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_transpose_matrix, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_histogram, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array, 
    GL_APPLE_packed_pixels, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texgen_reflection, GL_OES_read_format, 
    GL_SGI_color_matrix, GL_SGI_color_table, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x23 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  0  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x2b 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  0 16 16 16 16  0 0 Slow
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x46 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

The big problem is that 0x46 error "libGL warning: 3D driver claims to not support visual 0x46" is there anyway around this or a way to fix it... video card seems to work fine... but opengl rendering is slow and when i try to software rendering it crashes out with that error... I can't play wolf:et, ut99, or anything else for that fact...


Thanks In Advance,
Dane

---

### Post by DaneDog on 2007-01-09
Sorry to post in my own thread but what is the best driver for me,

Via Technologies Driver
Openchrome
Unichrome

---

### Post by Lord Illidan on 2007-01-09
Personally, having saved the money on so called cheap mobo, I'd buy a nice NVIDIA graphics card. The FX 5200 is a good example of one. It's not going to play very advanced games like Doom 3 or Quake 4, but it will work sufficiently well with games of 4 years ago.

---

### Post by DaneDog on 2007-01-09
I'd prefer just to get the most out of this I can... I have another PC but I only have one monitor and such and no room to have them both up... The other PC has all the goodies but i am still afraid of losing all the info on it... that's why Until i decide for sure that linux is for me i'm trying to test the cabilities of linux... sounds dumb right? i'm kinda wierd like that...

Thanks for the input, it's much appreciated... what driver would work best do you think? I can't figure out how to remove the openchrome driver to try the unichrome driver or ViaTech's driver...

---

### Post by DaneDog on 2007-01-09
I dug up a ATI RAGE PRO TURBO PCI 8mb card... will that work better then the unichrome onboard?

---

### Post by medad on 2007-04-06
I am just wondering what ever happened to your system.  I also have the p4m800 motherboard.  I actually used the guidelines from [https://help.ubuntu.com/community/OpenChrome]("https://help.ubuntu.com/community/OpenChrome") .  After I followed the guidelines, I was able to get 2D/3D working with a crash once in a while on a 3D game..

---

### Post by Domie on 2007-04-22
> **medad said:**
> I am just wondering what ever happened to your system.  I also have the p4m800 motherboard.  I actually used the guidelines from [https://help.ubuntu.com/community/OpenChrome]("https://help.ubuntu.com/community/OpenChrome") .  After I followed the guidelines, I was able to get 2D/3D working with a crash once in a while on a 3D game..

Well, I followed this guide also, but the system freezes when using 3D. Due to the guide, I have to uncomment Load "drm", but now I can't use 3D. This comes by a bug in drm. Is there a solution to fix this?

---


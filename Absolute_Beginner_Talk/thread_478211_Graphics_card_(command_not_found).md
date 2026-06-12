---
title: "Graphics card (command not found)"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by lightfoot on 2007-06-19
Hi all,

I am very new to the Linux scene and really don't know much about computers at all but since switching to Ubuntu I've been inspired to find out what makes these things tick. I have recently installed Ubuntu 7.04 on my Toshiba Tecra T9100.

It's been a steep but fun learning curve and all has been fine and dandy so far. However I was looking into the Beryl package and wanted to find out what graphics card was on my laptop. I typed    **$ lspci **   into terminal and the output said    **bash: $: command not found**    So what am I doing wrong ???

Any help will be greatfully received

Thanks

Lightfoot the Luddite.

---

### Post by viciouslime on 2007-06-19
Don't type the '$'  :) That just shows you are at the prompt. If you look, when you open the terminal, you will see there is already a '$'

---

### Post by Crafty Kisses on 2007-06-19
> **lightfoot said:**
> Hi all,

I am very new to the Linux scene and really don't know much about computers at all but since switching to Ubuntu I've been inspired to find out what makes these things tick. I have recently installed Ubuntu 7.04 on my Toshiba Tecra T9100.

It's been a steep but fun learning curve and all has been fine and dandy so far. However I was looking into the Beryl package and wanted to find out what graphics card was on my laptop. I typed    **$ lspci **   into terminal and the output said    **bash: $: command not found**    So what am I doing wrong ???

Any help will be greatfully received

Thanks

Lightfoot the Luddite.
You might want to try:
```
glxinfo
```
That might say.

---

### Post by lightfoot on 2007-06-19
Thanks for that.

It works fine now.  I was sure it would be something simple (like me !)

Cheers

Lightfoot

---

### Post by fakie_flip on 2007-06-19
try sudo lshw

---

### Post by lightfoot on 2007-06-19
Next question, what dose all this mean and what kind of graphics card do I have ??

tony@tony-laptop:~$ $ lspci
bash: $: command not found
tony@tony-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #3) (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: S3 Inc. SuperSavage IX/C SDR (rev 05)
02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
02:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
02:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)
tony@tony-laptop:~$ 
tony@tony-laptop:~$ glxinfo
name of display: :0.0
libGL error: drmMap of framebuffer failed (Invalid argument)
libGL error: reverting to (slow) indirect rendering
display: :0  screen: 0
direct rendering: No
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
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)
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
0x22 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x23 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x24 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x25 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  8  0  0  0  0  0 0 Slow
0x26 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x27 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  0 16 16 16  0  0 0 Slow
0x28 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x29 16 tc  0 16  0 r  .  .  5  6  5  0  0 16  8 16 16 16  0  0 0 Slow
0x42 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
tony@tony-laptop:~$ 


Sorry I did say I was still learning

Lightfoot the Luddite

---

### Post by fakie_flip on 2007-06-19
01:00.0 VGA compatible controller: S3 Inc. SuperSavage IX/C SDR (rev 05)

That's it.

---

### Post by lightfoot on 2007-06-19
Thanks for that

---

### Post by lightfoot on 2007-06-19
Ok so I have got a 01:00.0 VGA compatible controller: S3 Inc. SuperSavage IX/C SDR (rev 05).

I'm not sure if I have put the right commands in but this what I have got so far and it's all kind of greek to me and I need to do some (lots) more homework.

tony@tony-laptop:~$ glxinfo | grep direct
libGL error: drmMap of framebuffer failed (Invalid argument)
libGL error: reverting to (slow) indirect rendering
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
tony@tony-laptop:~$ fglrxinfo
The program 'fglrxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install xorg-driver-fglrx
Make sure you have the 'restricted' component enabled
bash: fglrxinfo: command not found
tony@tony-laptop:~$ 

Dose this make any sense and what would I have to do next if I wanted to install Beryl ??

Thanks

Lightfoot

---

### Post by Songwind on 2007-06-19
I am not sure if there IS a Beryl-compatible driver for S3 cards.

---

### Post by fakie_flip on 2007-06-19
This thread is a little bit old, but still probably worth checking out.

[http://ubuntuforums.org/showthread.php?t=75393&highlight=VGA+compatible+controller%3A+S3+Inc.+SuperSavage+IX%2FC+SDR+%28rev+05%29](http://ubuntuforums.org/showthread.php?t=75393&highlight=VGA+compatible+controller%3A+S3+Inc.+SuperSavage+IX%2FC+SDR+%28rev+05%29)

Here's some search results with a list of threads with people that have the same graphics card as you. I suggest you read what they said about it and ask them questions.

[http://ubuntuforums.org/search.php?searchid=22360442](http://ubuntuforums.org/search.php?searchid=22360442)

---


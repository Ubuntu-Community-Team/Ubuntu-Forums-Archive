---
title: "New laptop.....slow Ubunutu!"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by reefsrt4 on 2008-04-10
So, I recently got a new laptop with the following hardware:

- Intel® Core 2 Duo Processor T9300 (2x 2.5Ghz)
- Mobility 512MB NVIDIA 8600GT Video
- 2 GB DDR2-667 Memory
- 250GB 5400 rpm S-ATA HDD  (150G for Vista, 100G for Ubuntu - Gutsy)


Now, I also have a laptop with the hardware listed in my sig.  Strangely, the older laptop runs Ubuntu faster than the new one!  On the new one, Vista screams.....loading programs and webpages with amazing speed.  When I boot into Gutsy, everything slows to a crawl....it is seriously confusing.  

Has anybody else, with similar hardware, suffered this type of strange computer behavior?  I'd love to find out if there is something I can do to allow Ubuntu to run as quickly as Vista currently is.  Any ideas?


p.s. - the Gutsy installation is very new.  All I've done is load CCSM so far and set up some 3D effects.

---

### Post by NightwishFan on 2008-04-10
Run these two commands in the terminal:
```
top
```
Just post the top couple process names and their %
```
free -m
```
Post the line called +/- buffers/cache

---

### Post by reefsrt4 on 2008-04-10
PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND   
5825 mike      15   0 57264  34m 9136 S    3  1.7   0:03.60   compiz.real        
 5440 root      15   0 54652  26m 6888 S    2  1.3   0:29.14   Xorg               
 5971 mike      15   0 70624  19m  11m S   2  1.0   0:00.52   gnome-terminal     
 5991 mike      15   0  2368 1164  876 R     0  0.1   0:00.12   top                
       1 root      15   0  2952 1852  532 S     0  0.1   0:01.26   init  



-/+ buffers/cache:        220       1805

---

### Post by NightwishFan on 2008-04-10
There seems to be nothing wrong with your specs, or usage. Well is this slowdown of the gui? Do applications like firefox run fine when they are opened? If even open apps are slow I am not sure of the problem but if it is just gui it may be compiz issue. Try setting effects to none. Also check the live cd for errors to see if you burned it wrong. A slow Linux is quite possibly because of badly burned cd.

---

### Post by reefsrt4 on 2008-04-10
Looks like Compiz is the culprit.  With effects set to none, things are running much faster.

It seems strange that it is running that slow just because of the effects, though.  I thought for sure the hardware would be able to handle it all and not bring the computer to such a slow pace.  Perhaps exploring drivers might get some better performance...

---

### Post by NightwishFan on 2008-04-10
Install the proper drivers for your card and you should be ok. Ubuntu is about as fast as computers can get on my hardware. Well then again I use 64-bit.

---

### Post by medley on 2008-04-10
> **reefsrt4 said:**
> Looks like Compiz is the culprit.  With effects set to none, things are running much faster.

It seems strange that it is running that slow just because of the effects, though.  I thought for sure the hardware would be able to handle it all and not bring the computer to such a slow pace.  Perhaps exploring drivers might get some better performance...

It sounds to me like a GL problem. What do you get when you type 'glxinfo' at the console? Also, if, without compiz running, you select one of the 3d screen savers in system settings, does it running smoothly? I'm just guessing probably not. If not, this says that your graphics driver is not running in accelerated 3d mode.

---

### Post by reefsrt4 on 2008-04-10
So, since I last posted I did some searching here concerning my gfx card.  I ended up loading envy and using it to automatically install drivers and update xorg.conf, etc...

well, now it is more eff'd up than ever.  pop up windows claiming gnome couldn't start correctly....

So, should I just reinstall Gutsy from scratch again or is there a way I can reverse this Envy created mess?  What driver should I be running with this card?



edit - I meant to say gnome settings daemon that wouldn't start.

---

### Post by NightwishFan on 2008-04-10
edit: i need to learn to read...

---

### Post by reefsrt4 on 2008-04-10
My video card:  - Mobility 512MB NVIDIA 8600GT Video

512Mb of memory, yes?

---

### Post by NightwishFan on 2008-04-10
I thought you meant the one in the sig. Try the restricted drivers manager, it is installed with gutsy by default. It will install the correct driver if it exists. My mistake. Reading skills are lost with age.. Also search for a thread on your card for help.

---

### Post by reefsrt4 on 2008-04-10
I did search, since your 2nd post and found something about Envy.  I used it and things got worse.....as far as the theme that loaded and the issue with gnome setting daemon not starting.

Trying to figure out if I can reverse that or if I need to do a complete ubuntu reinstall.

---

### Post by NightwishFan on 2008-04-10
Ok I am not on gnome so it is a bit hard ill try to search on the issue as well.

---

### Post by reefsrt4 on 2008-04-10
I restarted X and everything seems better now.  wondering if i will be seeing that gnome settings error again in teh future though.  We'll see.

---

### Post by NightwishFan on 2008-04-10
I see.  If it works now I doubt you will have problems in the future. When dealing with graphics hardware you should reboot after you update it for the changes to take effect. I am sorry for my inability to be of more direct help to the problem.

---

### Post by drascus on 2008-04-10
The problem is almost surely the Nvidia card. I have an Nvidia card in my laptop and it runs weird on battery power sometimes. With the proper driver it should run no problem.

---

### Post by reefsrt4 on 2008-04-10
So, exactly what is the "proper" driver then?

---

### Post by NightwishFan on 2008-04-10
Like I said try the restricted driver manager if you have not already. Envy should work but as you saw it comes up with errors. Post the output of this command.
```
glxgears
```

---

### Post by reefsrt4 on 2008-04-10
I tried the restricted drivers first.  Here's the output:

21334 frames in 5.0 seconds = 4266.770 FPS
X connection to :0.0 broken (explicit kill or server shutdown).

---

### Post by NightwishFan on 2008-04-10
You should be able to run compiz no problem your card seems to have opengl support and is absurdly fast. Mine is 1/4 that speed I believe.

Try extra effects again.

---

### Post by reefsrt4 on 2008-04-11
it runs compiz.  the problem is it is slow.  for example the burn effect and magic lamp will hang for a couple seconds at the very beginning and then the effect will take place....but slowly.  With my hardware, I just don't get why it does that.  if it is driver caused....I am dying to find out what driver i should have here.  haha

---

### Post by NightwishFan on 2008-04-11
=/ Yeah I do not see any reason why it should I forget that command to see if you have direct rendering. I will seek it out. Await my return.

edit: found
```
glxinfo
```
should perhaps be 3rd line down.

---

### Post by reefsrt4 on 2008-04-11
```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_framebuffer_sRGB
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_EXT_framebuffer_sRGB, 
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 8600M GT/PCI/SSE2
OpenGL version string: 2.1.2 NVIDIA 169.12
OpenGL extensions:
    GL_ARB_color_buffer_float, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_half_float_pixel, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_S3_s3tc, GL_EXT_texture_env_add, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_Cg_shader, GL_EXT_bindable_uniform, GL_EXT_depth_bounds_test, 
    GL_EXT_draw_buffers2, GL_EXT_draw_instanced, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_object, GL_EXTX_framebuffer_mixed_formats, 
    GL_EXT_framebuffer_sRGB, GL_EXT_geometry_shader4, 
    GL_EXT_gpu_program_parameters, GL_EXT_gpu_shader4, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_float, GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_array, GL_EXT_texture_buffer_object, 
    GL_EXT_texture_compression_latc, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_integer, GL_EXT_texture_lod, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object, GL_EXT_texture_sRGB, 
    GL_EXT_texture_shared_exponent, GL_EXT_timer_query, GL_EXT_vertex_array, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_KTX_buffer_region, GL_NV_blend_square, GL_NV_copy_depth_to_color, 
    GL_NV_depth_buffer_float, GL_NV_conditional_render, GL_NV_depth_clamp, 
    GL_NV_fence, GL_NV_float_buffer, GL_NV_fog_distance, 
    GL_NV_fragment_program, GL_NV_fragment_program_option, 
    GL_NV_fragment_program2, GL_NV_framebuffer_multisample_coverage, 
    GL_NV_geometry_shader4, GL_NV_gpu_program4, GL_NV_half_float, 
    GL_NV_light_max_exponent, GL_NV_multisample_coverage, 
    GL_NV_multisample_filter_hint, GL_NV_occlusion_query, 
    GL_NV_packed_depth_stencil, GL_NV_parameter_buffer_object, 
    GL_NV_pixel_data_range, GL_NV_point_sprite, GL_NV_primitive_restart, 
    GL_NV_register_combiners, GL_NV_register_combiners2, 
    GL_NV_texgen_reflection, GL_NV_texture_compression_vtc, 
    GL_NV_texture_env_combine4, GL_NV_texture_expand_normal, 
    GL_NV_texture_rectangle, GL_NV_texture_shader, GL_NV_texture_shader2, 
    GL_NV_texture_shader3, GL_NV_transform_feedback, GL_NV_vertex_array_range, 
    GL_NV_vertex_array_range2, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_NV_vertex_program2, GL_NV_vertex_program2_option, 
    GL_NV_vertex_program3, GL_NVX_conditional_render, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow, 
    GL_SUN_slice_accum

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x30 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x31 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x32 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x33 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x35 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x37 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x38 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x39 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x3a 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x3b 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x3d 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x3f 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x40 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x41 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x42 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x43 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x44 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x45 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x46 24 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x47 24 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x48 24 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x49 24 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x4a 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x4c 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x4e 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x4f 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x50 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x51 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x52 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x54 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x56 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x57 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x58 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x59 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x23 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x5a 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x5b 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x5c 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x5d 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x5e 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x5f 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x60 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x61 32 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x62 32 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x63 32 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x64 32 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x65 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x66 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x67 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x68 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x69 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x6a 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x6b 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x6c 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x6d 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x6e 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x6f 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x70 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x71 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x72 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x73 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x74 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon

```

---

### Post by NightwishFan on 2008-04-11
Everything checks out. When those effects happen do they take a lot of cpu usage? Perhaps try resetting all the compiz settings to default.

---

### Post by reefsrt4 on 2008-04-11
during the hanging or slow movement, CPU goes to 50%.

---

### Post by NightwishFan on 2008-04-11
That is odd as it should rely on your gpu. Did you disable the restricted driver before you used envy that may have been the problem.

---


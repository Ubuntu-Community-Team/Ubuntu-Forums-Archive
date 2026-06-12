---
title: "Colors are weird"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by dooey100 on 2008-04-02
Hey, I'm getting a stracge color problem with Ubuntu, the colors are all different, but not in a pattern, black is still black, and white is still white, but orange is green, shades are grey are mixed up, green is blue, etc.

The problem doesn't happen right when I start up, but when I run Wings3D, (a free modeling software)

A search showed that I can fix this with a hotkey Super+M which doesn't do anything. (Apparently I need a program called compiz) So does anyone know whats causing this? My laptop specs are:

1.7 Ghz Dual Core CPU
ATI mobility radeon 2600
2 gigs ram + 1 gig turbo ram

I tried updating drivers, didn't help.

---

### Post by Crafty Kisses on 2008-04-02
First, what kind of Monitor do you have? 

Secondly make sure your Monitor is connected good, sometimes when it's loose the same symptoms will happen.

Thirdly, have you checked your settings on your Monitor?

---

### Post by dooey100 on 2008-04-02
The monitor came with the laptop so I don't know what kind it is (I remember seeing somewhere that it is a generic PnP moniter). Hopefully it's not a loose connection, that would probably need repairs.

Where do you change monitor settings in Ubuntu? I looked under system>preferences and didn't see anything obvious.

---

### Post by Crafty Kisses on 2008-04-02
> **dooey100 said:**
> The monitor came with the laptop so I don't know what kind it is (I remember seeing somewhere that it is a generic PnP moniter). Hopefully it's not a loose connection, that would probably need repairs.

Where do you change monitor settings in Ubuntu? I looked under system>preferences and didn't see anything obvious.

Ohhh, this is a laptop Monitor, is it possible, you don't have your Drivers enabled for your Video chipset?

---

### Post by dooey100 on 2008-04-02
Haha, probably.

I only use Ubuntu for Wings3D (It doesn't work in windows Vista) And until now its been fine because I can still work it just looks weird. But now I need to use some pictures as references, which doesn't work so well.

Anyway, a quick google search didn't reveal how to enable drivers. I don't suppose you could tell me? Much appreciated.

---

### Post by Crafty Kisses on 2008-04-02
> **dooey100 said:**
> Haha, probably.

I only use Ubuntu for Wings3D (It doesn't work in windows Vista) And until now its been fine because I can still work it just looks weird. But now I need to use some pictures as references, which doesn't work so well.

Anyway, a quick google search didn't reveal how to enable drivers. I don't suppose you could tell me? Much appreciated.

Yeah sure, do the following, **System<Administration<Restricted Drivers Manager** after you do that, enter your password, and tell me what you see.

---

### Post by dooey100 on 2008-04-04
It says my hardware doesn't require any resticted drivers.

Sorry for the dalay. I really appreciate the help.

---

### Post by dooey100 on 2008-04-04
Just tried it with Fedora. Same problem.

---

### Post by dooey100 on 2008-04-04
So the problem seems to happen only when I use OpenGL, it only starts when I start orbiting the camera.

This probably means its a video card issue, if that helps at all.

---

### Post by Crafty Kisses on 2008-04-04
> **dooey100 said:**
> So the problem seems to happen only when I use OpenGL, it only starts when I start orbiting the camera.

This probably means its a video card issue, if that helps at all.
Post the following output:
```
glxinfo
```

---

### Post by dooey100 on 2008-04-04
Output before the colors changed:




drew@drew-laptop:~$ glxinfo

name of display: :0.0

display: :0  
screen: 0

direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

server glx vendor string: SGI
server 
glx version string: 1.2
server 
glx extensions:
    GLX_ARB_multisample, 
GLX_EXT_visual_info, 
GLX_EXT_visual_rating, 
    
GLX_EXT_import_context, 
GLX_EXT_texture_from_pixmap, 
GLX_OML_swap_method, 
    
GLX_SGI_make_current_read, 
GLX_SGIS_multisample, 
GLX_SGIX_hyperpipe, 
    
GLX_SGIX_swap_barrier, 
GLX_SGIX_fbconfig, 
GLX_MESA_copy_sub_buffer
client 
glx vendor string: SGI
client 
glx version string: 1.4

client glx extensions:
    GLX_ARB_get_proc_address, 
GLX_ARB_multisample, 
GLX_EXT_import_context, 
    
GLX_EXT_visual_info, 
GLX_EXT_visual_rating, 
GLX_MESA_allocate_memory, 
    
GLX_MESA_copy_sub_buffer, 
GLX_MESA_swap_control, 
    
GLX_MESA_swap_frame_usage, 
GLX_OML_swap_method, 
GLX_OML_sync_control, 
    
GLX_SGI_make_current_read, 
GLX_SGI_swap_control, 
GLX_SGI_video_sync, 
    
GLX_SGIS_multisample, 
GLX_SGIX_fbconfig, 
GLX_SGIX_pbuffer, 
    
GLX_SGIX_visual_select_group, 
GLX_EXT_texture_from_pixmap

GLX version: 1.2

GLX extensions:
    
GLX_ARB_get_proc_address, 
GLX_ARB_multisample, 
GLX_EXT_import_context, 
    
GLX_EXT_visual_info, 
GLX_EXT_visual_rating, 
GLX_MESA_copy_sub_buffer, 
    
GLX_OML_swap_method, 
GLX_SGI_make_current_read, 
GLX_SGIS_multisample, 
    
GLX_SGIX_fbconfig, 
GLX_EXT_texture_from_pixmap

OpenGL vendor string: Mesa 
project: [www.mesa3d.org](www.mesa3d.org)
OpenGL 
renderer string: Mesa GLX Indirect
OpenGL 
version string: 1.4 (2.1 Mesa 7.0.1)

OpenGL extensions:
    
GL_ARB_depth_texture, 
GL_ARB_draw_buffers, 
GL_ARB_fragment_program, 
    
GL_ARB_imaging, 
GL_ARB_multisample, 
GL_ARB_multitexture, 
    
GL_ARB_occlusion_query, 
GL_ARB_point_parameters, 
GL_ARB_point_sprite, 
    
GL_ARB_shadow, 
GL_ARB_shadow_ambient, 
GL_ARB_texture_border_clamp, 
   
GL_ARB_texture_compression, 
GL_ARB_texture_cube_map, 
    
GL_ARB_texture_env_add, 
GL_ARB_texture_env_combine, 
    
GL_ARB_texture_env_crossbar, 
GL_ARB_texture_env_dot3, 
    
GL_ARB_texture_mirrored_repeat, 
GL_ARB_texture_non_power_of_two, 
    
GL_ARB_texture_rectangle, 
GL_ARB_transpose_matrix, 
GL_ARB_vertex_program, 
    
GL_ARB_window_pos, 
GL_EXT_abgr, 
GL_EXT_bgra, 
GL_EXT_blend_color, 
    
GL_EXT_blend_equation_separate, 
GL_EXT_blend_func_separate, 
    
GL_EXT_blend_logic_op, 
GL_EXT_blend_minmax, 
GL_EXT_blend_subtract, 
    
GL_EXT_clip_volume_hint, 
GL_EXT_copy_texture, 
GL_EXT_draw_range_elements, 
    
GL_EXT_fog_coord, 
GL_EXT_framebuffer_object, 
GL_EXT_multi_draw_arrays, 
    
GL_EXT_packed_pixels, 
GL_EXT_paletted_texture, 
GL_EXT_point_parameters, 
    
GL_EXT_polygon_offset, 
GL_EXT_rescale_normal, 
GL_EXT_secondary_color, 
    
GL_EXT_separate_specular_color, 
GL_EXT_shadow_funcs, 
    
GL_EXT_shared_texture_palette, 
GL_EXT_stencil_wrap, 
GL_EXT_subtexture, 
    
GL_EXT_texture, 
GL_EXT_texture3D, 
GL_EXT_texture_edge_clamp, 
    
GL_EXT_texture_env_add, 
GL_EXT_texture_env_combine, 
    
GL_EXT_texture_env_dot3, 
GL_EXT_texture_lod_bias, 
    
GL_EXT_texture_mirror_clamp, 
GL_EXT_texture_object, 
    
GL_EXT_texture_rectangle, 
GL_EXT_vertex_array, 
GL_APPLE_packed_pixels, 
    
GL_ATI_draw_buffers, 
GL_ATI_texture_env_combine3, 
    
GL_ATI_texture_mirror_once, 
GL_ATIX_texture_env_combine3, 
    
GL_IBM_texture_mirrored_repeat, 
GL_INGR_blend_func_separate, 
    
GL_MESA_pack_invert, 
GL_MESA_ycbcr_texture, 
GL_NV_blend_square, 
    
GL_NV_fragment_program, 
GL_NV_light_max_exponent, 
GL_NV_point_sprite, 
    
GL_NV_texgen_reflection, 
GL_NV_texture_rectangle, 
GL_NV_vertex_program, 
    
GL_NV_vertex_program1_1, 
GL_SGI_color_matrix, 
GL_SGI_color_table, 
    
GL_SGIS_generate_mipmap, 
GL_SGIS_texture_border_clamp, 
    
GL_SGIS_texture_edge_clamp, 
GL_SGIS_texture_lod, 
GL_SGIX_depth_texture, 
    
GL_SGIX_shadow, 
GL_SGIX_shadow_ambient, 
GL_SUN_multi_draw_arrays

   
visual  x  bf lv rg d st 
colorbuffer ax dp st 
accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b 
eat
----------------------------------------------------------------------

0x22 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 
None
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 
None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 
None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 
None
0x3d 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 
Ncon
drew@drew-laptop:~$ 

This isn't the same formatting from the terminal, but ubuntu won't recognize my wireless card, so I have to reboot in vista to post anything, which deletes all the line breaks. I think i did alright, putting them back though.

The output was the same before and after the colors change.

Also: if it hasn't already, the colors will change when I shut down. I had never actually shutdown without using wings before so I never noticed that.


Edit: Direct Rendering seems to be off, mabey thats it? I'll see if I can turn it on, and if it helps.

---


---
title: "3D acceleration not enabled ??"
date: 2007-12-04
forum: Apple Intel Users
---

### Post by Zaff on 2007-12-04
hey guys, I'm using Gutsy on a macbook intel first Gen (the one the wiki works perfectly for). Now this issue isn't exactly vital as this is a work station more than anything else but I tried launching Xmoto and some other apps and it seems the 3D acceleration isn't enabled. If I try to enable the Desktop Visual effects metacity gets reloaded and then I get a dialog saying the Desktop effect could not be enabled.
Is there something I need to do to enable this ? I'm not trying to install compiz as I'm using a dual screen and I know it's probably a bad idea to mix the two, but it would be cool to be able to play physical neverball (I wanna show off to people who think linux is just not as good as mac os...)
Any help on this will be highly appreciated.
Thanks

---

### Post by Rog-Mahal on 2007-12-04
can you post the output of the following command:

```
glxinfo
```

---

### Post by Zaff on 2007-12-04
Yep , here it is :
Thanks for the help
```
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
OpenGL vendor string: Mesa project: www.mesa3d.org
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
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x5e 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
```
Im guessing it has something to do with the direct rendering being : No.
How do  change that ???

---

### Post by cyberdork33 on 2007-12-04
See the line:
```

direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
```

---

### Post by Zaff on 2007-12-04
> **cyberdork33 said:**
> See the line:
```

direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
```

taking the risk to look stupid here but : how do I do that ? (setting LIBGL_DEBUG=verbose).

---

### Post by cyberdork33 on 2007-12-04
> **Zaff said:**
> taking the risk to look stupid here but : how do I do that ? (setting LIBGL_DEBUG=verbose).I am assuming it is a 'system variable'. You set system variables from the commandline like so:
```
export VARIABLE=value
```so you want:
```
[SIZE=-1]export **LIBGL_DEBUG**=verbose[/SIZE]
```
You will probably have to restart xorg to reload the libraries.

---

### Post by Zaff on 2007-12-05
Ok so that didn't work but I just remember that I commented out this :
Load "DRI" 
in xorg.conf
This is probably the cause.
However I also remeber being told to do so because it would mess up my dual screen setup (I use xrandr everytime I start my macbook). Is this still true ?
in other words : Will enable DRI enable 3D acceleration and will it mess up the dual screen display ?
Do I need to disable it every time I use dual screen ?
thanks

---

### Post by cyberdork33 on 2007-12-05
> **Zaff said:**
> Ok so that didn't work but I just remember that I commented out this :
Load "DRI" 
in xorg.conf
This is probably the cause.
However I also remeber being told to do so because it would mess up my dual screen setup (I use xrandr everytime I start my macbook). Is this still true ?
in other words : Will enable DRI enable 3D acceleration and will it mess up the dual screen display ?
Do I need to disable it every time I use dual screen ?
thanks

Not that hard to try...

---

### Post by Zaff on 2007-12-05
So I uncommented that line and it still says direct rendering : no. I tried export LIBGL_DEBUG=verbose, restarted X and when it came back online the LIBGL_DEBUG was empty again so I can't get more precisions from glxinfo.
Anyway I could get that environment variable to stay set ?

---

### Post by cyberdork33 on 2007-12-05
what does fglrxinfo say?

---

### Post by Zaff on 2007-12-06
> what does fglrxinfo say?

I don't have fglrxinfo, this is an integrated intel chipset (MacoBook, the white version, not macbook pro), not an ATI video card so I didn't think I needed it. Do I ?

---

### Post by Rog-Mahal on 2007-12-06
Depends, if you got the new Macbook with the Santa Rosa chipset, I believe you have and ati card. If you didn't get the newest one, then you have an intel card.

---

### Post by cyberdork33 on 2007-12-06
no sorry.. .I thought this was an ATI issue (which something like this would normally be).

If you are using the Intel driver then I really can't debug much more. You might try in one of the other forums since this issue shouldn't a mac specific thing. I looked at what the verbose output looks like, and it wasn't very helpful to me.

---

### Post by Zaff on 2007-12-07
> **cyberdork33 said:**
> no sorry.. .I thought this was an ATI issue (which something like this would normally be).

If you are using the Intel driver then I really can't debug much more. You might try in one of the other forums since this issue shouldn't a mac specific thing. I looked at what the verbose output looks like, and it wasn't very helpful to me.

Ok I'll do that. Thanks anyway.

---


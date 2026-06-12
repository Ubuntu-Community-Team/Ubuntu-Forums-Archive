---
title: "Bug??????"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by superjdf on 2007-08-25
I am having a problem, with ubuntu 6.06!

Ok, what happens? What happens is the screen locks up with multi-colored usually colors from the page I was looking at, pixil smudging type patterens. Its kind of hard to explain. But its like slanting lines almost.

At first this happened only when searching the internet, then a few minutes ago it happened when using gimp.

Its starting to get really frustrating. I have installed all of the updates from the update manager. 

Does this problem sound familar to anyone. I am pretty sure almost one hundred percent that this is an OS problem. All I am running is ubuntu 6.06. I guess I should include my specs.

Biostar geforce 6100-m9
amd dual-core 2.2ghz
1gig ddr4
160 gB HDD sata2
sata2 lightscrib samsung dvd-rw

---

### Post by southernman on 2007-08-25
What type of video adapter are you using? Onboard, PCI, AGP

What brand if it's a plugin video card?

It sounds as if either your video is dying or not using the proper driver... more the dying than not.

---

### Post by superjdf on 2007-08-25
Onboard geforce 6100 
I am using a wireless adapter by linksys a wusb54g, I thought that might be apart of it but now I am not sure????

I know that it is completly random when it happens. And it didnt start until I was searching the web.

I just recently hooked that adapter up.

---

### Post by mysticmatrix on 2007-08-25
Have you installed the Nvidia driver?
If you are not sure, post output of this command.
Go to Applications --> Acessories --> Terminal and type
```

glxinfo
```

---

### Post by superjdf on 2007-08-25
jared@jared-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
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
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_visual_select_group
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_imaging, GL_ARB_multitexture,
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow,
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_window_pos,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate,
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements,
    GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels,
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap,
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle,
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_ATI_texture_env_combine3,
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3,
    GL_HP_occlusion_test, GL_IBM_texture_mirrored_repeat,
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture,
    GL_NV_blend_square, GL_NV_point_sprite, GL_NV_texgen_reflection,
    GL_NV_texture_rectangle, GL_SGIS_generate_mipmap,
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp,
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow,
    GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x22 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
jared@jared-desktop:~$

---

### Post by superjdf on 2007-08-25
How would I install driver if its not there???

---

### Post by mysticmatrix on 2007-08-25
You don't have your correct drivers installed. To install the drivers, refer here
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by superjdf on 2007-08-25
OK I installed all the nvidia drivers ubuntu has to offer for 6.10 and earlier!!!! I am now restarting my pc and after a couple of hours, e.g. I have to leave for a little while, I will check it out and post the results!!

I hope that fixes the problemo!! 

Anyway thanx for your help mystic I really appreciate it!!

Jared

---

### Post by asmoore82 on 2007-08-25
> **mysticmatrix said:**
> You don't have your correct drivers installed. To install the drivers, refer here
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

about the sig ...

I would say don't try to run any real game on any non(ATI or nVidia) card, regardless of OS.
That's quite a hefty rig not to have a, for lack of a better word, real video card.

---

### Post by superjdf on 2007-08-25
Ok its still doing it???????

When I restart I see a flash of the page it screwed up on??? When it kicks on to the log in page I mean???

It doesnt seem to do it when I am on here though, weird???

I am totally at a loss for whats going on??:mad:

---

### Post by mysticmatrix on 2007-08-27
> **asmoore82 said:**
> about the sig ...

I would say don't try to run any real game on any non(ATI or nVidia) card, regardless of OS.
That's quite a hefty rig not to have a, for lack of a better word, real video card.

Ok if you read the thread carefully, I am able to run Far Cry and CS Source and more at fairly playable speed(under Windows, that is). Most games made for linux are also fine. Problem is with WIne gaming, and I don't know who's responsible.( Like I'm not getting to run even Counter Strike 1.6, something running even on Geforce 4 under wine. Man that sucks!!)

---


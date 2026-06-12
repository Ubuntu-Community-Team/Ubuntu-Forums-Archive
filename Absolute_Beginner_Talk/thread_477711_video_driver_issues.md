---
title: "video driver issues"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by ITdrummer on 2007-06-18
Hello,
I have a clean install of Ubuntu version 7.04. I am not sure if my video driver is installed or working correctly. I have found several threads in the forum pertaining to ATI/NVIDIA graphics cards, but i dont have either of these types.  Where can i find support/drivers about intel integrated graphics cards?

---

### Post by nitro_n2o on 2007-06-18
well.. if you see the screen and the resolution is fine.. then the card works.. unless you need some specific feature and you can't figure out a way of making it work?

---

### Post by ITdrummer on 2007-06-18
well is there a command i can enter to find out if my display driver is working correctly?

---

### Post by Kubunteando on 2007-06-19
Do you see any problems in the Graphical interface?

Do you mean if you have OpenGL HW acceleration to execute 3D applications and games?

If so, post the out put of "glxinfo", and check if you have "Direct Rendering" as "Yes",

---

### Post by Crafty Kisses on 2007-06-19
> **ITdrummer said:**
> Hello,
I have a clean install of Ubuntu version 7.04. I am not sure if my video driver is installed or working correctly. I have found several threads in the forum pertaining to ATI/NVIDIA graphics cards, but i dont have either of these types.  Where can i find support/drivers about intel integrated graphics cards?

You should go into terminal and type:
```
glxinfo
```
You should look for the "direct rendering" and if you have that, it's working properly.

---

### Post by ITdrummer on 2007-06-25
my direct rendering is "no" how do i fix that

---

### Post by w4ett on 2007-06-25
Please post your:

glxinfo 

and 

xorg.conf

---

### Post by ITdrummer on 2007-06-25
how do i get to xorg.conf?

---

### Post by ITdrummer on 2007-06-25
This is the result of :$ glxinfo

> :~$ glxinfo
name of display: :0.0
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
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x43 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon


---

### Post by w4ett on 2007-06-26
From the terminal command prompt type:

lspci

Copy and paste the result...this will tell us the video card and chipset you are using
the also from the command prompt type:

sudo gedit /etc/X11/xorg.conf

Copy and paste the result...this will tell us the video driver installed and how it's set to operate.

We need this info to correct your problems.

---

### Post by ITdrummer on 2007-06-26
Thanks so much for explaining it to me in detail. As i previously stated (in both threads, lol) i am new to linux/ubuntu and i am still learning the terminology and common commands (xorg.conf). I will do what was suggested as soon as i get home from work. Thank you

---

### Post by ITdrummer on 2007-06-27
this is the result of my lspci:


00:00.0 Host bridge: Intel Corporation 82810 DC-100 GMCH [Graphics Memory Controller Hub] (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810 DC-100 CGC [Chipset Graphics Controller] (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02)
01:07.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
01:07.1 Input device controller: Creative Labs SB Live! Game Port (rev 08)
01:0c.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)

---

### Post by w4ett on 2007-06-27
I think you should be using the i810 driver for that chipset.

sudo apt-get install xserver-xorg-video-i810

then

sudo dpkg-reconfigure xserver-xorg

---

### Post by ITdrummer on 2007-06-27
When i typed into the terminal:

sudo gedit /etc/X11/xorg.conf

It opened up a nautilus window with the contents of the xorg.conf folder, but it was empty.......any sugestions?

---


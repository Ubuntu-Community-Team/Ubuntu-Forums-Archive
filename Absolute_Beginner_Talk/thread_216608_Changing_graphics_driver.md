---
title: "Changing graphics driver"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by BarFly on 2006-07-15
Hello.  I've been using the VESA drivers for VIA S3 Unichrome integrated graphics for K8M800.  Dapper Drake has a VIA driver for it, so I would like to use it.  I am scared to mess around with the xorg.conf file, though, not wanting to boot into a blank screen or some other nightmare.  I have Dapper Drake up to date.

This is what I propose doing (I already created a backup of xorg.conf called xorg.conf.bak):

sudo vi /etc/X11/xorg.conf (password)

Make the following changes:

Section "Device"
	Identifier	"VIA Unichrome Pro"
	Driver		"via"
	BusID		"PCI:1:0:0"
	Option		"EnableAGPDMA"
	Option		"DisableIRQ"
EndSection

Save it and reboot.  Again, I am frightened to mess with the video and would appreciate some advice.  Thanks.

---

### Post by ahaslam on 2006-07-15
> **BarFly said:**
> Hello.  I've been using the VESA drivers for VIA S3 Unichrome integrated graphics for K8M800.  Dapper Drake has a VIA driver for it, so I would like to use it.  I am scared to mess around with the xorg.conf file, though, not wanting to boot into a blank screen or some other nightmare.  I have Dapper Drake up to date.

This is what I propose doing (I already created a backup of xorg.conf called xorg.conf.bak):

sudo vi /etc/X11/xorg.conf (password)

Make the following changes:

Section "Device"
	Identifier	"VIA Unichrome Pro"
	Driver		"via"
	BusID		"PCI:1:0:0"
	Option		"EnableAGPDMA"
	Option		"DisableIRQ"
EndSection

Save it and reboot.  Again, I am frightened to mess with the video and would appreciate some advice.  Thanks.

That will work. You don't have to change the identifier though, if you do you'll need to ensure tha the 'device' name under the 'screen' section is the same.

If you do encounter problems (you shouldn't, I have the same chipset), boot in recovery mode and use, "sudo nano /etc/X11/xorg.conf" to change back to vesa.

I hope that helps.

Tony.

---

### Post by BarFly on 2006-07-15
Thank you, Tony.  I had to use "sudo gedit" instead of "vi" though.  I don't know why as I don't really understand Linux or the commands.  All seems to be well, though.  VESA was really getting on my nerves, but I was too scared to do anything about it.

---

### Post by ahaslam on 2006-07-17
No worries mate. I realise how fustrating the vesa drivers are, I couldn't get it to work with Breezy. 

One tip though, avoid the 'antspotlight' screensaver (and a couple of others). It causes my system to lock.


Tony.

---

### Post by BarFly on 2006-07-17
Yup, after playing some vids, I checked out the screensavers.  Antspotlight froze it.  Whatever, I can do without a screensaver (used blank screen before).

The Via driver needs some work.  I am not much of a gamer or a graphics artist, so I can live without.  If I were either, I would invest in a graphics card.  Coincidentally, my parent's computer broke right after I installed the Via driver (either mobo or BIOS).  I am sharing mine with them now.  Yes, I live with my parents, but not in the basement!  It is because my father is handicapped and needs help.  Back to the story, my mom, mum to you, likes playing solitaire.  The Via driver made every card move take 4 seconds.  I switched back to the VESA driver so she can play her game.

I have Atunnel as the ss now as it seems to work well with the VESA driver.

---

### Post by ahaslam on 2006-07-17
It's rather unusual that the vesa driver offers better performance to the via one. Did you have direct rendering with the via driver? Type **glxinfo** in a terminal, you're looking for *direct rendering: Yes*. I also found that my frame rate doubled with the via driver. To check try **glxgears -printfps** at the terminal.

If you don't have direct rendering, you my want to try the openchrome drivers.


Tony.

---

### Post by BarFly on 2006-07-18
943 frames in 5.2 seconds = 180.162 FPS
1026 frames in 5.3 seconds = 193.534 FPS
1026 frames in 5.3 seconds = 193.342 FPS
X connection to :0.0 broken (explicit kill or server shutdown).
(Showed 3 gears moving slowly).

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
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
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
(This is all with the VESA driver).

---

### Post by BarFly on 2006-07-18
I take it that I have to enable direct rendering.  How?  Thank you so much for having patience with me.

---

### Post by BarFly on 2006-07-18
It is now late in Chicago and a storm is upon us.  I need to unplug the computer and go to bed.  I had lightning wipe out everything a few years ago.  That is not going to happen this time.

---

### Post by ahaslam on 2006-07-18
If you do the same using the via driver, you should see your FPS double and direct rendering: Yes. 
This should give better performance in all situations as it takes the strain away from your processor (unless a screensaver or 3D game crashes it). ;)

I'll be trying out the openchrome drivers in a couple of days, I'll let you know if they're any better (might even write a how-to).


Tony.

---

### Post by ahaslam on 2006-07-19
I have compiled & installed the OpenChrome drivers and performance & stability have not changed. Still 421fps and 'AntSpotlight' crashes my system. This process was not easy and took me a couple of hours. I don't recommend it if the existing 'via' driver works with Direct Rendering - do the previous checks while using the via driver.

Tony.

---


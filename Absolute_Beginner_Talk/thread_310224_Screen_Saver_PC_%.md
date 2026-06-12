---
title: "Screen Saver PC %"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by aznlnx on 2006-11-30
I have been using Ubuntu for about 3 months now and I just love it. However, one stupid thing is happening that I'm wondering is happening to other users.

I have my screen saver enabled but the screen saver doesnt move smoothly...
I also noticed its using a fairly high amount of processing.

Any reason why? Can someone help me out?

Thanks fellas ;)

---

### Post by styracosaurus on 2006-11-30
Which screen saver is it? Some of the fancy OpenGL ones need acceleration I think. Do you have hardware acceleration?

---

### Post by aznlnx on 2006-12-01
I"m not certain. I"m guessing the ones that came standard with Ubuntu.

How would I determine I have hardware acceleration?

THanks :)

---

### Post by RMorris78 on 2006-12-01
run "glx-info" from the terminal and post the output. Do you know if you have installed video card drivers or played with xorg.conf?

---

### Post by RAOF on 2006-12-01
The above command should actually be
```
glxinfo
```

---

### Post by RMorris78 on 2006-12-01
whoops i wasnt thinking there

excuse the brain fart

---

### Post by aznlnx on 2006-12-01
OK now what? Hehe 

I hav an Nvidia card and I don't remember installing a video driver. It just worked with ubuntu. The way I like things to work.

PLUG AND PLAY BABY! HEHE
___________________________________________________________________________
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
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  0 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  0 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  0 0 None

---

### Post by Pjotr123 on 2006-12-01
I advice strongly to install and activate the closed source driver from Nvidia. Much better performance than the open source driver, especially in 3D. A lot of screensavers are 3D, by the way. If you have the right sources in your sources.list, then you can install it with Synaptic.

I myself also have an Nvidia card and am using the closed source driver. Does an excellent job.

Greeting, Pjotr.

---

### Post by aznlnx on 2006-12-01
ok thanks...but ehm..how would you begin doing so?

Hehe

Synaptic Manager?

search for nvidia and closed driver?

THanks

---

### Post by RAOF on 2006-12-01
From Synaptic you are after the "nvidia-glx" package.  The open-source **nv** drivers that you're currently using sadly don't support 3d acceleration, so your OpenGL screensavers are just using the processor :)

From a terminal, you want to
```
sudo apt-get install nvidia-glx
sudo nvidia-xconfig
```

The first line installs the driver, the second line uses the nvidia configuration tool to tell the GUI to use the new driver.  The next time you restart, it will then be using the nVidia driver.

---

### Post by aznlnx on 2006-12-04
**RAOF** 

Thank you. That worked great 

But now there is a second problem. THis nvidia card is a dual card. One goes to my 1080i Samsung LCD TV and the other card goes to my Dell 2007 FP which resolution was at 1600x1200.

Now I can't even see the screen on my Dell. I have to turn on my 1080i on to run UBUNTU.

THat driver I installed got my screen saver working but now I can't use my original monitor.

The resolution can only do 1024 x 768.

What do I do now? LOL! :(

Install another driver?

---

### Post by aznlnx on 2006-12-04
oh and yes of course I switched the cable to see if the Dell would work and nothing :(

What gives? I need a damn driver to use the DELL monitor? LOL!

Well thanks for the help now I need to solve this next issue.

Thanks again :)

---

### Post by RAOF on 2006-12-05
Hm.  If you just unplug the TV and leave just the Dell plugged in, does it work in anything but 1024x768?

I'm in no way an expert on dual-head and the nVidia drivers.  There's probably an option you can pass (in xorg.conf) to select which is the primary display, and various funky options like that.

I'd suggest first checking out the output of running **nvidia-xconfig --advanced-help | less** from a terminal.  Particualrly looking at twinview or xinerama options.  Maybe also the EDID options (if your Dell is a little old, it might be reporting misleading information about itself).

---

### Post by aznlnx on 2006-12-05
Waaaaaaaaa! The Dell giving misleading information? Damn!
I hate dell u know..lol

But in all seriousness I did just leave the Dell plugged into that port that works and nothing. Still doesn't work.

I have to now use my LCD 1080i Samsung. 

Any suggestions how to get my Dell screen working now?

This is what I have 

[http://www.dell.com/content/products/productdetails.aspx/monitor_2001fp?c=us&cs=22&l=en&s=dfh](http://www.dell.com/content/products/productdetails.aspx/monitor_2001fp?c=us&cs=22&l=en&s=dfh)

Thanks :)

---


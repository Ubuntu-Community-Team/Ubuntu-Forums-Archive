---
title: "problem: laptop screen / icons / cursor / program windows / jump around"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by GMachine_24 on 2007-08-03
I am on a Compaq Presario R3000 and:

* Web pages act of their own accord - e.g. they will open or go to a linked Web site without my touching the keypad, mouse or anything.

* Program windows which are minimized suddenly maximize of their own accord.

* When I type input, the cursor jumps around 

* Another example: while typing the line above, my computer opened FIVE 'trash/file browser' windows without any input from me. Now the Firest arter window just maximized on its own and I am having to retype / correct sections of this asterisk text as the cursor jumps around, removes text pujnctuation part as  programs continue to act, seemingly, on their own.

* The cursor also acts on its own when I attempt to type messages in gedit text program.

I would continue my list but this is driving me crazy. I have read 'fixes' posted by other Ubuntu-ites but they do not solve my problem.

Help me before I kill again. (Kidding.):lolflag:

Thanks.

--GM

---

### Post by ReaderRat on 2007-08-03
I went to the Compaq site, but could not get pertinent info without DLing pdf. Is it an Intel or AMD notebook? Does it have on-board video, and what type.
```
sudo glxinfo
```  will output video & drivers.

If that doesn't work:```
lspci | grep VGA
```

---

### Post by GMachine_24 on 2007-08-04
Hi:

I will post the information you requested but I really think this has to do with the touchpad and drivers for it.... but then again, since i have no idea what is causing this, i should just be happy someone replied so thanks :)

<code output>

username@computer:~$ sudo glxinfo
Password:
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

0x23 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x24 16 tc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 None
0x25 16 tc  0 24  0 r  y  .  5  6  5  8  0 16  8 16 16 16 16  0 0 None
0x26 16 tc  0 24  0 r  .  .  5  6  5  8  0 16  8 16 16 16 16  0 0 None
0x27 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  0  0  0  0  0  0 0 None
0x28 16 dc  0 16  0 r  y  .  5  6  5  0  0 16  8 16 16 16  0  0 0 None
0x29 16 dc  0 24  0 r  y  .  5  6  5  8  0 16  8 16 16 16 16  0 0 None
0x2a 16 dc  0 24  0 r  .  .  5  6  5  8  0 16  8 16 16 16 16  0 0 None

</code output>

****but i think this is what you might be looking for:***

<code output>

username@computer:~$ lspci | grep VGA
0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go 32M] (rev a3)

</code output>

The CPU is an AMD Athlon XP-M Processor 2800+

Ok, I think that does it. Because of the problems I am having with the touchpad and keyboard and arrows, you would not believe how long it took me to create this post 

Any help is greatly appreciated.

[Possible hint: it seems, sometimes, that if I type very s  l  o  w  l  y (I can type 120wpm+ being a former journalist) these problems appear to be minimized.]

gm

p.s. there is a fair chance that, since the cursor jumps around so much, keystrokes might be entered in the middle of a word or somewhere in the quoted computer output - it will most likely appear as a lower-case letter that seems out of place. i did the best i could to remove them all - but assume errors such as this are typos and not code/software problems

---

### Post by ThrobbingBrain66 on 2007-08-04
My first inclination is that you are accidentally gently hitting/rubbing the touchpad with your hands as you type, causing the erratic behavior.  If this doesn't happen at all when your hands are off the keyboard, this is most certainly the case.  You can disable touchpad tapping by adding
```
option "MaxTapTime" "0"
``` to the synaptics section of your xorg.conf file.

The section should look something like this:
```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"MaxTapTime"		"0"
EndSection
```

---


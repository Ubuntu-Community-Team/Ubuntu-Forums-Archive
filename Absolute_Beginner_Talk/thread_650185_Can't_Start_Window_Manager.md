---
title: "Can't Start Window Manager"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by klausner on 2007-12-26
Initially I was going to title this "I am so screwed!"

I was trying to install the packages for synce, and when I restarted my system, it will only come up into text mode. I can manually start xinit, but I can't start compiz, nautilus, firefox, or anything else I've tried. I get a libgtk2.0 error. But if I try to reinstall libgtk, it tells me too many other things are using it.

Short of doing a nuke-reinstall, how can I fix the system? :confused:

---

### Post by LaRoza on 2007-12-26
What happens when you type "startx"?

Also, can tell exactly what you did.

---

### Post by klausner on 2007-12-26
Startx produces the following:

```

hostname: Unknown host
xauth:  creating new authority file /home/klausner/.serverauth.6028

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux cimarron 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Dec 25 22:20:38 2007
(==) Using config file: "/etc/X11/xorg.conf"

(II) Module already built-in
(II) Module already built-in
(EE) intel(0): detecting sil164
(EE) intel(0): Unable to read from DVOI2C_E Slave 112.
(II) Module already built-in
Atom 4, CARD32 4, unsigned long 4
Synaptics DeviceInit called
SynapticsCtrl called.
Synaptics DeviceOn called
SetClientVersion: 0 9
Synaptics DeviceOff called

waiting for X server to shut down (EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.


```

When I try to start compiz after xinit; I ger:

```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:3582 (rev 02) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 


```

I was trying to install the parts for synce, and since the version on the package server is way behind,  I was forced into doing it manually from source, and having to install the parts to allow building the parts, etc.

The modules I was working on included: synce-gnome-0.10.0, synce-rra-0.10.0, librapi2-0.10.0, libsynce-0.10.0, python, glib-2.7.7, odccm-0.10.0, and glib-2.4.5. Frankly, I would have to dig to see which ones I actually got installed.

---

### Post by GSF1200S on 2007-12-26
> **klausner said:**
> Startx produces the following:

```

hostname: Unknown host
xauth:  creating new authority file /home/klausner/.serverauth.6028

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux cimarron 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Dec 25 22:20:38 2007
(==) Using config file: "/etc/X11/xorg.conf"

(II) Module already built-in
(II) Module already built-in
(EE) intel(0): detecting sil164
(EE) intel(0): Unable to read from DVOI2C_E Slave 112.
(II) Module already built-in
Atom 4, CARD32 4, unsigned long 4
Synaptics DeviceInit called
SynapticsCtrl called.
Synaptics DeviceOn called
SetClientVersion: 0 9
Synaptics DeviceOff called

waiting for X server to shut down (EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.


```

When I try to start compiz after xinit; I ger:

```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:3582 (rev 02) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 


```

I was trying to install the parts for synce, and since the version on the package server is way behind,  I was forced into doing it manually from source, and having to install the parts to allow building the parts, etc.

The modules I was working on included: synce-gnome-0.10.0, synce-rra-0.10.0, librapi2-0.10.0, libsynce-0.10.0, python, glib-2.7.7, odccm-0.10.0, and glib-2.4.5. Frankly, I would have to dig to see which ones I actually got installed.

Can you post the results of: 

```
glxinfo
```

And by 'after init' you mean that you set runlevel 3 and the GUI starts up? It sounds (and looks like with the startx error) the xorg.conf has become unusable and youll need to regenerate it in order to get 3d rendering from your intel card... the results of glxinfo will help us figure out whats next.

Good luck ;)

---

### Post by klausner on 2007-12-26
> 
Can you post the results of: glxinfo

And by 'after init' you mean that you set runlevel 3 and the GUI starts up? It sounds (and looks like with the startx error) the xorg.conf has become unusable and youll need to regenerate it in order to get 3d rendering from your intel card... the results of glxinfo will help us figure out whats next.



First, I am using ***x**init *to start X, not init.

Running glxinfo gives these results:

```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 852GM/855GM 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 7.0.1
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array, 
    GL_EXT_convolution, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_3DFX_texture_compression_FXT1, 
    GL_APPLE_client_storage, GL_APPLE_packed_pixels, 
    GL_ATI_blend_equation_separate, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x64 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
Error: unable to open display 


```

Thanks.

---

### Post by klausner on 2008-01-06
[IMG]http://www.kellyforums.com/forum/images/kc_forums/smilies/hurray.gif[/IMG]
See [http://ubuntuforums.org/showthread.php?p=4082750#post4082750]("http://ubuntuforums.org/showthread.php?p=4082750#post4082750")

---


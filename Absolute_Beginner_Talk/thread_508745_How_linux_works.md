---
title: "How linux works?"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by Kosimo on 2007-07-24
Hello.
I'm trying to understand how Linux works internally.
I'm a quite new Linux user and I have a simple idea about how my Ubuntu works. 


As far as I could understand 'till now,  Drivers are something inside the kernel if I'm not mistaken.
What's exactly the difference between Windows and Linux about drivers? Why is quite complicated to install the video driver in linux? Why do I need to compile my kernel?  I just want to understand the basic points. 
What is GLX,  GXGL...  

Then the last question is:
My laptop has a Mobility Radeon 9200, and it comes installed and working perfectly by default with Feisty. (With poor 3D performance by the way, but working anyway). I guess that the driver I'm using is not the official ATI driver, but some open source driver, right?  I found this when typing glxinfo from the console

```
laptop:~$ glxinfo
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
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 1x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 6.5.2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
    GL_EXT_histogram, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_ATI_fragment_shader, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_window_pos, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_OES_read_format, GL_SGI_color_matrix, 
    GL_SGI_color_table, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x4b 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

I'm may using MESA drivers? Is MESA some open source community that makes free drivers?
If the answer is yes, I'm using the 1.3 - 6.5.2. From Mesa home Page I found that the last version is the 7.0 already. Can I update them?

I know I'm may asking too much, but I really want to understand how my system works, specially now that I switch completely to Linux. I will really appreciate some answer.

Sorry for my english I know I can improve it ;)

From Barcelona.

---

### Post by wolfen69 on 2007-07-24
here's something to get you started   [http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)      google is your friend.

---

### Post by FleetAdmiral74 on 2007-07-24
[http://en.wikipedia.org/wiki/Linux_kernel](http://en.wikipedia.org/wiki/Linux_kernel)

This gives an overview, and more detailed links if you want.

---

### Post by Kosimo on 2007-07-24
> **wolfen69 said:**
> here's something to get you started   [http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)      google is your friend.

Thank you for your answers guys.
But, I search already in google, wikipedia, and other topics about this already. But I wanted to discuss this here in the forum because I couldn't understand it.  

The link you just post It doesn't answer my last question by the way. 

:confused:

---

### Post by Kosimo on 2007-07-24
> **FleetAdmiral74 said:**
> [http://en.wikipedia.org/wiki/Linux_kernel](http://en.wikipedia.org/wiki/Linux_kernel)

This gives an overview, and more detailed links if you want.


Yep, read :)

---

### Post by Foxmike on 2007-07-24
As far as I could understand 'till now, Drivers are something inside the kernel if I'm not mistaken.
 
No you are not.  Actually, the kernel is the lower layer between you and the physical hardware.  So basically, this is the overall drivers to make it run.  Drivers under *nix like systems are often called "modules" or "kernel modules".
 
Comes the second point.  The kernel can be "monolythic", which means that everything is compiled/bundled together.  With such a kernel, each time you change/update hardware, you have to re-compile it.  On another hand, there are (I don't remember the proper term here) kernels, that holds the very basics and everything else lays around as "drivers".
 
What we have with Ubuntu Linux (as I understood) is a mix of the two.  That is why we can add/remove some "drivers" or "modules".  The modules that comes by default is MESA, which works fine with any basic video card.  It does not takes advantages of the performance you could have, but it is sure to work.  In order to take advantage of your video card, you have to install proper video drivers, or modules.  For ATI, there is an open-source one and a closed-source one.  The best way to install drivers is to go thru the menus to the Restricted Drivers Manager: System -> Administration -> Restricted Drivers Manager.  A little window will pop-up with check boxes.  Just tick what suits you and apply!:)
 
Hope it helps!:)

---

### Post by asmoore82 on 2007-07-24
All Linux "drivers" are actually either kernel modules or built into the kernel.

Many of them began as speciality projects off to the side such as ALSA for sound drivers
and then eventually were merged into the kernel when they became stable.

Video drivers are a special case for several reasons.

1. for fast video performance they require two parts: the kernel module (hardware driver) and the xorg Driver (software module)
2. the official nVidia and/or ATI drivers are proprietary software that many Linux distrobutions will not enable by default for philosophical and legal reasons.

-------------------------

xorg is an Open-Source implementation of the X11 Windowing System
GLX is an extention of xorg to allow OpenGL graphics in X11 sessions

XGL is not a part of xorg but instead a re-implementation of X11 from the ground up with OpenGL in mind and composite rendering

the Mesa3D project is an Open-Source implementation of OpenGL and hopefully someday may provide 100% functionality on nVidia and ATI cards without the use of Proprietary Drivers.
Mesa3D was once knows as MesaGL but it's members now strongly request not to be called that for legal reasons.

XGL may sound like a great idea but the last I saw of it it was more of a conversation piece that a usable alternative to xorg

XGL may do _amazing_ effects with ease but stumble on everyday things like video playback
xorg is the best for everyday things but may stumble on effects.

---

### Post by dirtydenver on 2007-07-24
**Operating Systems - internals and design principles (Stallings)** is a good text on the subject of internals of all modern OSs

---

### Post by Kosimo on 2007-07-24
> **Foxmike said:**
> As far as I could understand 'till now, Drivers are something inside the kernel if I'm not mistaken.
 
No you are not.  Actually, the kernel is the lower layer between you and the physical hardware.  So basically, this is the overall drivers to make it run.  Drivers under *nix like systems are often called "modules" or "kernel modules".
 
Comes the second point.  The kernel can be "monolythic", which means that everything is compiled/bundled together.  With such a kernel, each time you change/update hardware, you have to re-compile it.  On another hand, there are (I don't remember the proper term here) kernels, that holds the very basics and everything else lays around as "drivers".
 
What we have with Ubuntu Linux (as I understood) is a mix of the two.  That is why we can add/remove some "drivers" or "modules".  The modules that comes by default is MESA, which works fine with any basic video card.  It does not takes advantages of the performance you could have, but it is sure to work.  In order to take advantage of your video card, you have to install proper video drivers, or modules.  For ATI, there is an open-source one and a closed-source one.  The best way to install drivers is to go thru the menus to the Restricted Drivers Manager: System -> Administration -> Restricted Drivers Manager.  A little window will pop-up with check boxes.  Just tick what suits you and apply!:)
 
Hope it helps!:)


Merci :)
That's exactly what I was trying to understand.
The monolytic kernel we're using is this (bloc) that contains everything we need to make our hardware works. 
That's a huge difference between (other, or in this case the windows) kernel. 
So, when I'm updating my "drivers" I'm putting them inside my kernel and that's why I MUST compile it.

Much more clear now :-)

About MESA, I felt already the gap in performance, but is still a valid option at the moment. Specially now that my video card (ati mobility 9200) is not supported by ATI drivers anymore. I can't enable the restricted drivers in ubuntu because says I don't need anyone. :lolflag:

Merci again for your answer.
Good night from Catalonia

---

### Post by irish_flu on 2007-07-24
> **Foxmike said:**
> 
Comes the second point.  The kernel can be "monolythic", which means that everything is compiled/bundled together.  With such a kernel, each time you change/update hardware, you have to re-compile it.  On another hand, there are (I don't remember the proper term here) kernels, that holds the very basics and everything else lays around as "drivers".
 

To add to this excellent info (hopefully correctly) the "NT Kernel" (used by Windows NT, 2000, XP, 2003, and Vista) is what you call a "micro-kernel".  BSD (and OSX, by extension) also uses this type of kernel.

---

### Post by Kosimo on 2007-07-24
> **asmoore82 said:**
> All Linux "drivers" are actually either kernel modules or built into the kernel.

Many of them began as speciality projects off to the side such as ALSA for sound drivers
and then eventually were merged into the kernel when they became stable.

Video drivers are a special case for several reasons.

1. for fast video performance they require two parts: the kernel module (hardware driver) and the xorg Driver (software module)
2. the official nVidia and/or ATI drivers are proprietary software that many Linux distrobutions will not enable by default for philosophical and legal reasons.

-------------------------

xorg is an Open-Source implementation of the X11 Windowing System
GLX is an extention of xorg to allow OpenGL graphics in X11 sessions

XGL is not a part of xorg but instead a re-implementation of X11 from the ground up with OpenGL in mind and composite rendering

the Mesa3D project is an Open-Source implementation of OpenGL and hopefully someday may provide 100% functionality on nVidia and ATI cards without the use of Proprietary Drivers.
Mesa3D was once knows as MesaGL but it's members now strongly request not to be called that for legal reasons.

XGL may sound like a great idea but the last I saw of it it was more of a conversation piece that a usable alternative to xorg

XGL may do _amazing_ effects with ease but stumble on everyday things like video playback
xorg is the best for everyday things but may stumble on effects.


And here we go. The final and perfect answer I was waiting for.
Thank you for make this clear to me. Was really difficult to find out when not an expert.

You're completely right about video playback in GLX. But I have to say that the last Gutsy tribe 3, was really fluent with desktop effects enabled. Videos where playing PERFECTLY even moving windows. Maybe we're moving on the right direction.

About mesa, do I have any chance to update (easily) from 6.5.2 to 7?

It's always nice to learn new things every day ^-^

---

### Post by Foxmike on 2007-07-24
Actually, just to correct a detail, the Linux kernel MUST NOT have to be re-compiled when you change video drivers, because video drivers (or modules) will "hook" themselves to the kernel.  The only time you have to re-compile the kernel is when you need a module to be "built-in" the kernel.  For an examble, there is a module to read ext2fs.  Without this module, the kernel cannot do anything with an ext2fs formatted hard drive.  If the ext2fs module is compiled outside the kernel, the kernel must firstly check on the disc in order to load it, but will be unable to read the disk because it does not have the module.  So you need ext2fs module build-in the kernel.  Other modules are "optionnal" so in order to keep the kernel to a decent size, they have been compiled, but outside the kernel, as modules.  After boot, the kernel has to load modules automagically or on demand.
 
If you end-up building your own custom kernel, you will have the possibility to build almost everything inside the kernel. That is what I am actually doing with my Gentoo Linux kernel.  Only pieces I really want as modules (for good reasons) are compiled outside.  Everyrhing else is compiled inside.

---


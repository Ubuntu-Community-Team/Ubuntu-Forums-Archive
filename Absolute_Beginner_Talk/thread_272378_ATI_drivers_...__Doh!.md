---
title: "ATI drivers ...  Doh!"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-10-06
I just reinstalled my Ubuntu. 
I did it for that only reason, to get my ATI drivers to work.

Can someone tell me what I am doing wrong? On breezy I never had this problem.

I donwload the newest ATI drivers (ati-driver-installer-8.29.6.run).

I then:

> sudo sh ati-driver-installer-8.29.6.runFollow the the grafic installer,  and done.

then I in the terminal type "aticonfig" and find there is nothing to do there.

I reboot.

Now I would think this is what I need to do, but when I login it fails. I try to login again, and it fails again. Sometimes I have to login5 or 6 times before it takes me to my desktop. My Screen is also in 640X480 and I cant set it higher.

So I run 
dpkg-reconfigure xserver-xorg 

set it to ATI drivers, make sure I can pick better screen resolution and set things up currect.

And now I can set my screen back.  But wait..  now I run:


> aktiwers@HAL:~$ glxgears -info
GL_RENDERER   = Mesa GLX Indirect
GL_VERSION    = 1.2 (1.5 Mesa 6.4.1)
GL_VENDOR     = Mesa project: [www.mesa3d.org]("http://www.mesa3d.org")
GL_EXTENSIONS = GL_ARB_imaging GL_ARB_multitexture GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_transpose_matrix GL_EXT_abgr GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias
X connection to :0.0 broken (explicit kill or server shutdown).
aktiwers@HAL:~$ glxgears -printfps
1171 frames in 5.1 seconds = 230.893 FPS
1140 frames in 5.1 seconds = 224.123 FPS
X connection to :0.0 broken (explicit kill or server shutdown).
aktiwers@HAL:~$
See? Back on Breezy when my drivers was installed currect, it showed the ATI info, and the FPS was about 4500-4900?

Can anyone see what I am doing wrong?

---

### Post by jm2003uk on 2006-10-06
I'm not sure how to help you but when i installed dapper on my pc it detected my ati card fine (i think...)

When i run 'glxinfo | grep rendering' this is what i get:

*********************************WARN_ONCE*********************************
File r300_state.c function r300Enable line 456
TODO - double side stencil !
***************************************************************************
No ctx->FragmentProgram._Current!!
direct rendering: Yes

I have no idea if thats good or not, except 'direct rendering: Yes' and so far everything works nicely (apart from the odd flickers when screensavers and some games run).

Perhaps if you do end up re-installing again trying running that command first and see if direct rendering is enabled before trying to install the ati drivers.


James

---

### Post by aktiwers on 2006-10-06
I forgot to say I have a radeon 9800 Pro.
Well it works fine on a fresh install, but it does not have 3d rendering. Also the FPS is too low.

I really want the ATI drivers, and dont understand why they worked fine on Breezy and not on Dapper?

Thanks for the reply though, try running
glxgears -printfps
from terminal.

Anyone else see what I am doing wrong?

---

### Post by zaflaucich on 2006-10-06
Follow the instruction in this  [thread]("http://www.ubuntuforums.org/showthread.php?t=204910")
change only the version number

---

### Post by aktiwers on 2006-10-06
Thanks. I just followed the guide, and it seams like Im closer to fixing my problem.

However, I still had to login 3 times after this reboot.

I went to Terminal and did these 3 commands.
> 
[SIZE=5]** aktiwers@HAL:~$ fglrxinfo**[/SIZE]
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.6065 (8.29.6)

[SIZE=5]** aktiwers@HAL:~$ glxgears -printfps**[/SIZE]
626 frames in 5.0 seconds = 125.092 FPS
628 frames in 5.0 seconds = 125.594 FPS
**[SIZE=5] aktiwers@HAL:~$ glxgears -info[/SIZE]**
GL_RENDERER   = RADEON 9800 Pro Generic
GL_VERSION    = 2.0.6065 (8.29.6)
GL_VENDOR     = ATI Technologies Inc.
GL_EXTENSIONS = GL_ARB_multitexture GL_EXT_texture_env_add GL_EXT_compiled_vertex_array GL_S3_s3tc GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_multisample GL_ARB_occlusion_query GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_shadow GL_ARB_shadow_ambient GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_crossbar GL_ARB_texture_env_dot3 GL_ARB_texture_float GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_blend GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_ARB_draw_buffers GL_ATI_draw_buffers GL_ATI_element_array GL_ATI_envmap_bumpmap GL_ATI_fragment_shader GL_ATI_map_object_buffer GL_ATI_separate_stencil GL_ATI_texture_env_combine3 GL_ATI_texture_float GL_ATI_texture_mirror_once GL_ATI_vertex_array_object GL_ATI_vertex_attrib_array_object GL_ATI_vertex_streams GL_ATIX_texture_env_combine3 GL_ATIX_texture_env_route GL_ATIX_vertex_shader_output_point_size GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_clip_volume_hint GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_object GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_texgen_reflection GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod_bias GL_EXT_texture_mirror_clamp GL_EXT_texture_object GL_EXT_texture_rectangle GL_EXT_vertex_array GL_EXT_vertex_shader GL_HP_occlusion_test GL_NV_blend_square GL_NV_occlusion_query GL_NV_texgen_reflection GL_SGI_color_matrix GL_SGIS_generate_mipmap GL_SGIS_texture_border_clamp GL_SGIS_texture_edge_clamp GL_SGIS_texture_lod GL_SUN_multi_draw_arrays
aktiwers@HAL:~$


You see, my Fps is still only 100 something.. it used to be 4500+.
Also when I login, and it through me back to the login screen, it sometimes hang at the Tty1 with somekind of error. I dont know how to show it, as I cant do anything out there, before it throughs me to the login screen.

Any Idea?

---

### Post by aktiwers on 2006-10-06
Here is my : dmesg | grep fglrx 


> aktiwers@HAL:~$ dmesg | grep fglrx
[17179601.168000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179601.172000] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
[17179601.172000] [fglrx] module loaded - fglrx 8.29.6 [Sep 19 2006] on minor 0
[17179605.076000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[17179605.076000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[17179605.076000] [fglrx] AGP detected, AgpState   = 0x1f00421b (hardware caps of chipset)
[17179605.076000] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[17179605.084000] [fglrx] total      GART = 536870912
[17179605.084000] [fglrx] free       GART = 520876032
[17179605.084000] [fglrx] max single GART = 520876032
[17179605.084000] [fglrx] total      LFB  = 119533568
[17179605.084000] [fglrx] free       LFB  = 94367744
[17179605.084000] [fglrx] max single LFB  = 94367744
[17179605.084000] [fglrx] total      Inv  = 0
[17179605.084000] [fglrx] free       Inv  = 0
[17179605.084000] [fglrx] max single Inv  = 0
[17179605.088000] [fglrx] total      TIM  = 0
[17179623.048000]  [<f8dea551>] firegl_irq_cleanup+0x121/0x1d0 [fglrx]
[17179623.048000]  [<f8de9a2b>] firegl_takedown+0x89b/0xba0 [fglrx]
[17179623.048000]  [<f8de889f>] firegl_release+0x12f/0x190 [fglrx]
[17179628.348000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[17179628.348000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[17179628.352000] [fglrx] AGP detected, AgpState   = 0x1f00421b (hardware caps of chipset)
[17179628.352000] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[17179628.360000] [fglrx] total      GART = 536870912
[17179628.360000] [fglrx] free       GART = 520876032
[17179628.360000] [fglrx] max single GART = 520876032
[17179628.360000] [fglrx] total      LFB  = 119533568
[17179628.360000] [fglrx] free       LFB  = 94367744
[17179628.360000] [fglrx] max single LFB  = 94367744
[17179628.360000] [fglrx] total      Inv  = 0
[17179628.360000] [fglrx] free       Inv  = 0
[17179628.360000] [fglrx] max single Inv  = 0
[17179628.360000] [fglrx] total      TIM  = 0
[17179638.040000]  [<f8dea551>] firegl_irq_cleanup+0x121/0x1d0 [fglrx]
[17179638.040000]  [<f8de9a2b>] firegl_takedown+0x89b/0xba0 [fglrx]
[17179638.040000]  [<f8de889f>] firegl_release+0x12f/0x190 [fglrx]
[17179638.040000]  [<f8dea551>] firegl_irq_cleanup+0x121/0x1d0 [fglrx]
[17179638.040000]  [<f8de9a2b>] firegl_takedown+0x89b/0xba0 [fglrx]
[17179638.040000]  [<f8de889f>] firegl_release+0x12f/0x190 [fglrx]
[17179638.044000]  [<f8dea551>] firegl_irq_cleanup+0x121/0x1d0 [fglrx]
[17179638.044000]  [<f8de9a2b>] firegl_takedown+0x89b/0xba0 [fglrx]
[17179638.044000]  [<f8de889f>] firegl_release+0x12f/0x190 [fglrx]
[17179672.984000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[17179672.984000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[17179672.984000] [fglrx] AGP detected, AgpState   = 0x1f00421b (hardware caps of chipset)
[17179672.984000] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[17179672.992000] [fglrx] total      GART = 536870912
[17179672.992000] [fglrx] free       GART = 520876032
[17179672.996000] [fglrx] max single GART = 520876032
[17179672.996000] [fglrx] total      LFB  = 119533568
[17179672.996000] [fglrx] free       LFB  = 94367744
[17179672.996000] [fglrx] max single LFB  = 94367744
[17179672.996000] [fglrx] total      Inv  = 0
[17179672.996000] [fglrx] free       Inv  = 0
[17179672.996000] [fglrx] max single Inv  = 0
[17179672.996000] [fglrx] total      TIM  = 0
aktiwers@HAL:~$


---

### Post by aktiwers on 2006-10-06
I followed this guide
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

And it seams like the logon thing has been fixed..  I still have low Fps though..

---

### Post by WalmartSniperLX on 2006-10-06
> **aktiwers said:**
> Thanks. I just followed the guide, and it seams like Im closer to fixing my problem.

However, I still had to login 3 times after this reboot.

I went to Terminal and did these 3 commands.


You see, my Fps is still only 100 something.. it used to be 4500+.
Also when I login, and it through me back to the login screen, it sometimes hang at the Tty1 with somekind of error. I dont know how to show it, as I cant do anything out there, before it throughs me to the login screen.

Any Idea?

My X1600pro is also choking at around 120-123 (rarely 130) fps with the newest fglrx driver, but I scored the same with the previous ones too.

Also I would get hangs too, but when logging out or shutting down.

---

### Post by aktiwers on 2006-10-06
Okey thanks.. I guess I can live with that then.. specially when I just got XGL + Beryl to work!! WOW!!!

---


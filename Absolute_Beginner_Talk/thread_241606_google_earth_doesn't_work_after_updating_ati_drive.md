---
title: "google earth doesn't work after updating ati driver"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by joris1977 on 2006-08-22
After I updated the Ati-driver (Radeon 9200 pro), google earth stopped working. I uninstalled  and reinstalled google earth, but it didn't help.
I don't have any problems with other programs.

Here is the output from the terminal after reinstalling google earth and trying to start it up.   

joris@Ruuf:~/Desktop$ chmod +x GoogleEarthLinux.bin
joris@Ruuf:~/Desktop$ sudo ./GoogleEarthLinux.bin
Password:
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.0.1693..................................................................
Installing mimetypes...
Running /usr/bin/update-mime-database /home/joris/.local/share/mime
***
* Updating MIME database in /home/joris/.local/share/mime...
Wrote 2 strings at 20 - 6c
Wrote aliases at 6c - 70
Wrote parents at 70 - 74
Wrote literal globs at 74 - 78
Wrote suffix globs at 78 - d0
Wrote full globs at d0 - d4
Wrote magic at d4 - e0
Wrote namespace list at e0 - e4
***

Note that '/home/joris/.local/share' is not in the search path
set by the XDG_DATA_HOME and XDG_DATA_DIRS
environment variables, so applications may not
be able to find it until you set them. The
directories currently searched are:

- /root/.local/share
- /usr/local/share/
- /usr/share/

Installing desktop menu entries...
joris@Ruuf:~/Desktop$ googleearth


I liked google earth a lot and don't like to switch back to windows all the time, so  if someone has any idea to solve this....it would be really great. :-D

---

### Post by Davidios on 2006-08-28
Same problem here. Any help?

---

### Post by Toxicity999 on 2006-08-28
uhm... all you showed us was a successful install output and you starting googleearth with no output... Was there a visual error at all? I mean... you literally showed us everything working fine.

Edit:
out of curiousity di you have an r2xx series card? do you get alotttt of error output on glxinfo? The newer drivers by default break for r2xx cards.

---

### Post by Davidios on 2006-08-29
I have a Radeon 9250:

```
davids@ubuntu:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample,
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200 Series DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.28.8)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array,
    GL_S3_s3tc, GL_ARB_occlusion_query, GL_ARB_point_parameters,
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_transpose_matrix, GL_ARB_vertex_blend, GL_ARB_vertex_buffer_object,
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_ATI_element_array,
    GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, GL_ATI_map_object_buffer,
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once,
    GL_ATI_vertex_array_object, GL_ATI_vertex_attrib_array_object,
    GL_ATI_vertex_streams, GL_ATIX_texture_env_combine3,
    GL_ATIX_texture_env_route, GL_ATIX_vertex_shader_output_point_size,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,
    GL_EXT_stencil_wrap, GL_EXT_texgen_reflection, GL_EXT_texture3D,
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_EXT_vertex_shader, GL_HP_occlusion_test, GL_NV_blend_square,
    GL_NV_occlusion_query, GL_NV_texgen_reflection, GL_SGI_color_matrix,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None

```

When I start Google Earth, I only can see the "loading screen", you know. It doesn't start.

---

### Post by joris1977 on 2006-08-29
Thanks for replying Toxicity999, when i start google earth i also get the loading screen, and here it also doesn't start. There is no terminal output with usefull information what the problem could be. 

I have a radeon 9200 pro card and updated the driver  following this guide :[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)    
to get the tv-out working.

After updating the ati driver i had also troubles with real player, but after reinstalling it worked fine. That's why i looked real hard to find a repo so i could install google earth with synaptic. I found a repo but reinstalling didn't help.

this is the glxinfo

joris@Ruuf:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample,
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200 Series DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.28.8)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array,
    GL_S3_s3tc, GL_ARB_occlusion_query, GL_ARB_point_parameters,
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_transpose_matrix, GL_ARB_vertex_blend, GL_ARB_vertex_buffer_object,
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_ATI_element_array,
    GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, GL_ATI_map_object_buffer,
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once,
    GL_ATI_vertex_array_object, GL_ATI_vertex_attrib_array_object,
    GL_ATI_vertex_streams, GL_ATIX_texture_env_combine3,
    GL_ATIX_texture_env_route, GL_ATIX_vertex_shader_output_point_size,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays,
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,
    GL_EXT_stencil_wrap, GL_EXT_texgen_reflection, GL_EXT_texture3D,
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_EXT_vertex_shader, GL_HP_occlusion_test, GL_NV_blend_square,
    GL_NV_occlusion_query, GL_NV_texgen_reflection, GL_SGI_color_matrix,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 Slow
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 Slow
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
joris@Ruuf:~$

hope you have some suggestion to help me and Davidios out cause we seem to have the same problem

---

### Post by Toxicity999 on 2006-08-29
Well I was just asking on the offchance that you had one of the lowerend card that are effected by a bug in the newer drivers like me. What you may want to do is just uninstall these drivers and roll back to a previous version until someone comes up with a more permanent fix. Read on the cchtml wiki about manual installs and just use an older driver from the time when it was working. The bug I mentioned incase you were curious resulted in a system with no advanced rendering and almost every call broken. But that's not your case. Unless theres some kind of log or verbose mode for running Gearth that's your only option really... I know they use a custom version of wine so it might work in much the same way they just hide all the fixme and the like output.

---

### Post by leonleyva on 2006-09-18
Have the same google problem with ati...

---

### Post by Frank Golden on 2006-09-18
> **leonleyva said:**
> Have the same google problem with ati...

Running google earth from terminal should give error output.
Create a launcher for GE and check the "run in terminal" box in the launcher setup. When you run this launcher it should show in the terminal what is going on.

---

### Post by Najand on 2006-09-18
Did you guys install it yourselves or just via automatix or easyubuntu?

---

### Post by joris1977 on 2006-09-19
sorry Frank Golden, i made a launcher and checked in terminal but there just isn´t any error output. So no point to start troubleshooting...

thnx for replying anyway

I installed it following the on the forums. Didn´t work. I tried another time installing it from a repo To be found on this site. [http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/](http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/)  Make sure you uncheck it afterwards because there´s some experimental stuff on it you might not want. Also will set somethings to italian...

---

### Post by Frank Golden on 2006-09-28
> **joris1977 said:**
> sorry Frank Golden, i made a launcher and checked in terminal but there just isn´t any error output. So no point to start troubleshooting...

thnx for replying anyway
I get a running dialog of what is going on when I launch GE
using the terminal argument. It is usually hidden behind the GE 
screen.

---

### Post by MrBlonds on 2006-11-08
I have the same problem on a laptop compaq nx7010, ati radeo 9250, edgy ...

---

### Post by lon3lyliv3r on 2006-11-08
i used automatix2 to install google earth, after installing ati drivers.

now when i try to open google earth it stays at loading screen!



:(

---

### Post by rabid emu on 2006-11-13
I'm getting the same problem with an ATI x1600 card and fglrx drivers.

---

### Post by Paerez on 2006-12-13
I am getting this problem too. I modified google's startup script to run gdb and got this backtrace:

```
#0  0xb612e710 in ?? () from /lib/tls/i686/cmov/libc.so.6
#1  0xb61f2bcb in pthread_mutex_lock () from /lib/tls/i686/cmov/libc.so.6
#2  0xb5f230c5 in __glXInitialize () from /usr/lib/libGL.so.1
#3  0xb5f214be in glXWaitVideoSyncSGI () from /usr/lib/libGL.so.1
#4  0xb68415fb in Gap::Gfx::igOglVisualContext::internalSwapBuffers () from ./libIGGfx.so
#5  0xb685a5da in Gap::Gfx::igOglVisualContext::endDraw () from ./libIGGfx.so
#6  0xb39d666a in earth::evll::VisualContext::determineRefreshRate () from /usr/local/google-earth/libevll.so
#7  0xb39d6e3c in earth::evll::VisualContext::init () from /usr/local/google-earth/libevll.so
#8  0xb399cc45 in earth::evll::RenderContextImpl::init () from /usr/local/google-earth/libevll.so
#9  0xb63581c0 in RenderWidget::setApi () from ./librender.so
#10 0xb634581a in earth::render::RenderWindow::createWidget () from ./librender.so
#11 0xb77e47e7 in earth::client::ModuleWidget::showEvent () from ./libgoogleearth.so
#12 0xb6e321f7 in QWidget::event () from ./libqt-mt.so.3
#13 0xb6d87691 in QApplication::internalNotify () from ./libqt-mt.so.3
#14 0xb6d88179 in QApplication::notify () from ./libqt-mt.so.3
#15 0xb6e31156 in QWidget::show () from ./libqt-mt.so.3
#16 0xb6e30eab in QWidget::showChildren () from ./libqt-mt.so.3
#17 0xb6e310f7 in QWidget::show () from ./libqt-mt.so.3
#18 0xb6e30eab in QWidget::showChildren () from ./libqt-mt.so.3
#19 0xb6e310f7 in QWidget::show () from ./libqt-mt.so.3
#20 0xb6e30eab in QWidget::showChildren () from ./libqt-mt.so.3
#21 0xb6e310f7 in QWidget::show () from ./libqt-mt.so.3
#22 0xb6e30eab in QWidget::showChildren () from ./libqt-mt.so.3
#23 0xb6e310f7 in QWidget::show () from ./libqt-mt.so.3
#24 0xb6e30eab in QWidget::showChildren () from ./libqt-mt.so.3
#25 0xb6e310f7 in QWidget::show () from ./libqt-mt.so.3
#26 0xb6e30eab in QWidget::showChildren () from ./libqt-mt.so.3
#27 0xb6e310f7 in QWidget::show () from ./libqt-mt.so.3
#28 0xb6e30eab in QWidget::showChildren () from ./libqt-mt.so.3
#29 0xb6e310f7 in QWidget::show () from ./libqt-mt.so.3
#30 0xb6f05223 in QMainWindow::show () from ./libqt-mt.so.3
#31 0xb6e2a7c3 in QWidget::showNormal () from ./libqt-mt.so.3
#32 0xb77b9d40 in MainWindow::readScreensizeInfo () from ./libgoogleearth.so
#33 0xb77d2992 in earth::client::Application::run () from ./libgoogleearth.so
#34 0xb77d3afd in earth::client::Application::Application () from ./libgoogleearth.so
#35 0x0804b70b in main ()

```

I am a Computer Science student, but the best I can gather from here is that google earth failed to get a mutex lock on the graphics hardware. And I have no clue where to go from there :D

---

### Post by Paerez on 2006-12-13
OK I found a solution on the google community forums. Download ati's 8.27 drivers and extract libGL.so.1.2 and copy it to "/usr/local/google-earth/libGL.so.1".

I have attached libGL.so.1.2 from 8-27. Download it to your desktop, extract it, then type:
"sudo cp ~/Desktop/libGL.so.1.2-8.27 /usr/local/google-earth/libGL.so.1"

enjoy.

---

### Post by osval on 2006-12-29
I have the same problem in my two computers, one is a desktop with a Radeon 9800SE video card and the other a laptop with Radeon Xpress 200M. Both uses the same ATI driver launched on december 13th. If someone know how to fix this problem without having to downgrade anything please let me know.

It's obvious that the problem resides on the ATI driver or FireGL.

The solution Paerez wrote works but doesn't use the 3D features of the video card. It just activate the software emulation turning Google Earth extremely slow.

---

### Post by k|d&lt;FuNkY&gt;FrY on 2006-12-30
Well, I feel like I've tried everything short of pulling my own hair out! I'll keep an eye on this thread and hope that something else surfaces relatively soon.

---

### Post by petermck on 2006-12-30
> **k|d<FuNkY>FrY said:**
> Well, I feel like I've tried everything short of pulling my own hair out! I'll keep an eye on this thread and hope that something else surfaces relatively soon.

I had the same problem when I upgraded to the ATI driver from their web-site. It broke the googleearth startup and also broke playback of .wmv files in Totum. I fixed it by rolling back my xorg.conf to the Linux ATI driver and dropped the attached library in ~/googleearth folder. This is the same driver as Paerez posted, I've just renamed it from libGL.so.1.2-8.27 to libGL.so.1 and put it in the place where the GoogleEarthLinux.bin installed everything. Thanks Paerez for the fit.

---

### Post by petermck on 2006-12-30
> **Paerez said:**
> OK I found a solution on the google community forums. Download ati's 8.27 drivers and extract libGL.so.1.2 and copy it to "/usr/local/google-earth/libGL.so.1".

I have attached libGL.so.1.2 from 8-27. Download it to your desktop, extract it, then type:
"sudo cp ~/Desktop/libGL.so.1.2-8.27 /usr/local/google-earth/libGL.so.1"

enjoy.

Thanks for the help. It worked great.

---

### Post by petermck on 2006-12-30
I had the same problem. Check out ' Ati Radeon Xpress 200M + Edgy + FGLRX working how to' as a search. The instructions there work well, at least for getting sortware rendering working.

---

### Post by k|d&lt;FuNkY&gt;FrY on 2006-12-30
> **petermck said:**
> I had the same problem. Check out ' Ati Radeon Xpress 200M + Edgy + FGLRX working how to' as a search. The instructions there work well, at least for getting sortware rendering working.

I will look into it ASAP! Thanks for all the help! It really is appreciated!

---

### Post by JohnnyBee on 2007-05-19
Hey guys! This workaround with libGL.so.1 was quite helpful. However, it still has several problems at least in my case since the earth appears to be white and the countries are with yellow lines. 

Could this be attributed to the fact that i'm using the 8.36.5 driver for my ati 200m and the libGL.so.1 is from 8.28.8 driver???

Any ideas?

---


---
title: "Couple of problems with ubuntu"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by ITdrummer on 2007-07-09
Hello all, 
First of all, this is my first experience with ANY linux distro so i am pretty new to everything that's not windoze.
I am currently dual-booting Ubuntu  with XP on my Dell Inspiron 1100 laptop and have gotten close to running perfectly.  I have gotten my wireless card working, email client, installed several more games that were not pre-installed, and have gotten pretty comfortable with the CLI.  Although many things have fallen together, there are a few more bugs i must get figured out. 

1) For starters, when i play FPS' (Nexuiz, Termulous, Warsow), everytime i shoot the gun, the screen laggs REALLY bad.  It onlly seems to happen when i shoot the gun/weapon.  Could this be an issue with a graphics driver.  My direct rendering is labeled as "yes" so i always though my display driver was working.  Could it be that i have no 3-d rendering?

2)  I was playing around with configuring my "taskbar"(dont know what its called in Ubuntu) and i deleted some items from the pane.  I got them all back except the item that shows icons for running applications, similar to windoze' bottom right corner.  I right-clicked on the bar and selected "add to panel" and i couldn t find it anywhere.  Did i screw up?

lastly, 3) I just got a Lexar 256 MB Jump Drive, can i read/write files to/from windows with Ubuntu?  Will i need to format the Jumpdrive with NTFS or FAT 32?

Im sorry for the multiple questions, but if i didnt get the out now i would forget about them.
Any help would be greatly appreciated.
Tanks in advance!

---

### Post by shrift on 2007-07-09
1. I expect you don't have a very good video card on your laptop. Can you find out what you have?

2. It is called the "notification area" It's at the bottom of the "add to panel" window.

3. You can use the drive to copy files to both. You need to format it as fat32.

---

### Post by Wiebelhaus on 2007-07-09
> **shrift said:**
> 1. I expect you don't have a very good video card on your laptop. Can you find out what you have?

2. It is called the "notification area" It's at the bottom of the "add to panel" window.

3. You can use the drive to copy files to both. You need to format it as fat32.

ditto

---

### Post by ITdrummer on 2007-07-09
> **shrift said:**
> 1. I expect you don't have a very good video card on your laptop. Can you find out what you have?



I originally thought the same thing. 
 It is an Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03). 

 But what leads me away from this is the fact that i have been able to play games such as Halo, Battlefield 1942, Wolfenstein, deus-ex, and other such "graphically intensive" games with no problem running windows.  I would assume if i can run a game like Halo or deus-ex, i should be able to run tremulous, nexuiz, and warsow no problem.  Is this an incorrect assumption?

---

### Post by ITdrummer on 2007-07-09
If it helps: 

```
 $ glxinfo
name of display: :0.0
display: :0 screen: 0
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
OpenGL renderer string: Mesa DRI Intel(R) 845G 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 6.5.2
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

visual x bf lv rg d st colorbuffer ax dp st accumbuffer ms cav
id dep cl sp sz l ci b ro r g b a bf th cl r g b a ns b eat
----------------------------------------------------------------------
0x23 16 tc 0 16 0 r y . 5 6 5 0 0 16 0 0 0 0 0 0 0 None
0x24 16 tc 0 16 0 r . . 5 6 5 0 0 16 0 0 0 0 0 0 0 None
0x25 16 tc 0 16 0 r y . 5 6 5 0 0 16 8 0 0 0 0 0 0 Slow
0x26 16 tc 0 16 0 r . . 5 6 5 0 0 16 8 0 0 0 0 0 0 Slow
0x27 16 tc 0 16 0 r y . 5 6 5 0 0 16 0 16 16 16 0 0 0 Slow
0x28 16 tc 0 16 0 r . . 5 6 5 0 0 16 0 16 16 16 0 0 0 Slow
0x29 16 tc 0 16 0 r y . 5 6 5 0 0 16 8 16 16 16 0 0 0 Slow
0x2a 16 tc 0 16 0 r . . 5 6 5 0 0 16 8 16 16 16 0 0 0 Slow
0x2b 16 dc 0 16 0 r y . 5 6 5 0 0 16 0 0 0 0 0 0 0 None
0x2c 16 dc 0 16 0 r . . 5 6 5 0 0 16 0 0 0 0 0 0 0 None
0x2d 16 dc 0 16 0 r y . 5 6 5 0 0 16 8 0 0 0 0 0 0 Slow
0x2e 16 dc 0 16 0 r . . 5 6 5 0 0 16 8 0 0 0 0 0 0 Slow
0x2f 16 dc 0 16 0 r y . 5 6 5 0 0 16 0 16 16 16 0 0 0 Slow
0x30 16 dc 0 16 0 r . . 5 6 5 0 0 16 0 16 16 16 0 0 0 Slow
0x31 16 dc 0 16 0 r y . 5 6 5 0 0 16 8 16 16 16 0 0 0 Slow
0x32 16 dc 0 16 0 r . . 5 6 5 0 0 16 8 16 16 16 0 0 0 Slow
0x4b 32 tc 0 32 0 r . . 8 8 8 8 0 0 0 0 0 0 0 0 0 Ncon

```

and my lspci:
```



~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02)
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:04.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller


```

---

### Post by Wiebelhaus on 2007-07-09
How much ram is allocated to the onboard chip?

---

### Post by ITdrummer on 2007-07-09
I have 512MB system memory and either 32 or 64MB graphics memory

---

### Post by shrift on 2007-07-09
Well it may or may not mean that you can use the open source games well... : ( I presume you were running those other games in windows? And with that video card probably with the settings all the way down. I don't think running those games well in windows = running the open source FPSs well in Linux. It is a bit odd that you only get hiccups when firing the gun, maybe there is a particularly intensive bit of rendering during that though. : (

---

### Post by ITdrummer on 2007-07-09
> **shrift said:**
> Well it may or may not mean that you can use the open source games well... : ( I presume you were running those other games in windows? And with that video card probably with the settings all the way down. I don't think running those games well in windows = running the open source FPSs well in Linux. It is a bit odd that you only get hiccups when firing the gun, maybe there is a particularly intensive bit of rendering during that though. : (

I understand what your saying, but it makes NO sense whatsoever.  How can i play a much more intense game on windows and not be able to play a less intense game on linux?

---

### Post by shrift on 2007-07-09
> **ITdrummer said:**
> I understand what your saying, but it makes NO sense whatsoever.  How can i play a much more intense game on windows and not be able to play a less intense game on linux?

Unfortunately as far as 3d rendering etc, windows has generally had the edge over other PC platforms. Which is not to say that what your experiencing is not a bug, it may be. I hope you can get it figured out!

---

### Post by ITdrummer on 2007-07-09
> **shrift said:**
> Unfortunately as far as 3d rendering etc, windows has generally had the edge over other PC platforms. Which is not to say that what your experiencing is not a bug, it may be. I hope you can get it figured out!

How can i find out if it is a bug and not just Windoze being superior to Ubuntu in something?

---

### Post by shrift on 2007-07-09
I would try to find some forums for the game that is causing the glitching. Post a question over there, or they may have some email or irc contact info. Also you can cruise their bug system to see if anything has been reported. That is usually a good place to start.

---

### Post by forrestcupp on 2007-07-09
> **ITdrummer said:**
> I originally thought the same thing. 
 It is an Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03). 

 But what leads me away from this is the fact that i have been able to play games such as Halo, Battlefield 1942, Wolfenstein, deus-ex, and other such "graphically intensive" games with no problem running windows.  I would assume if i can run a game like Halo or deus-ex, i should be able to run tremulous, nexuiz, and warsow no problem.  Is this an incorrect assumption?

I don't know much about that chipset, but have you tried running the Restricted Drivers Manager to see if there is a proprietarty driver for it?  If there is, that may help.

> **shrift said:**
> Unfortunately as far as 3d rendering etc, windows has generally had the edge over other PC platforms. Which is not to say that what your experiencing is not a bug, it may be. I hope you can get it figured out!
That's a pretty big debate, there.  A lot of people believe that OpenGL is superior to Direct3D.  It's just that there are more people making more advanced games for Windows.

---

### Post by Lakefall on 2007-07-09
> **ITdrummer said:**
> It is an Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03).
Intel is supposed to have pretty good support, at least with their newest chipsets. They provide open source drivers.

Here's their site dedicated to that:
[http://intellinuxgraphics.org](http://intellinuxgraphics.org)

> But what leads me away from this is the fact that i have been able to play games such as Halo, Battlefield 1942, Wolfenstein, deus-ex, and other such "graphically intensive" games with no problem running windows.  I would assume if i can run a game like Halo or deus-ex, i should be able to run tremulous, nexuiz, and warsow no problem.  Is this an incorrect assumption?
I'm not sure. Tremulous, Nexuiz and Warsow may not be very heavy by todays standards, but they are new games in any case. As an example Tremulous uses the Quake III engine like Return to Castle Wolfenstein, but I wouldn't be surprised if they have found some way to make their game more demanding. Halo, Battlefield 1942, RtCW and Deus Ex are all old games by now.

Maybe you should try the Linux games on Windows to make sure Linux performs worse.

---

### Post by ITdrummer on 2007-07-09
Ill try that, but its just kind of weird what happens. I can move, run, jump, strafe but as soon as i pull the trigger, the game lags for about 1.5 seconds.  eerie

---

### Post by ITdrummer on 2007-07-16
bump

---

### Post by shrift on 2007-07-16
> **ITdrummer said:**
> Ill try that, but its just kind of weird what happens. I can move, run, jump, strafe but as soon as i pull the trigger, the game lags for about 1.5 seconds.  eerie

I really think you're looking in the wrong forums for help on the games. I'm not sure which game you're experienceing this problem in, but here's a list of support options for all three:

[http://tremulous.net/phpBB2/](http://tremulous.net/phpBB2/) The Tremulous forums.

[http://www.alientrap.org/forum/](http://www.alientrap.org/forum/) The Nexuiz forums.

[http://www.warsow.net/forum/index.php](http://www.warsow.net/forum/index.php) And the Warsow forums. 

Please post in the relevant forums as they are much more likely to be able to help you troubleshoot the game issues. : )

I hope you can get it to work! Maybe we can help if you have any other trouble.

Good luck.

---

### Post by ITdrummer on 2007-07-16
> **shrift said:**
> I really think you're looking in the wrong forums for help on the games. I'm not sure which game you're experienceing this problem in, but here's a list of support options for all three:

[http://tremulous.net/phpBB2/](http://tremulous.net/phpBB2/) The Tremulous forums.

[http://www.alientrap.org/forum/](http://www.alientrap.org/forum/) The Nexuiz forums.

[http://www.warsow.net/forum/index.php](http://www.warsow.net/forum/index.php) And the Warsow forums. 

Please post in the relevant forums as they are much more likely to be able to help you troubleshoot the game issues. : )

I hope you can get it to work! Maybe we can help if you have any other trouble.

Good luck.
 Thats just it, i am having this problem with all 3 of those games.  Thats what leads me to believe that it is a problem with my Ubuntu, not the games themselves.

---

### Post by Canis familiaris on 2007-07-16
Slower Processor?

---

### Post by ITdrummer on 2007-07-16
I have a 2.2 GHZ pentium 4.  Shouldn't this be sufficient?

---


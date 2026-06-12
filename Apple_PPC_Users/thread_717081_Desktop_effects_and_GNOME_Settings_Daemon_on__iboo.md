---
title: "Desktop effects and GNOME Settings Daemon on  ibook g3 clamshell"
date: 2008-03-06
forum: Apple PPC Users
---

### Post by samisrafi on 2008-03-06
Hello
I'm running a mac ibook g3 clamshell ( 466-MHz PowerPC G3 processor -320 MB RAM -  - Graphics support ATI RAGE Mobility 128 graphics accelerator with 8MB of SDRAM graphics memory and AGP 2X support + Composite video output to TV through AV port )
and a HDD 80 GB partitioned to 10 partitions 2 partitions for Mac OSX  and mac os 9 which are running perfectly and 1 partition for UBUNTU Hardy Heron, 1 partition for UBUNTU Dapper Drake, 1 partition for fedora 8, and 1 partition for debian 4 , they are all running perfectly except for the  followed 2 famous problems that related to Compiz-Fusion enabling :

1-when I try to change the visual effects to anything but none it always said :"Desktop effects could not be enabled" 

2- The second problem is the error that appears after starting up :
There was an error starting the GNOME Settings Daemon.
Some things, such as themes, sounds, or background settings may not work correctly.
GNOME will still try to restart the Settings Daemon next time you log in.
and some time with this error included
 The last error message was:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

I'm trying to solve it since january 27th through reading and trying most of the solutions in here but I'm really starting to loose hope and getting tired putting in mind that I'm newbi in linux but I really did my best before asking help 

By The Way this problem is not only in UBUNTU Hardy Heron , it is the same in all other systems that I tried like fedora 8,  debian 4, UBUNTU Gusty Gibbon, UBUNTU Feisty Fawn, and even I tried UBUNTU Dapper Drake
Also I tried KUBUNTU and XUBUNTU 

here you'll find the glx info which I guess is the cause of the problem and I'm ready to post any desired info with the my grateful for help

samisrafi@ubuntu:~$ glxinfo
name of display: :0.0
display: :0* screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
*** GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
*** GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
*** GLX_SGI_swap_control, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
*** GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
*** GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
*** GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
*** GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
*** GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
*** GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
*** GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
*** GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
*** GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
*** GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_swap_control, 
*** GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_swap_control, 
*** GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
*** GLX_SGIX_visual_select_group
OpenGL vendor string: VA Linux Systems, Inc.
OpenGL renderer string: Mesa DRI Rage 128 Mobility 20051027 AGP 1x
OpenGL version string: 1.2 Mesa 7.0.3-rc2
OpenGL extensions:
*** GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
*** GL_ARB_texture_compression, GL_ARB_texture_env_add, 
*** GL_ARB_texture_mirrored_repeat, GL_ARB_transpose_matrix, 
*** GL_ARB_vertex_buffer_object, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
*** GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
*** GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
*** GL_EXT_copy_texture, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 
*** GL_EXT_histogram, GL_EXT_packed_pixels, GL_EXT_polygon_offset, 
*** GL_EXT_rescale_normal, GL_EXT_secondary_color, 
*** GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
*** GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
*** GL_EXT_texture_env_add, GL_EXT_texture_object, GL_EXT_vertex_array, 
*** GL_APPLE_packed_pixels, GL_IBM_rasterpos_clip, 
*** GL_IBM_texture_mirrored_repeat, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
*** GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texgen_reflection, 
*** GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
*** GL_SGIS_generate_mipmap, GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod

** visual* x* bf lv rg d st colorbuffer ax dp st accumbuffer* ms* cav
*id dep cl sp sz l* ci b ro* r* g* b* a bf th cl* r* g* b* a ns b eat
----------------------------------------------------------------------
0x23 24 tc* 0 24* 0 r* .* .* 8* 8* 8* 0* 0 24* 0* 0* 0* 0* 0* 0 0 None
0x24 24 tc* 0 24* 0 r* .* .* 8* 8* 8* 0* 0 24* 8* 0* 0* 0* 0* 0 0 None
0x25 24 tc* 0 24* 0 r* .* .* 8* 8* 8* 0* 0 24* 0 16 16 16* 0* 0 0 Slow
0x26 24 tc* 0 24* 0 r* .* .* 8* 8* 8* 0* 0 24* 8 16 16 16* 0* 0 0 Slow
0x27 24 tc* 0 24* 0 r* y* .* 8* 8* 8* 0* 0 24* 0* 0* 0* 0* 0* 0 0 None
0x28 24 tc* 0 24* 0 r* y* .* 8* 8* 8* 0* 0 24* 8* 0* 0* 0* 0* 0 0 None
0x29 24 tc* 0 24* 0 r* y* .* 8* 8* 8* 0* 0 24* 0 16 16 16* 0* 0 0 Slow
0x2a 24 tc* 0 24* 0 r* y* .* 8* 8* 8* 0* 0 24* 8 16 16 16* 0* 0 0 Slow
0x2b 24 dc* 0 24* 0 r* .* .* 8* 8* 8* 0* 0 24* 0* 0* 0* 0* 0* 0 0 None
0x2c 24 dc* 0 24* 0 r* .* .* 8* 8* 8* 0* 0 24* 8* 0* 0* 0* 0* 0 0 None
0x2d 24 dc* 0 24* 0 r* .* .* 8* 8* 8* 0* 0 24* 0 16 16 16* 0* 0 0 Slow
0x2e 24 dc* 0 24* 0 r* .* .* 8* 8* 8* 0* 0 24* 8 16 16 16* 0* 0 0 Slow
0x2f 24 dc* 0 24* 0 r* y* .* 8* 8* 8* 0* 0 24* 0* 0* 0* 0* 0* 0 0 None
0x30 24 dc* 0 24* 0 r* y* .* 8* 8* 8* 0* 0 24* 8* 0* 0* 0* 0* 0 0 None
0x31 24 dc* 0 24* 0 r* y* .* 8* 8* 8* 0* 0 24* 0 16 16 16* 0* 0 0 Slow
0x32 24 dc* 0 24* 0 r* y* .* 8* 8* 8* 0* 0 24* 8 16 16 16* 0* 0 0 Slow
0x4c 32 tc* 0 32* 0 r* .* .* 8* 8* 8* 8* 0* 0* 0* 0* 0* 0* 0* 0 0 Ncon
samisrafi@ubuntu:~$ 

Again thank you very much for any help.

---

### Post by stream303 on 2008-03-07
> **samisrafi said:**
> 1-when I try to change the visual effects to anything but none it always said :"Desktop effects could not be enabled"

I'm not absolutely sure that desktop affects are even available at all for that box.  Heck, on my G5 iMac, I don't have that option since the video card manufacturers haven't been kind enough to provide the developers any info. :)

Is there anything here that might improve it a little?
[https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec](https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec)

> 2- The second problem is the error that appears after starting up :
There was an error starting the GNOME Settings Daemon.
Some things, such as themes, sounds, or background settings may not work correctly.

I've seen quick work-arounds including logging out, and then logging back in, messing around with a virtual terminal (ie CTRL-ALT-F2) and then coming back (CTRL-ALT-F7)

One suggested fix for this was to make sure that you install **dbus-x11**

```
sudo apt-get install dbus-x11

(note the lowercase x11)
```

These are only suggestions as I have not personally experienced this problem.

---

### Post by samisrafi on 2008-03-07
Thanks for your reply
yes it is very frustrated this graphic card subject
as for the sudo apt-get install dbus-x11 I already did that before with no good result but thanks any way for your concern .

---


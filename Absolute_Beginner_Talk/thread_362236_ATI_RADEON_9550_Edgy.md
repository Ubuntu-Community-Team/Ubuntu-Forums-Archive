---
title: "ATI RADEON 9550 Edgy"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by ddollas on 2007-02-15
Anyone know how to get the ati-driver-installer-8.33.6-x86.x86_64.run to install on Ubuntu Edgy Eft?

---

### Post by Utopar on 2007-02-15
This on the subject from the Unofficial ATI Linux Driver Wiki:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

I have the same card and have trying to get this working for quite a long time.
This guide helped a lot, followed the procedure and it didn't work.

I had to build the ATI for driver for Ubuntu/dapper to get it to work on Edgy.
Now my fglrx is loaded.
I am now running SecondLife on my Radeon 9550.

---

### Post by ddollas on 2007-02-18
It worked for me!  Thanks for the guide!

---

### Post by Gnoobuntu on 2007-02-19
Hey all,

Complete nubie here.  I've started playing around with Ubuntu after a freind recommended it to me and fell in love with it! I've still got a dual boot set up (the rest of the fam likes windows) but am personally only using Ubunutu with the occasional foray into XP.

Thanks for the awesome guide, it worked very well except for one thing. I don't know how (or if its even possible) to get it into direct render mode.

name of display: :0.0
display: :0  screen: 0
direct rendering: [COLOR="Red"]No[/COLOR]
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
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
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string:[COLOR="Red"] Mesa GLX Indirect[/COLOR]
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None

glxgears -printfps
1285 frames in 5.3 seconds = 240.242 FPS
1482 frames in 5.3 seconds = 280.641 FPS
1140 frames in 5.4 seconds = 211.493 FPS
1254 frames in 5.2 seconds = 238.954 FPS
1254 frames in 5.1 seconds = 244.848 FPS
1254 frames in 5.1 seconds = 244.948 FPS
1254 frames in 5.1 seconds = 244.813 FPS
1254 frames in 5.1 seconds = 247.477 FPS
1254 frames in 5.2 seconds = 240.687 FPS
1254 frames in 5.2 seconds = 241.651 FPS
1254 frames in 5.1 seconds = 244.354 FPS

AUPDATE:
I've noticed that when I start up glxgears it will run smoothly for about a second and then bog down. It seems that glxgears ramps up my CPU to 100% *headscratch*

---

### Post by nonewmsgs on 2007-02-19
what does this mean?

~$ aticonfig -v
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-1
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.

im using a radeon 9550 and edgy as well.  i did modify my xorg.conf file for beryl (but it still doesnt work), however, at the moment i want to know whats up with this card and to get its current settings.

---


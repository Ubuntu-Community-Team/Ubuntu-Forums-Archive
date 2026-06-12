---
title: "ATI Radeon 9800 Pro Drivers"
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-05-26
Hi!

I have been trying to install my ATI Radeon 9800 Pro video card drivers again, after I reinstalled Ubuntu 5.10.

Last time I installed it, I finally got it to work, with help from this forum. Here is my old threat:

[http://www.ubuntuforums.org/showthread.php?t=157515](http://www.ubuntuforums.org/showthread.php?t=157515)

Now when I try to do the same thing, its still not working. Here is some info:
[B]
 sudo glxinfo[/B]

```
aktiwers@ubuntu:~$ sudo glxinfo
Password:
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
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
aktiwers@ubuntu:~$

```

And then  [B]glxgears -printfps

[/B]
```
aktiwers@ubuntu:~$ glxgears -printfps
1935 frames in 5.4 seconds = 360.906 FPS
2736 frames in 5.1 seconds = 539.231 FPS
3762 frames in 5.1 seconds = 744.352 FPS
3648 frames in 5.0 seconds = 724.519 FPS
4104 frames in 5.1 seconds = 799.416 FPS
3762 frames in 5.0 seconds = 748.787 FPS
2964 frames in 5.0 seconds = 587.972 FPS
1824 frames in 5.1 seconds = 356.546 FPS
1938 frames in 5.3 seconds = 367.786 FPS
1824 frames in 5.1 seconds = 358.902 FPS
X connection to :0.0 broken (explicit kill or server shutdown).
aktiwers@ubuntu:~$

```

As you can see, the FPS is much lower than last time, where I had between  3155.190 FPS and 3945.190 FPS.

What is wrong here? And how do I install my Drivers currect?

Thanks a lot for any help!

---

### Post by Aniquibobo on 2006-05-27
Hi

New drives from ATI

[http://www2.ati.com/drivers/linux/linux_8.25.18.html](http://www2.ati.com/drivers/linux/linux_8.25.18.html)

---

### Post by aktiwers on 2006-05-27
Thanks! I got it working now! and with better FPS than Ever!

```
aktiwers@ubuntu:~$ glxgears -printfps
23573 frames in 5.0 seconds = 4714.590 FPS
23536 frames in 5.0 seconds = 4707.170 FPS
23592 frames in 5.0 seconds = 4718.226 FPS
23607 frames in 5.0 seconds = 4721.306 FPS
23583 frames in 5.0 seconds = 4716.486 FPS
23527 frames in 5.0 seconds = 4705.399 FPS
aktiwers@ubuntu:~$

```

I simply followed the guide you posted.
[http://www2.ati.com/drivers/linux/linux_8.25.18.html]("http://www2.ati.com/drivers/linux/linux_8.25.18.html")

After downloading these drivers:
[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)

Incase someone else has the same problem.

Thanks alot!

---

### Post by Aniquibobo on 2006-06-03
No problem, you are welcome.

---


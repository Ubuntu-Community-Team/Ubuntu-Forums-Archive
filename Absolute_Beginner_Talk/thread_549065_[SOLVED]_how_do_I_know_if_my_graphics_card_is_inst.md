---
title: "[SOLVED] how do I know if my graphics card is installed/configured right?"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by NovaAesa on 2007-09-12
Hi everyone,

My exams have just finished, so I though I might give gaming on Ubuntu a little try, however I seem to be running into a few problems. I installed fglrx a few weeks ago when I first installed Ubuntu, but I'm not sure if I did it correctly. The post when I installed fglrx is [here]("http://ubuntuforums.org/showthread.php?t=535771").

The problem seems to be that 3D games do not seem to be working correctly. I installed Nexuiz from the repositories but when playing the frame rate is very slow and the textures seem to be garbled. Everything in it just seems 'wrong'. I haven't bothered to try any other 3D games yet (I'm on a frequently and harshly shaped broadband connection), so I was wondering if I have done something wrong or neglected to do something making 3D support work or if Nexuiz simply has its own issues.

My relevant specs are: Sempron 3200+, Radeon X800XL, 1GiB RAM

---

### Post by hyper_ch on 2007-09-12
in a terminal run:

```

glxgears

```

if the gears move then it should be fine ;)

---

### Post by NovaAesa on 2007-09-12
The glxgears seems to work okay, but that still doesn't explain the problems with Nexuiz. Do you think I should just try some other 3D app or continue with trying to figure out what is happening with my graphics card/drivers?

---

### Post by RedGreen on 2007-09-12
I have a problem with getting 3d apps to work also, im not sure how to fix the problem, but something that diagnoses it for me:

in my Xorg.0.log I have the message:

(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed! *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO) *
(WW) fglrx(0): * no 3D acceleration available *
(WW) fglrx(0): ********************************************* *

Im curious if you might find something similar.

to open your Xorg.0.log in an editor: sudo gedit /var/log/Xorg.0.log

---

### Post by NovaAesa on 2007-09-12
nope there's nothing similar to that in there.

There's a few things that have (WW) and (EE) at the start (i think these are warnings and errors), but I have no idea what they mean.

---

### Post by Vadi on 2007-09-12
ATI said they're comming out with better drivers for Linux, and I think your card is included.

Try googling the card's name + ubuntu, some guides on how to tweak it definitely should come up.

Because I can play Nexuiz on my Radeon 7500 pretty decently (albeit I'm using the open source drives, not the flgrx, because the latter refuses to run Compiz)

---

### Post by misfitpierce on 2007-09-12
fglrxinfo usually works for ATI cards or

glxinfo and if it says Direct Rendering : Yes ... then you are good

---

### Post by RedGreen on 2007-09-12
yep:

(WW) warning, (EE) error, (NI) not implemented, (??) unknown

now to figure out how to solve any of these problems...

---

### Post by NovaAesa on 2007-09-12
> **misfitpierce said:**
> fglrxinfo usually works for ATI cards or

glxinfo and if it says Direct Rendering : Yes ... then you are good

This is what I got when I ran these commands:

```
ps@compaq-ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R300 20060815 x86/MMX+/3DNow!+/SSE2 TCL
OpenGL version string: 1.3 Mesa 6.5.2

ps@compaq-ubuntu:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
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
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R300 20060815 x86/MMX+/3DNow!+/SSE2 TCL
OpenGL version string: 1.3 Mesa 6.5.2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias

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
0x4b 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
ps@compaq-ubuntu:~$ 
```

Looks like I'll have to do some googling. Maybe later though, its getting late.

---

### Post by RedGreen on 2007-09-12
In doing some looking around I ran across this guide: [http://ubuntuforums.org/showthread.php?t=342812](http://ubuntuforums.org/showthread.php?t=342812)

Which links to information on getting the fglrx drivers to work correctly: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#C](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#C)

Haven't gotten it working myself yet but it seems like a lead on something to do.

---

### Post by NovaAesa on 2007-09-12
I found a program called Envy in the forums somewhere. It looks promising, but I won't give it a go until tommorow morning (I prefer to use my offpeak downloads for downloading stuff).

Here the [link]("http://albertomilone.com/nvidia_scripts1.html").

---

### Post by RedGreen on 2007-09-13
> **NovaAesa said:**
> I found a program called Envy in the forums somewhere. It looks promising, but I won't give it a go until tommorow morning (I prefer to use my offpeak downloads for downloading stuff).

Here the [link]("http://albertomilone.com/nvidia_scripts1.html").

I think your having the same problem I was, I tried Envy and it diddnt fix anything.

What I did to fix the problem was installed the fglrx drivers using method 2 in this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#C](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#C)

although when you get to the part that says create .deb packages and has this code:

> bash ati-driver-installer-8.38.6-x86.x86_64.run --buildpkg Ubuntu/edgy

you need to change it to this (considering your using Feisty)

> bash ati-driver-installer-8.38.6-x86.x86_64.run --buildpkg Ubuntu/Feisty

and make sure your at :user@ubuntu:~/Desktop$" get there by typing:

> cd Desktop

---

### Post by NovaAesa on 2007-09-13
YAY! It's working now. Envy seemed to do the trick.
> direct rendering: Yes

---


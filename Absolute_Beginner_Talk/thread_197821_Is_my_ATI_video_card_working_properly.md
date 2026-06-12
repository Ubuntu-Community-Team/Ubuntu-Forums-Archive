---
title: "Is my ATI video card working properly?"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by symbiont7 on 2006-06-16
I'm only a few sessions into running ubuntu off the CD, actually using it now. I see so many people having issues with their ATI cards, I was wondering before I take the plunge if my card is working properly out of the box.

Keep in mind I'm running off the CD, not sure if that changes things.

I typed in a few commands that I saw around here, and here are my results:
(BTW-I don't see a FPS counter on the "glxgears" app, and the big red gear is spinning at about 4 seconds per revolution, so I'm assuming the ATI isn't working in hardware acceleration.)

```
ubuntu@ubuntu:~$ lspci | grep ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
0000:01:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)
ubuntu@ubuntu:~$ fglrxinfo
bash: fglrxinfo: command not found
ubuntu@ubuntu:~$ glxinfo
name of display: :0.0
*********************************WARN_ONCE*********************************
File r300_state.c function r300Enable line 456
TODO - double side stencil !
***************************************************************************
No ctx->FragmentProgram._Current!!
display: :0  screen: 0
direct rendering: Yes
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
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_swap_control,
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_video_sync,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R300 20040924 AGP 1x TCL
OpenGL version string: 1.2 Mesa 6.4.1
OpenGL extensions:
    GL_ARB_fragment_program, GL_ARB_imaging, GL_ARB_multisample,
    GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_compression, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix,
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_window_pos,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color,
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture,
    GL_EXT_draw_range_elements, GL_EXT_histogram, GL_EXT_packed_pixels,
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture,
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp,
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate,
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once,
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat,
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture,
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent,
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program,
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
ubuntu@ubuntu:~$ fgl_glxgears
bash: fgl_glxgears: command not found
ubuntu@ubuntu:~$ glxgears
*********************************WARN_ONCE*********************************
File r300_state.c function r300Enable line 456
TODO - double side stencil !
***************************************************************************
No ctx->FragmentProgram._Current!!
*********************************WARN_ONCE*********************************
File r300_render.c function r300_get_num_verts line 188
user error: Need more than 2 vertices to draw primitive QS !
***************************************************************************
ubuntu@ubuntu:~$

```

Any thoughts? I'd rather not go through the lengthy headaches others seem to have endured just to get hardware acceleration up and running. Although I DO want it. I hate to throw in the towel before a fight even, but are Nvidia cards just THAT much easier to deal with out of the box? Almost seems easier for me to go buy a cheap Nvidia card rather than fight with an installation, especially for a total rookie.

Thanks for any help.

[edit]
Oops...I have an ATI Radeon 9600XT

---

### Post by muep on 2006-06-16
Actually, when the drivers work, an Nvidia driver is not easier to install than an ATI driver. Neither of them are included in default installations because of their proprietariness.

There are free drivers for some ATI chips. It seems that you have Direct Rendering enabled, but I don't think it works on a 9600 card.

The driver installation isn't hard, I think the 9600s at least are quite well supported. On this computer I have a 9600 XT which works perfect, though not nearly as fast as in windows. Still better than no acceleration at all.

The basic way to install ATI drivers:
```
sudo apt-get update
sudo apt-get install xorg-driver-fglrx
sudo dpkg-reconfigure xserver-xorg
```

You can try this even on the livecd. The driver will be stored in your RAM.

---

### Post by imrumpf on 2006-06-16
The way it works is that the real ATI drivers cannot be bundled with ubuntu, for some stupid reasons. the default "ati" driver really sucks, so what you have to do when you install ubuntu is install the xorg-driver-fglrx from the repositories. 

go to this link for installing instructions: [link]("https://wiki.ubuntulinux.org/BinaryDriverHowto/ATI#head-5ead174a0b3294527486cd4d71ded66b40003f25")

Hope I could help!

---

### Post by firetux on 2006-06-16
The only thing you can actually do is to try it.

Just install it, install xorg-driver-fglrx and linux-restricted-modules, and change "ati" in your xorg.conf (the device section, next to driver) to "fglrx". Its as simple as  that(if it works).

If it doesn't just do some google searches and if nothing works just open a thread here, its frustrating, but in the end, when you get it working you will realise it was fun.
(I'm assuming you are a user that wants to learn about his computer)

To get the fps do
```
glxgears -printfps
```
and for a more advanced test
```
fgl_glxgears
```
These two commands will only be available after you install the drivers(not sure about this).

---

### Post by symbiont7 on 2006-06-16
[QUOTE=firetux]...
To get the fps do
```
glxgears -printfps
```
....[/QUOTE]

Oh, hehe. I thought the gears would spin faster as the FPS went up, silly me! I'm getting around 1600 FPS, but that doesn't sound like a lot compared to others I've seen.

Thanks everyone for the input so far.

---

### Post by JGKC9AYC on 2006-06-16
[QUOTE=firetux]The only thing you can actually do is to try it.

Just install it, install xorg-driver-fglrx and linux-restricted-modules, and change "ati" in your xorg.conf (the device section, next to driver) to "fglrx". Its as simple as  that(if it works).

If it doesn't just do some google searches and if nothing works just open a thread here, its frustrating, but in the end, when you get it working you will realise it was fun.
(I'm assuming you are a user that wants to learn about his computer)

To get the fps do
```
glxgears -printfps
```
and for a more advanced test
```
fgl_glxgears
```


These two commands will only be available after you install the drivers(not sure about this).[/QUOTE]

I'm running a 9800 Pro on an A64 3200+ w/2 gb ram.  What, theoretically, should my FPS be?
I did that test & got 876...that seems kinda low, yes?

---

### Post by firetux on 2006-06-16
To see if your driver is set up properly(only for ati-users) do:

```
fglrxinfo
```

If that says somthing about ati, its configured just right (in 98% of the cases)
If it says about mesa, you haven't installed the drivers or configured them wrongly.

---

### Post by JGKC9AYC on 2006-06-16
[QUOTE=firetux]To see if your driver is set up properly(only for ati-users) do:

```
fglrxinfo
```

If that says somthing about ati, its configured just right (in 98% of the cases)
If it says about mesa, you haven't installed the drivers or configured them wrongly.[/QUOTE]

Here's what I got when I typed in ```
fglrxinfo
```

[i]
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.5814 (8.25.18 )
[/i]

Now...about those FPS  ;)

---

### Post by firetux on 2006-06-16
[QUOTE=JGKC9AYC]Here's what I got when I typed in ```
fglrxinfo
```

[i]
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.5814 (8.25.18 )
[/i][/QUOTE]
That is good.
> 
Now...about those FPS  ;)
Those are not good, with your graphics card you should be getting around 4000 and more.

---

### Post by symbiont7 on 2006-06-16
[QUOTE=firetux]To see if your driver is set up properly(only for ati-users) do:

```
fglrxinfo
```

If that says somthing about ati, its configured just right (in 98% of the cases)
If it says about mesa, you haven't installed the drivers or configured them wrongly.[/QUOTE]

Maybe you missed that in my original post, it was a bit long. I got:

ubuntu@ubuntu:~$ fglrxinfo
bash: fglrxinfo: command not found

Did I type something in wrong? It's already been established it's just an out of the box install (Live CD actually) and I guess that doesn't come with the actual ATI drivers, but shouldn't it have said something? Did I need to put "sudo" in front of it?

Total newbie, that's why I'm here! :-)

---

### Post by BoyOfDestiny on 2006-06-16
[QUOTE=symbiont7]Maybe you missed that in my original post, it was a bit long. I got:

ubuntu@ubuntu:~$ fglrxinfo
bash: fglrxinfo: command not found

Did I type something in wrong? It's already been established it's just an out of the box install (Live CD actually) and I guess that doesn't come with the actual ATI drivers, but shouldn't it have said something? Did I need to put "sudo" in front of it?

Total newbie, that's why I'm here! :-)[/QUOTE]

No you didn't do anything wrong. Out of the box you get the open source drivers, which work great for lower cards (I'm using it on my 9250 as I type this)... 

Just follow the instructions in the other post... Step by step, go to synaptic, install xorg-driver-fglrx 

after that
from a terminal

gksudo gedit /etc/X11/xorg.conf

search for "ati"
change it to "fglrx"

save and reload X

Achtung:
If something goes wrong you'll need to edit xorg.conf again... So I'd recommend making a backup, or if you are comfortable in terminal, reboot into recovery mode, then do a 

nano /etc/X11/xorg.conf

change "fglrx" back to "ati", press ctrl x to save...

---

### Post by JGKC9AYC on 2006-06-16
[QUOTE=firetux]That is good.

Those are not good, with your graphics card you should be getting around 4000 and more.[/QUOTE]

What can I do about that?
I take it you saw the results of "fglrxinfo"?
Are those drivers up to date?
Is there another (possibly more reliable) test I can run to check my FPS?

---

### Post by lime4x4 on 2006-06-16
john@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9550 Generic
OpenGL version string: 2.0.5814 (8.25.18)

john@ubuntu:~$ glxgears -printfps
Usage:
  -display <displayname>  set the display to run on
  -stereo                 run in stereo mode
  -fullscreen             run in fullscreen mode
  -info                   display OpenGL renderer info
john@ubuntu:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
977 frames in 5.0 seconds = 195.400 FPS
912 frames in 5.0 seconds = 182.400 FPS
1098 frames in 5.0 seconds = 219.600 FPS
1121 frames in 5.0 seconds = 224.200 FPS
1102 frames in 5.0 seconds = 220.400 FPS
1120 frames in 5.0 seconds = 224.000 FPS
1105 frames in 5.0 seconds = 221.000 FPS
1106 frames in 5.0 seconds = 221.200 FPS
1119 frames in 5.0 seconds = 223.800 FPS
1099 frames in 5.0 seconds = 219.800 FPS
john@ubuntu:~$ lspci | grep ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
0000:01:00.1 Display controller: ATI Technologies Inc RV350 ?? [Radeon 9550] (Secondary)
john@ubuntu:~$

is this decent or does it require more tweaking yet?

---

### Post by JGKC9AYC on 2006-06-16
[QUOTE=firetux]To get the fps do
```
glxgears -printfps
```
and for a more advanced test
```
fgl_glxgears
```
[/QUOTE]

What's the difference between the two...just one's in a cube & one isn't?
I'm getting drastic differences in my FPS between them.
The first one varied between 6500 FPS & 14500 FPS & the second varied between 390 FPS & 1900 FPS.
That's some difference, yes?

---

### Post by highslime on 2006-06-16
hmm i have an ati radeon 9250, and this is what i get:
```

steven@steven-kubuntu:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
1401 frames in 5.0 seconds = 280.200 FPS
1533 frames in 5.0 seconds = 306.600 FPS
1536 frames in 5.0 seconds = 307.200 FPS
steven@steven-kubuntu:~$ glxgears -printfps
9178 frames in 5.0 seconds = 1835.592 FPS
9271 frames in 5.0 seconds = 1854.102 FPS
9220 frames in 5.0 seconds = 1843.805 FPS
9257 frames in 5.0 seconds = 1851.265 FPS
9250 frames in 5.0 seconds = 1849.829 FPS
9227 frames in 5.0 seconds = 1845.235 FPS
steven@steven-kubuntu:~$

```

1850fps seems sort of low too, but i know that the 9250 is outdated now.  :(

---

### Post by firetux on 2006-06-17
fgl_glxgears is a very heavy test, I'm not getting more than 700 with my x700.
If it runs smoothly it means everything is ok, and 3D-accel is propperly set up.

That problem with glxgears, wanting extra options is new for me too, some weeks ago it didn't do that.

Wow, this thead has been statrted by symbiont7 and hijacked by JGKC9AYC, lime4x4 and highslime. With all those different problems its very difficult to concentrate and find a solution for your problems. Bear in mind that I'm doing this for fun so please make thread of your own. This way we can help you better.

I'm going to answer everyone of you this afternoon, after my exam.

---

### Post by JGKC9AYC on 2006-06-17
I noticed when I had the video window minimized, my FPS went up...but I guess that's normal.
So are we stuck at these FPS until better drivers come out?

---

### Post by firetux on 2006-06-17
[QUOTE=JGKC9AYC]I noticed when I had the video window minimized, my FPS went up...but I guess that's normal.
So are we stuck at these FPS until better drivers come out?[/QUOTE]
 I don't see your problem, your fps are excellent.(with an similar nvidia card you would be getting twice as much fps but thats just ati's fault)

Hihgslime; Your fps are good too, for that card, try to play some game(ppracer)

Lime4x4: do ```
glxgears -info
``` and tell us what fps you get.

symbiont7: Did you get the divers working off the live-cd?

---

### Post by lime4x4 on 2006-06-17
5350 frames in 5.0 seconds = 1069.926 FPS
5306 frames in 5.0 seconds = 1061.104 FPS
5307 frames in 5.0 seconds = 1061.236 FPS
5306 frames in 5.0 seconds = 1061.139 FPS
5306 frames in 5.0 seconds = 1061.111 FPS
5306 frames in 5.0 seconds = 1061.165 FPS
5306 frames in 5.0 seconds = 1061.086 FPS
5306 frames in 5.0 seconds = 1061.119 FPS
5306 frames in 5.0 seconds = 1061.077 FPS
5306 frames in 5.0 seconds = 1061.109 FPS
5306 frames in 5.0 seconds = 1061.084 FPS
5306 frames in 5.0 seconds = 1061.109 FPS
5306 frames in 5.0 seconds = 1061.034 FPS

---

### Post by firetux on 2006-06-17
[QUOTE=lime4x4]5350 frames in 5.0 seconds = 1069.926 FPS
5306 frames in 5.0 seconds = 1061.104 FPS
5307 frames in 5.0 seconds = 1061.236 FPS
5306 frames in 5.0 seconds = 1061.139 FPS
5306 frames in 5.0 seconds = 1061.111 FPS
5306 frames in 5.0 seconds = 1061.165 FPS
5306 frames in 5.0 seconds = 1061.086 FPS
5306 frames in 5.0 seconds = 1061.119 FPS
5306 frames in 5.0 seconds = 1061.077 FPS
5306 frames in 5.0 seconds = 1061.109 FPS
5306 frames in 5.0 seconds = 1061.084 FPS
5306 frames in 5.0 seconds = 1061.109 FPS
5306 frames in 5.0 seconds = 1061.034 FPS[/QUOTE]
Thats on the edge, can you play 3dgames? (ppracer for example)

---

### Post by symbiont7 on 2006-06-17
[QUOTE=firetux]...
symbiont7: Did you get the divers working off the live-cd?[/QUOTE]

Nope. It actually got worse, big time!

But I haven't had the chance to mess with it again, I think I'm going to wait until Monday or Tuesday when I put in a 3rd drive and install ubuntu there for testing.

I didn't use your method, I used the method posted by muep, I just figured running a few command lines was going to be easier than finding and changing some config file.

```
sudo apt-get update
sudo apt-get install xorg-driver-fglrx
sudo dpkg-reconfigure xserver-xorg
```

What I didn't realize was that I got some window with like a million options to select (I guess that was the xserver?) and had no idea what to choose for half of them. So I just started hitting enter really fast! After all that was done glxgears actually ran slower, so much so the gears were visibly moving slower and were choppy.

I'll try your method next time. But let me ask, with the way that I tried, can I just change a few setting in xserver (that's what the app was right?) and quit out of it? Or do I have to go through the whole thing?

Tweaking a couple lines in a config is now sounding MUCH easier than running through a bunch of setting I have no clue how to set.

Thanks for all the help!

---

### Post by pommattski on 2006-06-17
(I have Radeon 9600XT)
I have followed the procedure in the wiki - as linked to earlier in this thread - and I now get the following:
```
mattski@TheKubuntuMachine:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
```
I did notice in xorg.conf that there are TWO "Screen" Sections and 2 "Device" Sections - is this normal?

---

### Post by firetux on 2006-06-17
[QUOTE=symbiont7]
But I haven't had the chance to mess with it again, I think I'm going to wait until Monday or Tuesday when I put in a 3rd drive and install ubuntu there for testing.[/QUOTE]
That is indeed the best to do.

[QUOTE=symbiont7]
Tweaking a couple lines in a config is now sounding MUCH easier than running through a bunch of setting I have no clue how to set.[/QUOTE]
Exactly, the command line and editing config files not something to be afaid of.
I think they are the biggest shortcoming in windows.

[QUOTE=symbiont7]
Thanks for all the help![/QUOTE]
Always glad to help!

pommatski: Try to remove the device section that says "ati" instead of "fglrx", see if that works. If it doesn't work do a search on the forums or google and if you don't get it solved start a new thread.(I don't know about this forum's policy but in most of the forums I go, thread-hijacking is not-done)

---


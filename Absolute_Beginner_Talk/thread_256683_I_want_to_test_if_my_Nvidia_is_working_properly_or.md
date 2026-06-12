---
title: "I want to test if my Nvidia is working properly or not !!"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by D_frag on 2006-09-13
I would like some assistance as to how i can be hundred percent sure of my cards effeciency on linux and that it's totally functinal 
any reomendations ?
I get the nvidia flash screen but i have doubts

---

### Post by Lord Illidan on 2006-09-13
Either download a 3D game from the repos and try it out.

Like ```
sudo apt-get install planetpenguin-racer
``` or else run glxgears in a terminal, and post the framerate here.

Also, run ```
glxinfo | less
``` in a terminal, and examine the first 4 lines.

---

### Post by D_frag on 2006-09-13
this is what i got when i typed glxinfo | less

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4

and when i typed glxgears in the terminal i got that gears revolvin around each other but i dunno how to know the framerate ?

---

### Post by haxer on 2006-09-13
Ive got this :P 

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync,
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_multisample, GLX_NV_float_buffer, GLX_ARB_fbconfig_float,
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation


Is that good?

---

### Post by D_frag on 2006-09-13
I've tried the game 
it works but the screen resolution is not corrent it's in the middle of my screen and it's tilted from the edges lookin like an american football

---

### Post by furiousV on 2006-09-13
> **D_frag said:**
> this is what i got when i typed glxinfo | less

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4

and when i typed glxgears in the terminal i got that gears revolvin around each other but i dunno how to know the framerate ?

The framerate will show in the console, every 5 seconds it will display another average FPS.

haxer, lookin good mate

---

### Post by haxer on 2006-09-13
Thx almost new graphic card i love it :=)

---

### Post by Drakkor on 2006-09-13
Ooh,that glxgears thing is cool ! :p

---


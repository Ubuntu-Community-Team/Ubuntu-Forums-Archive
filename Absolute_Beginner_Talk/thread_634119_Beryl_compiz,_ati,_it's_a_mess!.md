---
title: "Beryl compiz, ati, it's a mess!"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by peterj on 2007-12-07
HI,

I used to be ok with this kind of thing but I'm only going back to Ubuntu after a year and I literally forget everything! 

This 7.10 OS is nice, but it's strange for me the way more settings can be controlled by the interface and I'm having trouble differentiating between what I do in terminal and what I do with the mouse! 

so I have an ATI x1300 and 2 monitors, a Dell and an Insignia TV which is widescreen. 

First problem:
I can't set the second monitor to anything other than a replica of the first. The options to do so aren't available in the settings manager (they're there, but grey)

Second problem:
I love Beryl, although I'm willing to try compiz. I installed the advanced editor for setting but anytime I try and enable the 'extra' mode I get this message: 'the composite extension is not available' I have the proprietary driver enabled and direct:rendering is a 'yes' (see output below)


Third problem:
I'm not sure if I'm using the optimum broadcom drivers. My internet speed leaves a lot to be desired and it's normally very quick. I disabled ipv6 in Firefox (about:config) and not for the whole comp as downloads seem ok. It helped a lot but still sluggish connection. 

I'll be here all day so tell me what info you need and how to get it, and I'll deliver promptly. 

To be honest I'm really out of the know here, as in I haven't a clue whats going on! Normally I would have spent hours learning, which I enjoy so much. But this time I said, 'I want Ubuntu, but I don't have time to spend hours working things out' - This year is really busy for me.

I really appreciate the help, thank you. 
Peter




peter@box:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
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
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300/X1550 Series
OpenGL version string: 2.0.6473 (8.37.6)
OpenGL extensions:

---

### Post by peterj on 2007-12-07
I really would appreciate any help at all on this!

Problem 4:

peter@box:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 16 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x39 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None


I somehow managed to do this through the graphic settings manager. Everytime I try and tell it I'm using ATI proprietary radeon drivers and a Dell E197FP monitor it reverts to it's old settings

PLEASE HELP!!

---

### Post by peterj on 2007-12-09
Please could someone help me out on this I've tried everything at this stage

---


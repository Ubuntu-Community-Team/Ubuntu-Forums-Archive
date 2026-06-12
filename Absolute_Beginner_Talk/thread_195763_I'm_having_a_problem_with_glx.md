---
title: "I'm having a problem with glx"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by lordharsha on 2006-06-13
I'm having problems running blender. When I try to run it thru the terminal, I get this error:
> archangel@vault:~$ blender
Using Python version 2.4
Xlib:  extension "GLX" missing on display ":0.0".
ERROR: Unable to open Blender window


glxinfo give me this:
> archangel@vault:~$ glxinfo
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
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None


I have NO idea what to do now.

Also, I got this error whenever I try to run a graphics app thru terminal:
> (sysinfo:14854): Gdk-WARNING **: locale not supported by Xlib

(sysinfo:14854): Gdk-WARNING **: cannot set locale modifiers


I'm using an on board graphics card, on my 82845G

---

### Post by nitricacid on 2006-06-13
I am almost sure your card needs to support 32bit graphics.
I know my intel-graphics card that came with my mobo (motherboard) isn't 32bit but 24bit.
If your card does support 32bit then you might just have to install some glx files, such at nvidia-glx for invidia cards.

---

### Post by lordharsha on 2006-06-13
My card does support 32bit graphics. I had installed the nvidia-glx file, but still had the problem.

---

### Post by nitricacid on 2006-06-17
[QUOTE=lordharsha]My card does support 32bit graphics. I had installed the nvidia-glx file, but still had the problem.[/QUOTE]

I am not sure on this but you could try changing the color-depth in your xorg.conf file from 24 to 32.

---


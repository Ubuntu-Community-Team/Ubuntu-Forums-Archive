---
title: "blender problems"
date: 2011-12-28
forum: Art &amp; Design
---

### Post by barkerson on 2011-12-28
[FONT=Arial][SIZE=2]I know this is the wrong place to ask but, something is  wrong when I try to open blender (just downloaded the 2.61 version), nothing happens, I opened it from the terminal and this is what i got:
[/SIZE][/FONT][FONT=Arial][SIZE=2]```
emil@emil:~/Dokument/blender-2.61$ blender
Info: Config directory with "startup.blend" file not found.
Xlib:  extension "GLX" missing on display ":0".
/build/buildd/blender-2.58-svn37702/intern/ghost/intern/GHOST_WindowX11.cpp:194: X11 glXQueryVersion() failed, verify working openGL system!
initial window could not find the GLX extension, exit!
```Can anyone help me?[/SIZE][/FONT]

---

### Post by thatguruguy on 2011-12-28
It seems like your openGL system isn't working correctly.  Have you tried installing Blender from the Ubuntu repository (eg, the Ubuntu Software Center or Synaptic)?  It's possible that you're missing a required package.

---

### Post by barkerson on 2011-12-29
[FONT=Arial][SIZE=2]hmm... I tried to re-install the normal blender, I installed it to see if it worked[/SIZE][/FONT][FONT=Arial][SIZE=2] (it didn't) then I tried to open the downloaded blender from the terminal and I got the same error as before.[/SIZE][/FONT]

---

### Post by BcRich on 2012-01-03
hi 
dunno if this will help but you're supposed to have a startup.blend in a hidden dir in your home dir. Mine is here..

/home/bcrich/.blender/2.61/config/startup.blend

and a copy of my startup.blend

---

### Post by mcduck on 2012-01-04
> **barkerson said:**
> [FONT=Arial][SIZE=2]I know this is the wrong place to ask but, something is  wrong when I try to open blender (just downloaded the 2.61 version), nothing happens, I opened it from the terminal and this is what i got:
[/SIZE][/FONT][FONT=Arial][SIZE=2]```
emil@emil:~/Dokument/blender-2.61$ blender
Info: Config directory with "startup.blend" file not found.
Xlib:  extension "GLX" missing on display ":0".
/build/buildd/blender-2.58-svn37702/intern/ghost/intern/GHOST_WindowX11.cpp:194: X11 glXQueryVersion() failed, verify working openGL system!
initial window could not find the GLX extension, exit!
```Can anyone help me?[/SIZE][/FONT]

What graphics card do you have, and what driver are you using for it?

Based on the error it would seem that either the GPU or the driver currently in use isn't up to the task of running OpenGL graphics.

---


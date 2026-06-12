---
title: "where is the Proprietary driver tool in kubuntu"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by adewale on 2007-05-21
this may sound dumb but i've just got to ask. i got my kubuntu fiesty disc and fired it up but i couldn't find the tool that helps enable the nvidia driver. although when i typed glxgears it brought out the gears but was real slow so i need the driver

---

### Post by petersjm on 2007-05-21
You can use either Automatix2 or Envy to install the driver. Automatix is probably the easiest way (worked for me). Does the output of **glxinfo | grep direct** say "direct-rendering: yes"? If so, you've already got the driver installed. Maybe you just need an update? What's your FPS in glxgears? I'm getting about 1127 FPS, which I think is okay (runs smoothly, anyway).

---

### Post by adewale on 2007-05-21
i think i got 125 and the driver was nv. so probably i've got direct rendering since i got the gears

---

### Post by adewale on 2007-05-23
hi sorry this is the output of **glxinfo | grep direct**
direct rendering: no
openGl render string: Mesa Glx Indirect
pleasse what does this mean? does it mean i have 3d but its so slow

---

### Post by petersjm on 2007-05-25
Sorry not to reply sooner. Not sure what the render sting part means, but "direct rendering: no" means there's a problem. Try uninstalling your driver, then downloading Automatix2 and installing the nvidia driver from there. reboot and try the gears again. Hopefully it will work.

---

### Post by Bachstelze on 2007-05-25
If you're using the nv driver, no wonder you don't get direct rendering ! Just install the nvidia ones (and please don't use Automatix for that !)

[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)

---

### Post by adewale on 2007-05-25
thanks i'll give it a shot

---

### Post by Shaun32 on 2008-04-05
Hi everyone,

Sorry to dig up a sort of old post, but I have a Compaq R4000 laptop with the XPress 200M graphics card.  My output of **glxinfo | grep direct** is:
Warning, xpress200 detected.
direct rendering: Yes

Does Linux/Kubuntu hate my graphics card, is that why it shows WARNING!?!?!  I know people have had trouble with this laptop and this card in the past, but the driver is installed, as you can see, and all that was done for me almost automatically (all I had to do was approve the proprietary driver installation).

I would like to show you my FPS's in glxgears:

4582 frames in 5.0 seconds = 914.138 FPS
5737 frames in 5.0 seconds = 1147.253 FPS
5638 frames in 5.0 seconds = 1127.447 FPS
5589 frames in 5.0 seconds = 1117.650 FPS
5622 frames in 5.0 seconds = 1124.286 FPS
5649 frames in 5.0 seconds = 1129.635 FPS
4282 frames in 5.0 seconds = 856.380 FPS
4976 frames in 5.0 seconds = 995.135 FPS
645 frames in 5.2 seconds = 123.016 FPS
440 frames in 5.3 seconds = 83.295 FPS
729 frames in 5.0 seconds = 145.784 FPS
4687 frames in 5.0 seconds = 937.231 FPS
5582 frames in 5.0 seconds = 1115.732 FPS

Notice the incredibly low FPS's (123, 83, 145).  That's from taking the window with the gears and dragging it around real fast constantly.  Something about my graphics isn't right.  I just want to use Google Earth, for example.  That loads fine, but it only shows like the top third of the world when it starts, and that top third is spotted with blank spots.  What the heck is happening?  A similar thing also happens in games like Tux racer.  I installed a library (can't remember what it was called) libSDL (I think) and that hasn't solved the problem.  When I try to boot up cube (a game) in the terminal, it says:
**Unable to initialize SDL (No available video device)**

Does anyone know what's happening?

Thanks in advance!

---


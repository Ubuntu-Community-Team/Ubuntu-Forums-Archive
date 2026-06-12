---
title: "Slow dragging"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by Lazlo Falconi on 2006-12-08
Hey guys, I just installed Ubuntu for the first time and it's nice but... well slow. I know my computer isn't top of the line, but I've never had this problem with Windows XP.

Anyway, the problem is with smoothing. When I scroll down the page in a window, it seems to take forever and sorta jumps between areas. And when I drag windows around, they sit for a minute, then jump to my mouse' position, and jump again if I continue moving.

My computer doesn't seem to be having any troubles with all of this, in fact, it's sitting quieter than it does with Windows, so I figured I just hit a switch somewhere that told Ubuntu to be slow. :-k What do you think?

---

### Post by IYY on 2006-12-08
Can you post the specs of your computer? Mainly, the amount of RAM, video card memory and CPU speed. I've never seen dragging as slow as what you describe except for *very* old machines. It's possible that you do not have the correct video card drivers installed 

```
 grep Driver /etc/X11/xorg.conf
```

to check the drivers used (the video card driver is probably the last one). 

If you don't find a solution, you can simply switch of opaque resizing and moving of windows, but that doesn't look very nice.

---

### Post by Lazlo Falconi on 2006-12-08
[quote="Terminal"]        Driver          "kbd"
        Driver          "mouse"
  Driver        "wacom"
  Driver        "wacom"
  Driver        "wacom"
        Driver          "vesa"
[/quote]
Erm... I don't know what all of that is--Actually any of it. 

Anywho, I'm running this on my parent's computer now, because I'd rather screw theirs up before mine.. It's an eMachines (I know, they bought it without telling me.

It has 512MB RAM
A 1.8GHz AMD Sempron Processor
An nVidia GeForce 6100, but, being my parent's computer, I'm not sure what's going to it.

Crap. I thought they had an Intel chip. That's probably what did it.

**EDIT:** After paying closer attention, I note that I have a processor based around the x86 architecture anyway... so let me continue.

---

### Post by IYY on 2006-12-08
The video driver being used is Vesa, according to this line:

```
Driver "vesa"
```

It's a generic driver that works with almost every card, but is not what you actually want to be using. Most nVidia cards use the open source 'nv' driver by default, and an even better driver is the official 'nvidia'. I think that your particular card may not be supported by the nv driver, so you may have to install the official driver on your own.

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29)

---


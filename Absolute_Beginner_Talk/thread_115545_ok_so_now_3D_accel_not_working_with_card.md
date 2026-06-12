---
title: "ok so now 3D accel not working with card"
date: 2006-01-10
forum: Absolute Beginner Talk
---

### Post by alinuxfan on 2006-01-10
I have an ATI rage 128 pro AGP
and it doesn't seem to be working...I made nother post under my mouse pointer problem but figured i needed to start another....
I get the error
adam@ubuntu:~$ glxgears
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x30

Any idea how to change this...I read somewhere that I need to recompile my kernel...is this true?


I aslo get:
adam@ubuntu:~$ lspci | grep -i vga
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS

---

### Post by alinuxfan on 2006-01-10
well bah this sucks...i keep wishing I would have saved my copy of my xorg.conf file from my old system cause I had opengl and 3d support working....
gonna call it a night, maybe i just better get a new vid card  bah

---

### Post by az on 2006-01-11
Hoe much memory does it have?

Ubuntu defaults to using the maximum resolution at the maximum color depth.

I could not get acceleration going out-of-the-box on a card with 16 megs of ram because of this.  On another card with 32 megs, it worked out-of-the-box


In recovery mode I ran

dpkg-reconfigure xserver-xorg
and chose 1024x768 as the maximum resolution and I switched it to 16-bit color.

Then 

init 2

to get into the desktop.

I get impressive hardware acceleration, now.


Using high resolutions with high color depth seems to allocate the card's memory.  Even though you can tell gnome to use a lower resolution the memory is allocated.  You have to change this before you start X - hence the recovery mode.

---

### Post by alinuxfan on 2006-01-11
ok, somehow I messed something up in some other file than my xorg.conf file so I am doing a fresh install
Now, I started to doubt if my card was a 32mb card so I looked up the part number and it is 32mb...not sure why i am having the problems will try to reduce  the resolution and color depth and see what I end up with
thanks for the help

---

### Post by cgentry72 on 2006-01-11
I just recently installed Ubuntu and have really been pleased with the flexibility and stability.  One questions for now :), when I go to my screensavers, (using KDE btw instead of gnome as default) I notice a ton of screensavers that have GL after the name.  When I select a screensaver, nothing happens.  The screensaver doesn't appear to be working at all.  I only have two other ones that are not GL and they work fine. I'm afraid that OpenGL isn't installed or configured properly.  I also tried to run a game that requires OpenGL and it runs very very slow.  How can I fix this problem?

thank you in advance

---

### Post by az on 2006-01-11
[QUOTE=cgentry72]How can I fix this problem?

thank you in advance[/QUOTE]


It depends on your video card.  What does the device manager show it as?

(You can also post the output of 
lspci 
in Konsole)

---


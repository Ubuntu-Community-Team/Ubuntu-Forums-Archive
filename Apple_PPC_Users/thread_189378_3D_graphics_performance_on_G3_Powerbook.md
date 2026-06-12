---
title: "3D graphics performance on G3 Powerbook"
date: 2006-06-05
forum: Apple PPC Users
---

### Post by matthewedwinmiller on 2006-06-05
Hi everone, first post & new Linux user here :)

Ive just installed 6.06 on my old G3 Powerbook (Lombard).  One of the first things I noticed after the installation to the drive was that the screensavers that depend on 3D were running pretty slowly.  Is there some way of updating the display drivers, or installing some type of 3D support package on this system to improve performance?

as far as I can tell, this is a G3 400MHz PPC, cant remember how much (or find a way to confirm) system RAM.  LCD Display is set to 1024x768, 85Hz (dont see a way to confirm or change color depth).  It's a little frustrating that I cant easily see my own system specs, I've looked through the Administration tools that would make sense, but none seem to tell me the basics of my hardware or display.

thanks for your help!

---

### Post by ssam on 2006-06-05
hi

there is system -> administration -> deveice manager, which will tell you quite a bit about your hardware. you should be able to see which graphics card you have in here.

the command
```
free -m
```
will tell you how much ram you have in MB. (dont panic if it claims that nearly all you ram is being used. linux considers free memory to be wasted memory and uses it for disk buffering/caching).

if you could attach the file /etc/X11/xorg.conf, maybe someone could spot something that could be done to speed things up.

---

### Post by daft_ska on 2006-06-17
This is a common problem with rage 128 graphics cards.
Something is wrong with CCEIdle, although I have no idea what that is. :)
Anywho, the fix can be found at:

[https://launchpad.net/distros/ubuntu/+source/mesa/+bug/24810](https://launchpad.net/distros/ubuntu/+source/mesa/+bug/24810)

about halfway down the page the user "Conn" has a file to download and then instruction on how to patch it all up and get DRI working properly.

Good luck!

---

### Post by Rxke on 2006-06-17
Man, I sure hope that works, I successfully compiled the game Oolite for PPC, and it kept giving me the timeout error, despite it otherwise running 100%

(crosses fingers)

Edit: patch installed w/o hassles, xcept where it says sudo dpkg -i xserver-xorg-driver-ati_x.x.x.x-xubuntux_i386.deb you have to of course use the powerpc.deb, which you get prompted during the whole stuff. Now recompiling Oolite (i threw it away, after last failed attempt)

(Edit: ) Oolite stills times out my Rage 128 :(

---


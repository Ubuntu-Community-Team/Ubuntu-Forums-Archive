---
title: "screensaver problem"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by jpl007 on 2007-09-20
I'm just getting started w/ Ubuntu, and am having a problem.  When I try to change the screensaver to one of the ant screensavers on 7.04, it crashes the machine.  So I tried the LiveCD that I made and it does the same thing.  I used the "check CD" option on the startup screen and it checks out OK, as did the MD5 sums on download.

Any one else w/ this problem?

Thanks

---

### Post by overdrank on 2007-09-20
> **jpl007 said:**
> I'm just getting started w/ Ubuntu, and am having a problem.  When I try to change the screensaver to one of the ant screensavers on 7.04, it crashes the machine.  So I tried the LiveCD that I made and it does the same thing.  I used the "check CD" option on the startup screen and it checks out OK, as did the MD5 sums on download.

Any one else w/ this problem?

Thanks

Hi and welcome, could you tell us the model of you graphics card. You can use the command in the terminal 
```
lspci
```
Then terminal is located under applications, accessories, terminal and copy and paste the output here.

---

### Post by jpl007 on 2007-09-21
I'm actually using the graphics unit built into the motherboard.

from the terminal:

01:00.0 VGA compatible controller; VIA Technologies, Inc. S3 Unichrome Pro VGA adapter (rev 01)

---

### Post by overdrank on 2007-09-21
> **jpl007 said:**
> I'm actually using the graphics unit built into the motherboard.

from the terminal:

01:00.0 VGA compatible controller; VIA Technologies, Inc. S3 Unichrome Pro VGA adapter (rev 01)

Ok unichrome is not really that great but it should work. Is this a laptop or a desktop? If this is the onboard video then you may be able to increase the amount of memory shared with the graphics in the bios. :)

---

### Post by joecool362 on 2007-09-21
:lolflag:If you don't have a good 3D graphics card the 3D screensavers don't work

---

### Post by perixx on 2007-10-13
Don't know, but could it be that it's a similar problem like with the ATI Rage 128 card types and the 'molecule' screensaver? 
Many people have encoutered hang-ups with this combination under Ubuntu and also under Xubuntu. I managed to find a workaround for the latter, (Ubuntu was already solved before): 

[http://ubuntuforums.org/showthread.php?t=571810&highlight=screensaver+crashes+system](http://ubuntuforums.org/showthread.php?t=571810&highlight=screensaver+crashes+system)

Maybe this is also a bug in the screensaver... if so, you simply cannot use this specific screensaver. To recover you from the hang-up misery, delete the non-working screensavers from your screensavers configuration file, as described in the link above - or, I don't know about the Ubuntu (Gnome?) Desktop's screensaver-setup-file - it might possibly be 

/home/USERNAME/screensaver 

your have to look for yourself, if you're using the Gnome desktop.

Hope it helps you :)


perixx

---


---
title: "Newbie trying to install intel 810 graphics driver"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by crash331 on 2006-08-14
I am very new to Linux, only had it about 2 days.  I have most things working right except DVD playback.  It will only display the right colors of I use opengl to play dvds, but it runs very slow.  If I choose the other drivers, the gamme and color is way off.  I read somehwere else that it is a know bug and a driver problem on the intel 810 chipset and I found a driver that someone claimed would fix it.  So my question is now what do I do with these files?  Forgive me, but I come from windows where I click an exe and go. All I see are sh files and stuff like that.  Do I need to go into the terminal and compile this or run it somehow?  Please help.

---

### Post by GuitarHero on 2006-08-14
Did the driver come with a read me or installation file?

---

### Post by crash331 on 2006-08-14
It did, but the readme doesn't have any instructions as far as I can see.

[http://xorg.freedesktop.org/releases/individual/driver/xf86-video-i810-1.6.5.tar.bz2](http://xorg.freedesktop.org/releases/individual/driver/xf86-video-i810-1.6.5.tar.bz2)

---

### Post by crash331 on 2006-08-14
[https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-i810/+bug/32963](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-i810/+bug/32963)

That is the bug, if anyone knows of a different fix.  Installing a new driver when I know nothing about it sounds like a sure fire way for me to screw something up.

---

### Post by nalmeth on 2006-08-14
The i810 driver is included with Ubuntu. You are probably using it right now. Or is this some modified driver??

I've gone thru a lot of what you have, except for the slow mplayer playback. I've found that kaffeine works perfectly. I think it's using the xv driver right now. No weird colors or slow playback.

Any more info on the driver you're trying to install?

---


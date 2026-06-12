---
title: "KDE not starting"
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by Eltern on 2006-04-16
Just installed Kubuntu on my brother's desktop, which uses an NVIDIA Geforce video card, and KDE isn't working right. It'll boot just fine and go through the start up sequence, but then on tty7 we'll just get a black screen with the blinking white cursor. I hoped over to tty5 and typed sudo /etc/initi.d/kdm restart, and it gave me
"Stopping K Display manager: kdm.
Starting K Display Manager: kdm."

Went back over to tty7, and the same situation. Suggestions?

It seems that KDE is definitely installed. Could it be an issue of the video card? If so, would Gnome have different results?

Thanks!

---

### Post by gingermark on 2006-04-16
In recovery mode try a 'sudo dpkg-reconfigure xserver-xorg' and select the "vesa" driver. If X then starts properly it will be a driver problem. 

[This thread](http://www.ubuntuforums.org/showthread.php?t=75074) will guide you through the various driver options available.

---

### Post by htinn on 2006-04-16
It sounds like your X server isn't configured properly for your video card/monitor.

I don't know if there's a handy guide for Ubuntu, but here's one for Gentoo (parts of it may help you out):

[http://www.gentoo.org/doc/en/xorg-config.xml](http://www.gentoo.org/doc/en/xorg-config.xml)

EDIT: Here's the one for Ubuntu:

[https://wiki.ubuntu.com/FixVideoResolutionHowto](https://wiki.ubuntu.com/FixVideoResolutionHowto)

---


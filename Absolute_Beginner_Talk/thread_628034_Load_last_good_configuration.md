---
title: "Load last good configuration"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by thats_Mr_noob_to_you on 2007-11-30
OK, I don't know if I could have had any more hardware that is a pain to set up in Ubuntu, an ATI 1950 graphics card, Dual Monitors (with monitor 2 left of 1, and both different sizes), and an intel 537 ep fax modem (which I receive about 50 faxes per day on my home office computer).

So far, following guides, and a bit of trial and error, I have been able to get to a point where I can get the proprietary driver installed so that both monitors function correctly. Now I am at a point of enabling 3d, installing fglrx, going crazy with compiz, etc.

In the past, when I got to a point where I didn't know how to undo my recent changes, I would format and reinstall. 

*_So my question is:_* Is there a how to guide, or *fingers crossed* a program that will save a working configuration of drivers, xorg.conf, etc. so that when I make a change, if things don't work, I can load up some working settings from maybe the login screen or even from grub?

---

### Post by foolsh on 2007-11-30
cp 
cp is the program your looking for the end all says all of making a backup xorg file
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```
to restore type the reverse
```
sudo cp /etc/X11/xorg.conf-backup /etc/X11/xorg.conf
```
If something goes wrong you wont get the graphical login screen just a text login prompt
Don't fear the command prompt use it.
but not from grub the root file system hasn't been mounted yet, I assume.

---

### Post by thats_Mr_noob_to_you on 2007-11-30
Yeah, I got really good at going from the login screen to <alt><ctrl>F1 sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf

sometimes getting aticonfig to work right is a bit of a pain, but the one thing I can count on it for is making extra backups of xorg.conf

The problem I'm running into now is that, sometimes restoring my backup xorg.conf doesn't revert things back to a working setup

---


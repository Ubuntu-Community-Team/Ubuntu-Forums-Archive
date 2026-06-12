---
title: "No mouse and trackpoint does not work either"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by DesertBear on 2007-09-01
Hello,

I have managed to install Ubuntu to a Fujitsu Lifebook B2562.  Because the system wouldn't boot from the USB CD-ROM, I installed Ubuntu by hooking up the laptop harddrive to my desktop.  After fixing the graphics from [http://ubuntuforums.org/showthread.php?t=500696](http://ubuntuforums.org/showthread.php?t=500696), I can now get to Ubuntu desktop, which is very cool, but the trackpoint thingy doesn't work (and I don't have a USB mouse). 

How do I reconfigure the sytem to recognize the trackpoint?

Thank you in advance for any help!
DesertBear

Fujitsu Lifebook 2562
Ubuntu 7.04

---

### Post by SOULRiDER on 2007-09-02
Im not sure but i believe xorg handles that. Try reconfiguring it.

First back it up:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
Then reconfigure
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by DesertBear on 2007-09-02
Well, I tried that a few times with different options but it does not seem to change anything (as I recall it only asks how to handle the mouse in 1 window).  Are there custom options for the trackpoint-er?

---


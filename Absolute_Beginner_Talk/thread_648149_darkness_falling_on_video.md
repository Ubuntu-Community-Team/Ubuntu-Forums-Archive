---
title: "darkness falling on video"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by blackpit on 2007-12-23
Hi guys.I've recently dual-booted ubuntu gutsy with windows xp on my pc.Ever since I've been trying to fix various issues but overall it worked ok.The biggest problem is that ubuntu doesn't seem to support my video card(via s3 unichrome pro intergrated graphics).Last night a more experienced friend of mine came over in an attempt to optimize my system.He installed automatix and various updates and everything seemed to be fine until we tried to open a video file.We tried various video formats with various video players and the same weird thing keeps on happening.Blackness starts to fill the screen, slowly from top to bottom and everything freezes.My friend tried uninstalling automatix and several other things which I'm not really acquianted with but tough luck.Any suggestions would be highly appreciated.

---

### Post by buzzmandt on 2007-12-23
what player are you using and have you tried vlc?

---

### Post by SOULRiDER on 2007-12-23
Automatix is horrible. Did you have these issues before he installed it?
Just in case, are the video drivers installed? 
Chech this out, there are packages for ubuntu that will install the drivers [http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=Collection+of+contributed+binary+packages](http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=Collection+of+contributed+binary+packages)

Once installed press alt + f2 and type
```
gksu gedit /etc/X11/xorg.conf
``` and look for the section that looks like:
```
 Section "Device"
Identifier "VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
Driver "via"
BusID "PCI:1:0:0"
Option "DisableIRQ"
Option "EnableAGPDMA"
EndSection

```

and change via (where it says Driver) to openchrome. INSTALL THE DRIVERS FIRST from the link I gave you or you will not be able to get into GNOME. If youre already using thoe drivers, change it back to via and see what happens.

---

### Post by SOULRiDER on 2007-12-23
I just found thsi on the forums thatw ill compile form source, check it out.
[http://ubuntuforums.org/showthread.php?t=485646](http://ubuntuforums.org/showthread.php?t=485646)

Also, if you come across any issues those people might be able to help you.

---

### Post by blackpit on 2007-12-23
I installed the drivers manually from openchrome and the problem was solved.I still don't have 3D graphics but it at least i can work in 2D with no problems.Thanks.

---


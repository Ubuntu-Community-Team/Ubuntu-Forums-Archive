---
title: "Disk Error 0xAA!"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by HedgeHog74 on 2007-08-14
What does this mean: Disk Error 0xAA?

I just got the sbm to work, but now it won't let me boot my CD-ROM drive!  How convenient.  I have the Ubuntu Live CD in the drive, but it's not booting...this is really strange.  I changed the boot order to make the CD-ROM first in both the BIOS and sbm, still doesn't boot!  Is there a way I can just put the Ubuntu image on one of my empty hard drives and install it from there, or create an image of the CD on the the HD and change the boot sequence?  Any thoughts?  Please help, I'm really trying to get away from windows for security purposes.  My first attempt was with Solaris 10 OS, no luck yet.  

HH

P.S.- I was trying this with the Ubuntu 7.04...should I try it with 6.06 instead?  I have both images on different CDs (both burned at 1x, took about 90 minutes for each one!).  Also, see [this thread](http://ubuntuforums.org/showthread.php?t=132370) for my computer specs if you think there's something else I should try.

---

### Post by milosz.galazka on 2007-08-15
"If there is no CD in the drive, sbm complains about a "Disk error! 0xAA" and if you hit any key, SBM enters its Boot menu. The same happens, if the directory of the CD is not yet loaded, or if the drive cannot read it (e.g. RW disk in an older drive), so it is worth while to retry loading the CD by hitting any key in response to the "Disk error! 0xAA" message and Enter on the (highlighted) CD-ROM line in SBMs Boot Menu."
Source: [http://www.lrz-muenchen.de/~bernhard/grub-chain-cd.html](http://www.lrz-muenchen.de/~bernhard/grub-chain-cd.html)

Look at [https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

---


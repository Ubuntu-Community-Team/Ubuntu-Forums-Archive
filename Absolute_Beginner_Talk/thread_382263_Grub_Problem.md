---
title: "Grub Problem"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by TheTownSheriff on 2007-03-11
Hello Everyone,

Installed Version :  Ubuntu Edgy Eft  (Ubuntu Ultimate Edition 1.2)

I am a first-time linux user and have been playing around with my new Ubuntu install, in the process of trying lots of things I messed a bunch of stuff up, and decided to just re-install Ubuntu again instead of trying to fix the things I broke.  The problem I have run into is with Grub.  It is still installed on my MBR, and still boots to Grbu when I boot up my computer with the choice of the two linux kernels and WinXP.  However, when I select any of them it says "cannot find" or "will not boot" or something to that extent.  I logged on to IRC and someone refered me to this page: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-f5b2b33b369cf4e319ad0f1df557c42290ba2d33](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-f5b2b33b369cf4e319ad0f1df557c42290ba2d33)
I followed the directions, but it did not correct the problem.  I think that page is more for if Grub is no longer on the MBR.  My problem seems to be that Grub is looking in the wrong place for the boot partitions?  When I insert my Ubuntu CD the last option on the list is "boot from first hard drive" if I select that option, it kicks me out to Grub and both my linux and windows partitions boot up as they should.  I looked at the lines in both the non-working Grub (when I boot) and the lines in the one that works when I go through the CD-boot way and they are identical :(  Therefore, I do not know what else to try, if anyone could help me it would be much appreciated. Thank you in advance.
TownSheriff

---

### Post by Jonam on 2007-03-12
I had similar problems and ended up using the LiveCD to fix things as outlined in:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Regards,

Jonam

---

### Post by TheTownSheriff on 2007-03-12
Thank you very much! Fixed the problem.

---


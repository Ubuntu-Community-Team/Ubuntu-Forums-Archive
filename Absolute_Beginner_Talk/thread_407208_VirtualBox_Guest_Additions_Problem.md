---
title: "VirtualBox Guest Additions Problem"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by kremser on 2007-04-11
I am running Ubuntu Edgy 6.10 and trying to set up VirtualBox to run a virtual WinXP.  I have installed VirtualBox, have set up the New Drive, then go to the Device manager to mount the CD to Run the ISO file.  Once i select the additions ISO, nothing happens.  According to the user's manual it should be autorun.  I reset and i get a message saying, "FATAL: Could not read from the boot medium! System halted."  What am i doing wrong?  How can i get Windows XP running?  Thanks!

---

### Post by troymcdavis on 2007-05-06
It seems as if you are trying to boot from the Guest Additions ISO, which isn't a bootable image. See if you can get the WinXP image running without any guest additions, then once you are running XP, click "Devices" in the VirtualBox window for that session, then click "Install Guest Additions." It takes over from there, if I remember correctly.

---


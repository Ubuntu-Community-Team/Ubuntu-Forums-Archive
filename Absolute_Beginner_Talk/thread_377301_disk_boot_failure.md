---
title: "disk boot failure"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by LieToPurify3 on 2007-03-05
im new to all linux. i tried installing ubuntu from the live cd, but it stopped during the reboot every time. so i tried the alternative install cd, but when it reboots after i take the cd out after install, it says disk boot failure and that i need to put the cd back in. whats wrong with it?

---

### Post by BarfBag on 2007-03-05
Try moving the hard drive to the first place in your boot order.  This is done in bios.  If that doesn't work, the installation probably failed before it installed Grub (the boot loader).  If that's the case, you have to either clear the MBR or install a Linux distro; or else it won't boot anymore.  Try my first suggestion, then we can go into more detail about my second.

---


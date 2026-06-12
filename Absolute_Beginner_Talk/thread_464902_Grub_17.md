---
title: "Grub 17"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by harshasunder on 2007-06-05
I installed ubuntu today morning for the first time, on a computer with win xp .I followed the instructions while installing mostly, and went ahead with the automatic partition suggestions. if i remember correctly it made a 5.2 gb partition though im not sure about specifics...Now its giving me a grub 17 error and nothings happening. ive been looking through all the forums and thread with the same problems and tried to reinstall grub from terminal using this command- setup (hd0) though if i typed find /boot/grub/stage1 i got (hd0,2)..so basically i dont know what to do..i downloaded ultimate boot cd because one of the forums said it could fix the problem but im not sure how to do it..so..anybody please?

i just browsed some more, and now ve found out that the correct way to go about a dual boot is to reduce the partition to 0 gb while installing( [http://psychocats.net/ubuntu/installingdapperedgy](http://psychocats.net/ubuntu/installingdapperedgy))  ..so how do i just fix this grub problem, and then uninstall ubuntu? then ill install it properly again

---

### Post by alienexplorers on 2007-06-05
Put in your windows xp disk and boot into recovery mode.  Enter fixmbr & fixboot.  Then reboot and windows should start.  Next use xp's partition manager and clear out the ubuntu partitions.  Reboot.  Put in your livecd for ubuntu and install it.  It should create a dual boot system.  Reboot and hope for the best.

---


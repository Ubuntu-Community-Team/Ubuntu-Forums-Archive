---
title: "Where does Ubuntu install Grub by default?"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by leavingOS2 on 2007-01-05
When using the Ubuntu live CD (6.06) to install from, where would it put Grub by default?  The MBR? The /boot partition? (even if /boot and root are on separate partitions?

I intend to have /boot on a primary partition and / on a logical.  I plan to use IBM's Boot Manager on a primary partition as a loader, and I'm told I have to be careful about the interaction between it and Grub.

---

### Post by meng on 2007-01-05
MBR by default.

---

### Post by leavingOS2 on 2007-01-05
During the live CD installation, can you specify an alternate location (e.g., on the /boot partition)?  After installation, can it be moved?  If so, how?

Thanks

---

### Post by meng on 2007-01-05
You need to use the Alternate CD and answer "no" when asked to install grub to MBR.

---

### Post by Duck2006 on 2007-01-05
6 of 6 in the install there is a box with hd0 in it you can change to load the grub in witch ever drive you want 

ie. your primary drive is hd0, 
     and the second is the slave hd0,
you can tell it to place the loader on that drive with will let you use a different boot loader to boot your ubuntu linux from

---

### Post by Duck2006 on 2007-01-05
Edit: and the second is the slave hd0 sould read hd1

---


---
title: "Grub error 18"
date: 2005-08-27
forum: Absolute Beginner Talk
---

### Post by gandalf458 on 2005-08-27
I've just got my ubuntu CD and tried to install it on an old m/c and when it got to stage 1.5 (I think) I received a GRUB error 18. I tried Linspire before and got a GRUB error 17 which seemed insurmountable. I'm just wondering if my present predicament can be fixed before I donate the m/c to my local recycling centre...

---

### Post by tonym on 2005-08-27
I found [this article](http://forums.gentoo.org/viewtopic.php?t=122656) via Google.  If it is correct it implies that your machine can only boot from the first so many cylinders of the disk - which can apply to older machines.  To get round this you may need to repartition your disk.  Put a small partition (50 - 100 Mbytes) at the start of the disk,  when you install put /boot on this partition and when the installation asks where to put grub specify either the master boot record or the /boot partition.

---

### Post by nic2 on 2005-08-27
[https://wiki.ubuntu.com/WartyWarthogInstallNotes?highlight=%28error%29%7C%2818%29](https://wiki.ubuntu.com/WartyWarthogInstallNotes?highlight=%28error%29%7C%2818%29)

---

### Post by gandalf458 on 2005-10-11
I've only just found my post and your replies - thanks and sorry. Can't get into the wiki this morning. However, I found with some help that changing the disk type from "user" to "auto" in the BIOS did the trick.

---


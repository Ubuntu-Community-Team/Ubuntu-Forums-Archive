---
title: "WinXP+Ubuntu+Redhat+Mandrake"
date: 2006-01-03
forum: Absolute Beginner Talk
---

### Post by wingknight on 2006-01-03
hi. i want to try and compare the abovementioned flavors of linux. is there any guide how to install the 3 linux os in a 160GB HDD. currently, i have windows xp installed.

is it also possible to boot the 4 os using only one bootloader (preferably GRUB)? how can i do it? i prefer detailed guide since i'm new to multiboot os.

---

### Post by aysiu on 2006-01-03
Here's what I would do (having quadruple-booted before):

1. Make sure Windows XP is installed properly.

2. Back up all important documents.

3. Install Mandriva. Part of the Mandriva installation process is a partitioning program called DiskDrake--this is the best/easiest to use partitioning program I've ever seen--use it to shrink the Windows XP NTFS partition, and create three Ext3 partitions and a small swap partition (make this last partition twice the size of your RAM). Install Mandriva to one of your Ext3 partitions and install Grub (not Lilo) to the boot folder of the root partition.

4. Install Red Hat to one of the other Ext3 partitions and install Grub to the boot  folder of the root partition.

5. Install Ubuntu to the last Ext3 partition and install Grub to the Master Boot Record (MBR). Ubuntu's Grub will automatically add Windows XP to the Grub menu. It may or may not add Mandriva and Red Hat automatically. If it doesn't, you can add the entries in manually by looking at the Grub entries on the Red Hat and Mandriva partitions and copying them over to Ubuntu's Grub (use Ubuntu's Grub entry format--don't just copy and paste entire entries). You can view the other partitions by mounting them, or if you don't know how to mount, pop a live CD in (like Knoppix) and view the partitions that way.

---

### Post by davmac on 2006-01-03
...and coincidentally I've just stumbled across this excellent article by IBM on boot loaders. Have a look at [http://www-128.ibm.com/developerworks/library/l-bootload.html?ca=dgr-lnxw01LILOandGRUB](http://www-128.ibm.com/developerworks/library/l-bootload.html?ca=dgr-lnxw01LILOandGRUB)

Regards,

Dave Mac

---

### Post by wingknight on 2006-01-03
thanks. i'll give it a shot. hope to get it right and boot the 4 os properly. ;)

---


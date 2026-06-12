---
title: "Error 22: No Such Partition"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by Shane01638 on 2007-07-05
Can't install the new Ubuntu.  I've tried the 32 and 64 bit version.  I'm using hd1 and grub is picking up some leftover Vista stuff even though I've formatted that partition.  The live cd works fine and it installs fine, but when it reboots after the install any option I select on the boot loader says Error 22: No Such Partition. I have 100mb on hd1 partition 4 for /boot.  I have 10gb on hd1 partition 5 for / and 2gb on hd1 partition 7 for swap.  Partition 6 is my fat32 OS share partition.  Will ubuntu run on an extended partition at the end of the drive?  That's the only thing I can think of that might be the problem.  I set my bios to boot off my second hard drive so it doesn't mess with windows and I select Advanced at the verification screen and set the boot drive to (hd1) instead of 0.  I have no problem installing fc7 64bit on the exact same partitions.  Could it be the junk in the MBR left over from previous OS's?  Thanks in advance!

---

### Post by Hobo Joe on 2007-07-05
Do you have anything besides Ubuntu installed on the system?

---

### Post by confused57 on 2007-07-05
> **Shane01638 said:**
> Can't install the new Ubuntu.  I've tried the 32 and 64 bit version.  I'm using hd1 and grub is picking up some leftover Vista stuff even though I've formatted that partition.  The live cd works fine and it installs fine, but when it reboots after the install any option I select on the boot loader says Error 22: No Such Partition. I have 100mb on hd1 partition 4 for /boot.  I have 10gb on hd1 partition 5 for / and 2gb on hd1 partition 7 for swap.  Partition 6 is my fat32 OS share partition.  Will ubuntu run on an extended partition at the end of the drive?  That's the only thing I can think of that might be the problem.  I set my bios to boot off my second hard drive so it doesn't mess with windows and I select Advanced at the verification screen and set the boot drive to (hd1) instead of 0.  I have no problem installing fc7 64bit on the exact same partitions.  Could it be the junk in the MBR left over from previous OS's?  Thanks in advance!

Boot the live cd, open a terminal(Applications---Accessories---Terminal), post the output of:
```
sudo fdisk -l
```
-l is a small "L"

If you get a grub boot menu when you boot to your (hd1), highlight your Ubuntu entry, press "e", change root from (hd1,x) to (hd0,x), then press "b" to boot...

---

### Post by Shane01638 on 2007-07-05
setting grub to hd0 instead of hd1 fixed it.  I thought since the harddrive I installed and booted ubuntu from was a Primary/Slave, it would be hd0.  It works anyway.  Thanks!

---


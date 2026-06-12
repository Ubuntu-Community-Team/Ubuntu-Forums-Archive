---
title: "Read FAT32 Partition?"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by Xomphos on 2007-02-14
Hi,

I just finished installing my dual-boot setup. On my primary hdd (80GB), I have the partitions set up as follows:
-20 GB (Windows XP - NTFS)
-20 GB (Ubuntu 6.0.6.1)
-39 GB (Fat32 - Shared Between Windows XP and Ubuntu)
-1 GB (Swap Space)
I also have a 30GB NTFS formatted internal HDD (slave drive) that I use for backup.

Anyways, the dual-boot went successful! However, I for some reason cannot access the 39 GB Fat32 partition within Ubuntu. The mounting point (from the tutorial I used) is supposedly /windows. I can see the partition fine in Windows, but it is the only thing I can't even read from in Ubuntu. How can I find it? Also, when I boot into Windows XP from the GRUB boot loader after using Ubuntu, it wants to check my NTFS partition for consistancy. So far I have skipped these checks (2), but is there a way so that Windows XP doesn't even bug me about it?

Thanks a lot for your help! :D

---

### Post by jimrz on 2007-02-14
> **Xomphos said:**
> Hi,

I just finished installing my dual-boot setup. On my primary hdd (80GB), I have the partitions set up as follows:
-20 GB (Windows XP - NTFS)
-20 GB (Ubuntu 6.0.6.1)
-39 GB (Fat32 - Shared Between Windows XP and Ubuntu)
-1 GB (Swap Space)
I also have a 30GB NTFS formatted internal HDD (slave drive) that I use for backup.

Anyways, the dual-boot went successful! However, I for some reason cannot access the 39 GB Fat32 partition within Ubuntu. The mounting point (from the tutorial I used) is supposedly /windows. I can see the partition fine in Windows, but it is the only thing I can't even read from in Ubuntu. How can I find it? Also, when I boot into Windows XP from the GRUB boot loader after using Ubuntu, it wants to check my NTFS partition for consistancy. So far I have skipped these checks (2), but is there a way so that Windows XP doesn't even bug me about it?

Thanks a lot for your help! :D

[Here]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only") is a guide to mounting your Fat32 partition in Ubuntu...be sure to read far enough to get to the part that shows how to set it to mount automajically each time you boot. Youcan also mount your NTFS partion, though it will be read-only, following this same guide.

---

### Post by tonyr1988 on 2007-02-14
Are you sure you're not mounting your WinXP partition and not your Fat32 partition? If you still need help after that guide, please post the contents of /etc/fstab and the output of:

> sudo fdisk -l

(that's a lowercase L, not a number 1) (the "sudo fdisk -l" goes in the Application -> Accessories -> Terminal)

---

### Post by Xomphos on 2007-02-15
Nevermind, I found it-it was in 'Filesystem'-'Windows'
Is there a way to place a HDD icon shortcut on the desktop for it?

Thank-you! :D

---


---
title: "Cannot move /home to a vfat32 partition"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by jomasall on 2007-12-22
Hi all,
I've installed Ubuntu 7.10 the way: 25Mb on sda2 (NTFS) for win XP, 20Gb on sda3 (ext3) for ubuntu, sda4 for swap and 70 Gb on sda5 (FAT32) for data sharing with WinXP.
I've mounted the /home on the ext3 partition on the installation, but now I would like to move to the sda5 partition, in order to have all my data in  /home/pep and to share it with windows (it's FAT32)

To tray to do this, I 've moved the /home to /home.old, then mkdir /home, then mount the sda5 in /home, then edit fsstab, and finally I tried to move my /home.old/pep to the new /home/pep (in sda5), but this last step doesn't work, I cannot move the files.

So I would like to aks 2 things:
Is a good idea to have yout /home in a FAT32 partition that way?
In case yes, how can I do it?

Thanks in advance, and sorry about my english...

Josep

---

### Post by taurus on 2007-12-22
It is extremely bad idea to use fat32/vfat for /home because fat32 doesn't use permissions like in Unix/Linux.  If you want to share data with windows, create a share directory.  However, do you know that you can write to ext3 filesystem, /home/username, from windows if you use fs-drvier, [http://www.fs-driver.org/?](http://www.fs-driver.org/?)

---


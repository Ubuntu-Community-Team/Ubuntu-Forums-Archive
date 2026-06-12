---
title: "USB Harddisk question"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2007-08-19
I have a usb harddisk that i need to be portable and occasionally use on windows systems. Its 500GB big and i want to know the best FS to use.

AFAIK 
Linux cannot write NTFS
Windows cannot read FS2/3

That leaves me with FAT32 (is this too big at 500G?) if not thats ok, but i cannot find a way in linux to change the volume name which is important for backups.

The other option is Unformatted (found it by accident) is this ok to use? it seems to mount ok, but should i trust it?

---

### Post by taurus on 2007-08-19
Ubuntu can write to ntfs with ntfs-3g driver, [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G).

Windows can read/write to ext3 with [http://www.fs-driver.org/](http://www.fs-driver.org/).

---

### Post by kevinatkins on 2007-08-19
Hi,

I'd suggest sticking with FAT32. You can use volumes up to 2TB with FAT32 (although Windows XP / Vista will only allow you to create volumes up to 32GB in size, that's an artificially low limit and they will read larger FAT32 volumes, so you're OK). The maximum file size with FAT32 is 4GB, so bear that in mind if you're going to be using large files.

I'd stay away from NTFS for the moment - it's a better, more reliable filesystem than FAT, but Linux support is still not as mature as for FAT32.

You could use Linux ext2/3 - there are tools available for Windows which will allow you to read either of those filesystems.

---


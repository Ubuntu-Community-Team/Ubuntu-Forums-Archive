---
title: "Ubuntu 6.06 and hda2 Mount Problem.."
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by JustDon on 2007-07-07
I have my Windows XP partition mounted in Ubuntu 6.06. I can access files, open, read and print them BUT I cannot alter them at all. Here is my fstab file:

# /etc/fstab: static file system information.
 #
 #
 proc /proc proc defaults 0 0
 /dev/hda5 / ext3 defaults,errors=remount-ro 0
 1
 /dev/hda1 /home/dhatcher2/hda1 vfat
 defaults,utf8,umask=007,gid=46 0 1
 /dev/hda2 /home/dhatcher2/hda2 ntfs
 defaults,nls=utf8,umask=007,gid=46 0 1
 /dev/hda3 /home/dhatcher2/hda3 vfat
 defaults,utf8,umask=007,gid=46 0 1
 /dev/hda6 none swap sw 0 0
 /dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

The paste format may be a little off but the information is there. Notice that hda2 is formatted in NTFS, can Ubuntu write to NTFS? Othewise, any idea why this may be happening. I need to be able to access and change these files in order to migrate to Linux fully.

Thanks in advance for any help.

---

### Post by mysticrider92 on 2007-07-07
You have to install drivers for Ubuntu to write to ntfs partitions. There is a driver called 'ntfs-3g' but I could not get it working in Dapper (my dad has that on his laptop). I would recommend installing Automatix2. There is a script that you can install through it to automount ntfs and fat32 partitions.

---

### Post by JustDon on 2007-07-17
> **mysticrider92 said:**
> You have to install drivers for Ubuntu to write to ntfs partitions. There is a driver called 'ntfs-3g' but I could not get it working in Dapper (my dad has that on his laptop). I would recommend installing Automatix2. There is a script that you can install through it to automount ntfs and fat32 partitions.

Thanks, I have had nothing but trouble with AutoMatix so I am just going to drag over all my files to my Ubuntu Home Folder and use them directly from Linux. Thanks Again.

---


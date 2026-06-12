---
title: "Help accessing files in NTFS"
date: 2005-12-28
forum: Absolute Beginner Talk
---

### Post by lemmy999 on 2005-12-28
hello! I'm a noob!

Having installed Breezy on a spare HDD and been pretty happy with it ( we wont talk about the printer-yet!) i would like to migrate all my MP3s/ebooks/video etc from my old windows slave HDD. Disk manager detects the disk. I have installed Samba which also sees the drive ( i think!) 

What do i have to do now??

---

### Post by aysiu on 2005-12-28
See the fourth link in my sig.

---

### Post by lemmy999 on 2005-12-28
Ok i have been following  the instructions, my windows disk is  /dev/hda1. 
the fstab output is as follows

  GNU nano 1.3.8             File: /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Can i edit this and if so how?

Thanks

---

### Post by [Nirvana] on 2005-12-28
[QUOTE=lemmy999]Ok i have been following  the instructions, my windows disk is  /dev/hda1. 
the fstab output is as follows

  GNU nano 1.3.8             File: /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
**/dev/hda1 /media/windows ntfs nls=utf8,umask=0222 0  0**
Can i edit this and if so how?

Thanks[/QUOTE]

I'm not too sure about it, but try that. Also, make sure /media/windows exists, or it will fail.

---

### Post by lemmy999 on 2005-12-28
OK followed the instructions (as best i could) output now is

chris@chris:~$ sudo cp /etc/fstab /etc/fstab_backup
chris@chris:~$ sudo nano /etc/fstab
chris@chris:~$ sudo mount -a
Password:
mount: mount point /media/windows does not exist
mount: mount point /fat_files does not exist
  
My original concern was that fstab didnt appear to show hda1 at all. Maybe thats where the problem is?

---

### Post by lemmy999 on 2005-12-28
Created a /media/windows folder. got a new error message suggesting the I try dmesg. output is as follows

chris@chris:~$ dmesg | tail
[4294758.542000] Bluetooth: RFCOMM socket layer initialized
[4294758.542000] Bluetooth: RFCOMM TTY layer initialized
[4294930.156000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4309493.114000] NTFS driver 2.1.22 [Flags: R/O MODULE].
[4309493.115000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Primary b oot sector is invalid.
[4309493.115000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Mount opt ion errors=recover not used. Aborting without trying to recover.
[4309493.115000] NTFS-fs error (device hda1): ntfs_fill_super(): Not an NTFS vol ume.
[4309619.309000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Primary b oot sector is invalid.
[4309619.309000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Mount opt ion errors=recover not used. Aborting without trying to recover.
[4309619.309000] NTFS-fs error (device hda1): ntfs_fill_super(): Not an NTFS vol ume.

Any thoughts ?

---


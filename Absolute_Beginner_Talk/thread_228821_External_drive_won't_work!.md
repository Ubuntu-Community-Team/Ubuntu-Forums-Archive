---
title: "External drive won't work!"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by cheway on 2006-08-03
Hi all,

I just tried to plug in my external drive to do a backup before I reinstall, and it doesn't seem to be popping up on the desktop the way it should be. I've tried with both USB and Firewire, nothing. It's currently formatted with NTFS, my intention was to format it with ext3, and then put my files over.

Any ideas? I have a USB flash disk that works no problem, it's just this external. Thanks in advance.

---

### Post by givré on 2006-08-03
If you want it to automount automaticly, it's better if you don't have reference of it in /etc/fstab.
Let see your /etc/fstab & the result of 'sudo fdisk -l' when your external is plug in

---

### Post by cheway on 2006-08-03
Right, fstab says this...

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

...and 'sudo fdisk -l' yields...

> Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        7297    58613121   83  Linux
/dev/hda2            7298       14463    57560895   83  Linux
/dev/hda3           14464       14593     1044225   82  Linux swap / Solaris

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19929   160079661    7  HPFS/NTFS


I've got the icon on the desktop now, and I can READ the files, but I cannot format the disk, or do anything at all with the partition through Gnome Partition Editor - it won't even let me unmount it. When I try unmounting it, it says "No such file or directory". I want to resize this NTFS partition to make room for an ext3 one, which is where I want to put my backup before I reinstall everything.

Thanks in advance.

---


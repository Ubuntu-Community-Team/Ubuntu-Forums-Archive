---
title: "Automount behaves different after 2007 week no.2 updates"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-01-12
In the winter season I had some troubles with my automount when I re-installed XP and changed from my previous NTFS to current FAT filesystem.  All this got solved sometimes in in December 2006.

But this year 2007 around the week no.2 updates automount seems to behave differently from the past months.
All my windows FAT partitions automounts as usual but I can no longer copy/paste/delete files on those FAT partitions.
I have to manually
> sudo umount /dev/hda1
sudo mount /dev/hda1 /media/windows/ -t vfat -o iocharset=utf8,umask=000
in order to be able to copy/paste/delete again at my leisure.

What's up with the automount update, was this something INTENTIONAL or un-intentional?

> taco@bell:~$ **sudo fdisk -l**
Password:

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1278    10265503+   c  W95 FAT32 (LBA)
/dev/hda2            1279        3831    20506972+   c  W95 FAT32 (LBA)
/dev/hda3            3832        4998     9373927+  83  Linux

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         131     1052226    b  W95 FAT32
/dev/hdb2             132         261     1044225   82  Linux swap / Solaris
/dev/hdb3             262        4998    38049952+  83  Linux
taco@bell:~$ **cat /etc/fstab**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb3       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     vfat    defaults 0 0
/dev/hda2       /media/hda2     vfat    defaults 0 0
/dev/hdb1       /media/hdb1     vfat    defaults 0 0
/dev/hdb2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
taco@bell:~$


---

### Post by Bachstelze on 2007-01-12
For some reason, the lines in /etc/fstab were reset to the defaults. No big deal, just open it in your favourite text editor and replace "defaults" with "iocharset=utf8,umask)000" on the appropritate line(s) :)

---


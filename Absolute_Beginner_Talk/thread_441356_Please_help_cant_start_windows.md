---
title: "Please help cant start windows"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by Lindworm on 2007-05-12
Please help, I went through the installation it worked fine then I started and it went straight to Ubuntu. I found someone that said about changing it to Windows but I went into the log and there was no windows xp pro thing in there. It is a dual boot and I checked the size of the part and its the right size so the windows one must still exist. Also how do I view my windows partition. Please help quick.

Thanks,
Ben

---

### Post by alienexplorers on 2007-05-12
please print the output of sudo fdisk -l here.  (i is a small L)

---

### Post by annda on 2007-05-12
check the last posts in this thread to see how to find a "lost" win partition and add it to GRUB configuration:
[http://ubuntuforums.org/showthread.php?t=439431](http://ubuntuforums.org/showthread.php?t=439431)

---

### Post by Lindworm on 2007-05-12
Disk /dev/hda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3315    26627706    7  HPFS/NTFS
/dev/hda2            3316        3437      979965   82  Linux swap / Solaris
/dev/hda3            3438        3619     1461915   83  Linux
/dev/hda4            3620        4870    10048657+  83  Linux

Disk /dev/sda: 512 MB, 512753664 bytes
16 heads, 62 sectors/track, 1009 cylinders
Units = cylinders of 992 * 512 = 507904 bytes


There it is

---

### Post by alienexplorers on 2007-05-12
# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

This should be at the end of your /boot/grub/menu.lst file.

---

### Post by annda on 2007-05-12
DELETED - i was too late...

but the file is:

/boot/grub/menu.lst

---


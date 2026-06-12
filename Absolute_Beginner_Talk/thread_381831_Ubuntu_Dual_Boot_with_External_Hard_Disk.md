---
title: "Ubuntu Dual Boot with External Hard Disk"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Xanathus on 2007-03-11
I've just installed Ubuntu 6.10 on a Dell Inspiron 8600 with the following setup; Windows XP Home on an internal hard disk, and Ubuntu on an external hard disk. During boot-up I am able to choose between Ubuntu and WinXP (not sure if this constitutes dual-booting if both are on separate hard disks).

Both OS work fine, but when I disconnect my external hard disk I receive an error message during boot-up from GRUB 
```
GRUB Loading stage 1.5

GRUB loading, please wait

Error 21
```

Basically I want to be able to use Windows XP in my internal hard disk while my external hard disk (which has Ubuntu) is disconnected from my laptop.

Here's the output of sudo fdisk -l in case it's needed

```
Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4864    39070048+   7  HPFS/NTFS

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8470    68035243+   b  W95 FAT32
/dev/sda2           14218       14593     3020220    5  Extended
/dev/sda3            8471       14217    46162777+  83  Linux
/dev/sda5           14406       14593     1510078+  82  Linux swap / Solaris
/dev/sda6           14218       14405     1510047   82  Linux swap / Solaris
```

Addendum: Just remembered, I also set the internal hard disk to be mounted on boot-up for read/write following the instructions on [ubuntuguide.org](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access)

Follow up to addendum: Here's a readout of my /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=2c6aa4bd-f476-449f-904d-afe9f9d6fec9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=15741961-2119-4c7d-930d-022b9887ef31 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1    /media/windows    ntfs-3g    defaults,locale=en_US.utf8    0    0
```

I tried commenting the last line ("/dev/hda1 ..... .utf8 0 0") but nothing changed after rebooting.

---

### Post by matburton on 2007-03-11
The reason you get grub error 21 is because grub is installed on the external drive.

So if you disconnect it grub simply can't load!

What you'll need to do is install grub on the internal drive instead.

---

### Post by Xanathus on 2007-03-12
> **matburton said:**
> The reason you get grub error 21 is because grub is installed on the external drive.

So if you disconnect it grub simply can't load!

What you'll need to do is install grub on the internal drive instead.
So, "sudo grub-install /dev/hda1" ?
edit: ok that doesn't work, so how do I install grub onto an NTFS internal hard disk? And set it to try to boot that up first?

---


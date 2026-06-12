---
title: "Can't mount my hard drive"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by pacoramirez on 2008-02-04
Hello I am trying to access both my hard drives, Ubuntu 7.10 is installed on one but I can't access either one. This is what I get when I type "sudo fdisk -l"

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2cdcbee8

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4660    37431418+  83  Linux
/dev/hda2            4661        4865     1646662+   5  Extended
/dev/hda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c2ba8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641   83  Linux




Then when I type "sudo gedit /etc/fstab", in another window I get:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1
UUID=2f087b23-fd44-4375-a62c-a360da1de2c4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc5
UUID=af2a7e43-e58c-43f3-b8b1-1a6aa7e925b7 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/sda1       /new-disk   vfat   defaults,umask=000   0   0


the last line I added following the instructions of another thread, but I still can't see my hard drives under "Places" like I read. Any one have any ideas please? Thanks

---

### Post by pacoramirez on 2008-02-04
Also, I get this message when I type "sudo mount /dev/sda1"

mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by kpkeerthi on 2008-02-04
> Device Boot Start End Blocks Id System
/dev/sda1 1 38913 312568641 83 Linux


From the fdisk -l output it appears to be ext2/3 partition. But you seem to be mounting it as FAT partition in FSTAB
> /dev/sda1 /new-disk vfat defaults,umask=000 0 0

---

### Post by kpkeerthi on 2008-02-04
What happens when you type
```
sudo mount -t auto /dev/sda1 /new-disk
```
in a terminal?

**Note:** The mount point /new-disk must exist before mounting sda1

---

### Post by oedha on 2008-02-04
what is that disk type ??
i saw on your fdisk -l ...it was linux too..so it can't be mounted as vfat

~E~

---


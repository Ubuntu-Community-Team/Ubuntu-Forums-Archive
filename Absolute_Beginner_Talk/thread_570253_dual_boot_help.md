---
title: "dual boot help"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by manij on 2007-10-08
HI,


Here is the output from my fdisk -l command

[B][I]Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               5       14179   113860687+   7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14409   115740261   83  Linux
/dev/sdb2           14410       14593     1477980    5  Extended
/dev/sdb5           14410       14593     1477948+  82  Linux swap / Solaris
[/I][/B]

The SDB is the linux drive SDA is supposed to be the widnows drive.

I was messing with a FAT partition in the windows drive SDA. As you can see, the ntfs partition is not marked as bootable. I know that there is way to make it bootable from the command line.

Could you please help me with this! Thanks

Mani

---

### Post by cameronw on 2007-10-08
Im not familiar with partitioning using terminal but I find GParted or GNOME Partition Editor (same but sometimes called a different name) a great tool for partitioning and I know in that you can set flags (set a boot flag on the NTFS partition).

---

### Post by eph1973 on 2007-10-08
The command should be:
```
sudo parted /dev/sda set 1 boot on
```

---


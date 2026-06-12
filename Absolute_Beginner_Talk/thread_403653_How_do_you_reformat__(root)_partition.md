---
title: "How do you reformat / (root) partition?"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-04-07
In Windows when you just wanted to reformat a partition you typed in this:
format C:\
how do you do that with Ubuntu without having to delete the old partition?  And then having to reformat it making the process longer.

---

### Post by bigee1212 on 2007-04-07
gparted
or cfdisk if you prefer the terminal

of course this has to be done when you aren't logged in the root partition
my suggestion use a livecd

---

### Post by taurus on 2007-04-07
```
sudo mk2fs -j /dev/XXX
```
where /dev/XXX is the name of a partition.

---

### Post by Hieronymus on 2007-04-07
I agree with Taurus, just sone addition. It is possible to create the file system with the command (notice the extra x because usually the format of the name on the xxxx'es is  something like sda1 or hda1 where the number stands for the partition you want to change. 

```

mke2fs -j /dev/xxxx

```

This means you create a file system with an ext3 journal. Other possibilities are and ext2 journal

```

mke2fs /dev/xxxx

```or reiserfs

```

mkreiserfs /dev/xxxx

```There are more options but these are the most widely used ones. There is just one more that is widely used, but this is only for your swan space.

```

mkswap /dev/xxxx
swapon /dev/xxxx

```When you don't know what is the disk name that should be written on the xxxx you can check this with fdisk, this is the example for my system where my harddrive is sda:

```

root@laptop:/# fdisk /dev/sda 

The number of cylinders for this disk is set to 12161.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3264    26218048+  83  Linux
/dev/sda2            3265        3526     2104515   82  Linux swap / Solaris
/dev/sda3            3527        4179     5245222+  83  Linux
/dev/sda4            4180       12161    64115415   83  Linux

Command (m for help): 


```It is really your own choice which filesystem you want to use, but after the format take a look in your /etc/fstab file and make sure that the file system mentioned for this filesystem is the right one, if unsure check the fstab manual 

```

man fstab

```Jeroen

---

### Post by dptxp on 2007-04-07
Use GPARTED (live CD). You will see all your partitions, you shall not reformat a wrong one. Since you are formatting the root partition, you have to reinstall anyway.

---

### Post by jingo811 on 2007-04-07
Yeah deleting the / (root) partition and re-creating it in "text-mode-install" looks like the smoothest process after all.  Y'all lost me at Hello /etc/fstab :)

---


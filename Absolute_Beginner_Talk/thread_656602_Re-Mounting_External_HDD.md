---
title: "Re-Mounting External HDD"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by MeanStreak on 2008-01-02
Hi,

I have a 320GB Western Digital external hard drive (My Book). When I connect it now to Ubuntu 7.10, it no longer appears as an icon on my desktop nor comes up in My Places - I suspect I deleted some entry somewhere in the file system - I am a noob when it comes to fstab etc. so any help would be much appreciated - how do I mount this hard drive?

---

### Post by jken146 on 2008-01-02
Please post the output of the command ```
cat /etc/fstab
```

And also ```
sudo fdisk -l
``` when the drive is plugged in.

---

### Post by bindatype on 2008-01-02
If the drive is USB then plug it in and try 
```

lsusb

```
as well as 
```

dmesg | tail

```

You will see something along the lines of /dev/hda1 of /dev/sdb1, etc--remember it for future reference b.c you are going to use it shortly. You will also need to know the format of the filesystem. I use ext3 for this example but it could be fat, reiser, ext2, etc.

Create a directory--maybe call it testdir--by doing

```

$ sudo /mnt/testdir

```

then mount your filesystem by hand like this

```

$ sudo mount -t ext3 /dev/sdb2 /mnt/testdir

```

If it doesn't come up read/writable do this

```

$ sudo mount -o remount,rw /mnt/testdir

```



P.S., if you issue the command

```

$ mount

```
without any arguments it will list all of the mounted filesystems--yours isn't mounting so that doesn't help you but for future reference...

---

### Post by MeanStreak on 2008-01-02
Output of cat /etc/fstab:
```

charles@charles-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=32175502-271f-4b5c-b9c5-24927dd136b0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb1
UUID=60ab09cd-9300-4fc7-b179-dbc87db91710 /home           ext3    defaults        0       2
# /dev/sda1
UUID=E6541C87541C5C9D /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=13a15239-c531-4918-81cc-c494ef14ccf7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
charles@charles-desktop:~$ 

```

Output of sudo fdisk -l

```
charles@charles-desktop:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfc6ffc6f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8583    68942916    7  HPFS/NTFS
/dev/sda2            8584       14341    46251135   83  Linux
/dev/sda3           14342       14593     2024190    5  Extended
/dev/sda5           14342       14593     2024158+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4076f59e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       13419   107788086   83  Linux
/dev/sdb2           13420       19457    48500235   83  Linux

```

---

### Post by bindatype on 2008-01-02
I know you are getting hit with a lot of comments but could you give the output of 
```

lsusb

```
as well as 
```

dmesg | tail

```

There is no point in looking in fstab for your USB drive--it won't appear there until you put it there. Use lsusb and dmesg like above.

---

### Post by MeanStreak on 2008-01-02
Thanks for all the help but I've figured out the problem - easier to diagnose in Windows of course - the external hard drive had somehow failed, so despite being on and plugged in, it wasn't appearing. Windows identified that a USB device had failed, so I unplugged, switched it back on and it now mounts in both OS's. Sometimes you just have to admire the simplicity of Windows.

---


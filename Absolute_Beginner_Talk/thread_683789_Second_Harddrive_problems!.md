---
title: "Second Harddrive problems!"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by Xobulo on 2008-01-31
Hi

I am making my first steps into linux using xubunto, the system that I have put it onto has 2 HDDs the first was wiped during the install the second however still contains all the old xp data that was on it before.

Anyone able to tell me how I can blank the second hard drive?

---

### Post by jan quark on 2008-01-31
I would use the partition application gparted to format the second harddrive

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by njparton on 2008-01-31
There are 2 options. Install gparted a graphical partition manager which can also format/delete partitions etc.

Or

Use the command line to format the drive. Let's say it's detected as /dev/sdb and you want to format it as ext3:

```
mkfs.ext3 /dev/sdb
```

Can't remember if you need to be root to do that. In which case stick "sudo" before it.

The first thing you'll have to do with the second option though is dive into the /dev directory and see which device it's been detected as.  It may be /dev/hdb if it's an IDE drive. SATA drives are sda, sdb etc...

---

### Post by Xobulo on 2008-01-31
gparted doesnt seem to like my current settings I got this message in the Terminal

"Unable to open /dev/fd0 read-write (Read-only file system).  /dev/fd0 has been opened read-only."

---

### Post by jrothwell97 on 2008-01-31
/dev/fd0 is the floppy drive. Which is odd.

Try

```
mkfs.ext3 /dev/hdb0
```

or

```
mkfs.ext3 /dev/sdb0
```

---

### Post by dstew on 2008-01-31
To start graphical programs from the terminal, use gksudo.```
gksudo gparted
```

---

### Post by Xobulo on 2008-01-31
Attempeted both commands which gave this result:

```

xobulo@xobulo-desktop:~$ mkfs.ext3 /dev/hdb0
mke2fs 1.40.2 (12-Jul-2007)
Could not stat /dev/hdb0 --- No such file or directory

The device apparently does not exist; did you specify it correctly?
xobulo@xobulo-desktop:~$ mkfs.ext3 /dev/sdb0
mke2fs 1.40.2 (12-Jul-2007)
Could not stat /dev/sdb0 --- No such file or directory

The device apparently does not exist; did you specify it correctly?

```

and typing gksudo instead of sudo gave the same result as before when tryin to launch gparted.

---

### Post by jan quark on 2008-01-31
```
sudo fdisk -l
```

this will list all available partitions mounted or not
pls post the result

---

### Post by Xobulo on 2008-01-31
```
Disk /dev/sda: 6851 MB, 6851174400 bytes
255 heads, 63 sectors/track, 832 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f2db3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         790     6345643+  83  Linux
/dev/sda2             791         832      337365    5  Extended
/dev/sda5             791         832      337333+  82  Linux swap / Solaris

Disk /dev/sdb: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5f285f28

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2497    20057121    7  HPFS/NTFS

```

No laughter please! hehe

---

### Post by njparton on 2008-01-31
sdb0, sdb1  are partitions, if you want to format the whole drive stick to just sdb without the last number

---


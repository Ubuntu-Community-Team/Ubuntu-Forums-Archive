---
title: "how to mount  second HD with win98 ?"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by lich 6222 on 2007-05-11
Hello !:confused: 

my computer is a celron 1700 with 384 MB 2 hard disk .etheernet cards, 64MB video card
Dvd player and CD-ROM .
first Ubuntu 6.10
second win98

How do  I mount the second HD (win98), to copy file from it to ubuntu HD
BTW both HD have  partioned
Eli

---

### Post by gradedcheese on 2007-05-11
Here's how to do it from the shell (Applications->Accessories->Terminal)

First, create a place to mount it:

```

sudo mkdir /mnt/win

```

Second, mount it:

```

sudo mount -t vfat /dev/hdb0 /mnt/win

```

That assumes that your second hard disk is hdb (ie: second IDE disk) and that the partition you want is number 0.  Change those as needed (ex: /dev/hda1 for the second partition on the first IDE hard disk).  If you want to look up the right device, run:

```

sudo fdisk -l

```

to list all of them.

Once mounted, you can (with sudo) access /mnt/win to get at the files.  To unmount it:

```

sudo umount /mnt/win

```

You can also out an entry into /etc/fstab to have this mounted automatically if you want.  If you want a GUI way to manage partitions and look at / mount them, install gparted:

```

sudo apt-get install gparted

```

---


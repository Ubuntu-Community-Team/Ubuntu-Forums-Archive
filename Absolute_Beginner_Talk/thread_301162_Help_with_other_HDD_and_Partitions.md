---
title: "Help with other HDD and Partitions"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by bhudda on 2006-11-16
Hey there everyone! I just installed Ubuntu and have gotten through a few of the problems by reading on the forum and whatnot. But I have a question...How do I get my "Sharing" partition to mount all the time and what not?

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60802   488392033+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       15935   127997856    7  HPFS/NTFS
/dev/hda2           15936       24320    67352512+   f  W95 Ext'd (LBA)
/dev/hda5           15936       15968      265041   83  Linux
/dev/hda6           15969       22280    50701108+  83  Linux
/dev/hda7           22281       22408     1028128+  82  Linux swap / Solaris
/dev/hda8           22409       24320    15358108+   b  W95 FAT32

```

So I am wondering what I do to go about making the /dev/hda8 mount all the time...also I wouldn't mind mounting my RAID array and using it to listen to music (As that is where all of my music is stored). Thanks!

~bhudda

---

### Post by taurus on 2006-11-16
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by bhudda on 2006-11-16
Righto. Got that one. But I don't understand the fstab editing part...
I should have this somewhere? Or in a particular spot?

```
/dev/hda8 /shared vfat iocharset=utf8,umask=000 0 0
```

IS that all I need for the fstab?

And then in regards to my RAID array at /dev/sda1, it is NTFS so do I put this in somewhere?

```
/dev/sda1 /storage ntfs nls=utf8,umask=0222 0 0
```

Thanks for the speedy reply!

EDIT: Also, how do I remove directories I made and decided not to use?
EDIT2: Never mind on the directory, I got it...

~b

---

### Post by taurus on 2006-11-16
Yes, those two entries in /etc/fstab should mount both /dev/sda1 & /dev/hda8 for you.  Make sure you have both /shared & /storage before you mount them...

---

### Post by bhudda on 2006-11-16
Alright, well I got the hda8 drive to mount it it is a-ok!

But I am having problems getting /dev/sda1 to mount...is that because it is a SATA RAID system? fdisk detects it though, and lists it. I have it inputted into my fstab file.

Thanks again! I Love Ubuntu!

```
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

~b

---


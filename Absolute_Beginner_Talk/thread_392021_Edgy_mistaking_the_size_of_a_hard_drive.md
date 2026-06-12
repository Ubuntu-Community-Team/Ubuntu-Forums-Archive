---
title: "Edgy mistaking the size of a hard drive"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by brennydoogles on 2007-03-24
::EDIT::  This post has been resolved. Thanks to everyone for their help!

I am a new Ubuntu user running a dual boot with XP, and as such only allocated Linux a small portion of my hard drive, in case I didn't like it. After a few days, I decided to partition my second hard drive to use as storage for both (half each). I set up the second partition as an EXT3 file system, and after a while I was able to figure out where the hard drive was. I am able to read and write to it, but it is showing up as only having about 500MB storage, when in fact it has about 50GB. It shows up correctly on Gparted (which is what I used to partition it in the first place), and using the terminal command
```
sudo fdisk -l
```
I get this from the terminal...

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               2         513     3870720    5  Extended
/dev/hda2   *         514       10337    74269440    7  HPFS/NTFS
/dev/hda5               2          36      264568+  82  Linux swap / Solaris
/dev/hda6              37         513     3606088+  83  Linux

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        7012    56323858+   7  HPFS/NTFS
/dev/hdb2            7013       14593    60894382+   5  Extended
/dev/hdb5            7013       14400    59344078+  83  Linux
/dev/hdb6           14401       14593     1550241   82  Linux swap / Solaris

```

Have I done something wrong, or is this some type of known issue?? Any help would be greatly appreciated, and go easy on me if I did something stupid... I have only been a Linux user for about two weeks.

---

### Post by nyinge on 2007-03-24
Your /dev/hda5 shows ~50GB, which I believe is the partition you want to keep around for storage on your 2nd drive.  Things look good in fdisk as well.  So, where is it showing up as 50MB?  A screen shot would be great.

Why do you need a swap partition...  just wondering...  if you're just gonna keep your 2nd drive as your storage?  I'd just format your 2nd drive (120 GB) with FAT32 if I just want to be able to access it from both OS's.

---

### Post by brennydoogles on 2007-03-24
> **nyinge said:**
> Your /dev/hda5 shows ~50GB, which I believe is the partition you want to keep around for storage on your 2nd drive.  Things look good in fdisk as well.  So, where is it showing up as 50MB?  A screen shot would be great.

Why do you need a swap partition...  just wondering...  if you're just gonna keep your 2nd drive as your storage?  I'd just format your 2nd drive (120 GB) with FAT32 if I just want to be able to access it from both OS's.

Thank you for your response!! Although your response itself did not solve the problem, you pointed me in the right direction to figure it out. You mentioned /dev/hda5, which is my primary Windows partition, and the partition I was having trouble with was on the hdb drive. I got to thinking about that, and realized that for some reason i was trying to get hdb1 mounted correctly, when in all actuality I needed to be mounting hdb5. I mounted it, and everything seems to be working well now. Thank you for your help!!

---

### Post by nyinge on 2007-03-24
lol...  my mistake...  I meant to say /dev/hdb5 is 50GB.  /dev/hda5 would have been your swap partition.  well...  glad things work out.  :)

---


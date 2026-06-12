---
title: "Grub Error 17: cannot mount selected partition"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by roundhay on 2008-02-02
I have 4 HDD in my PC

I want to use 2 x 160GD HDD for OS 1 loaded with XP Pro and 1 with Ubuntu

I also have 2 x 500GD HDD which I use as media storage, mp3's, avi's etc

I had a working grub until I reinstalled windows XP, after I reinstalled XP the PC booted directly to XP. I then reinstalled Ubuntu onto the second HDD. After I had done this I managed to get grub back and can boot to XP but every time I try to boot to Ubuntu I get Error 17: cannot mount selected partition

I have spent hours working through tutorials but have failed to sort out this error. 

I have also tried using Super Grub Disk but this has not help either.

I have even gone so far as rebuilding the mbr of XP and formatting the Linux drive from windows before reinstalling Ubuntu but still the problem persists??

I have no idea what i am doing wrong and could do with some help!

Below is the output from sudo fdisk -lu that I ran in the live CD

Can someone shpw me what I need to do?

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd204d204

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   312560639   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd253d254

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001    7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00094cce

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   300415499   150207718+  83  Linux
/dev/sdc2       300415500   312576704     6080602+   5  Extended
/dev/sdc5       300415563   312576704     6080571   82  Linux swap / Solaris

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd253d255

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   976768064   488384001    7  HPFS/NTFS

---

### Post by billgoldberg on 2008-02-02
The easiest thing to to might be to start over.

Since all your data is on separate drives, this isn't a really big deal.

It is always better to install ubuntu second and xp first.

So if you format the two drives, install xp on the first drive and after that ubuntu on the second, everything should be fine.

I don't see why super grub disk wouldn't work, but it can be a bit complicated at times.

---

### Post by billgoldberg on 2008-02-02
Ignore that comment, didn't read carefully enough.

---


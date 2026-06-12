---
title: "Ubuntu Installation"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by listetyven on 2006-12-18
I am wasting too many keyboards in paroxysms of rage when using windows, therefor i have decided Linux For Humans.

I have used it before, but not on a computer where Windows is located too. I have Partioned a 320Gb Barracuda 7200.10 like this:

30Gb (C) Windows XP
30Gb (D) Where i want linux at
260Gb (E) Data

Except for this disk i have 3 other 320Gb disks and a few other, all of them SATA.

I would like to keep the NTFS Filesystem on the D-drive (i assume linux supports NTFS :)).

My computer Specs:

K8 4800+ X2 @ 2x 2.6
Asus A8N-SLi Premium
2x 1024Mb GeIL DDR PC3200
ATi Radeon X1900XTX
LG IDE CD-RW
Plextor PX760-SA SATA DVD-RW
Soundblaster Audigy 2 ZS

I have found out that most of my hardware manufacters supports Linux (I'm planning the Ubuntu AMD64 6.10) so the driver part is ok.

I guess i'm just about ready for installing right? (i've done it before with a 32Bit so i don't need that much help!)

---

### Post by mykalreborn on 2006-12-18
yup you are ;)
but you should make the other, non-linux partitions fat32, because ntfs gives you a real head-ache when it comes to linux. but if you already formatted them in ntfs you should check this howto:[link]("http://ubuntuforums.com/showthread.php?t=217009&highlight=ntfs")

---

### Post by jvc26 on 2006-12-18
You'll also need another small partition for the swap space for linux (either put this into your 30GB linux partition and make that slightly smaller or take a tiny bit off one of the other partitions). As mykalreborn says NTFS seems to cause a fair few headaches so FAT32 is an easier option as it works fine. Other than that enjoy :D

---

### Post by listetyven on 2006-12-19
Uhm, i'm a little confused here. Whats the trouble in running Linux on a NTFS? (maybe i didn't understand the Howto right, i'm from denmark so i don't use english very often:rolleyes: ).
I thought The Swap-partition was automaticaly being created by using some space from the installation directory.

btw, thanks for the replies, i appreciate your assistance!

---

### Post by aysiu on 2006-12-19
NTFS is a proprietary filesystem that's made to run Windows. You cannot install Linux on an NTFS partition.

---

### Post by jvc26 on 2006-12-19
When you install ubuntu to the 30GB partition presumably you'll use the GTPartd which is the Gnome partition editor which loads during the install process. When you select the 30GB space its just a matter of setting apart a 1Gig section for instance as a partition for the swap file. I think ext3 is the commonly used one for installing linux to (in terms of filesystem) and to transfer files between them the most headache free is FAT32 as linux and windows can both read/write between the two with ease. :)
Il

---

### Post by aysiu on 2006-12-19
Read this:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by listetyven on 2006-12-19
That's weird, well i guess not, but i have once read (almost :) ) a book about Red Hat, and i am nearly sure that it said the Red Hat Could run on NTFS.

---

### Post by aysiu on 2006-12-19
Maybe it said that Red Hat could *read* NTFS? That is certainly can do. It can also resize NTFS and be installed next to NTFS.

---

### Post by listetyven on 2006-12-19
Well, that kinda settles it. I'll just make that 30 Gig Partition ext3. Windows will see this as a "unformated" or "raw" disk right?

---

### Post by mykalreborn on 2006-12-19
> **listetyven said:**
> Well, that kinda settles it. I'll just make that 30 Gig Partition ext3. Windows will see this as a "unformated" or "raw" disk right?

not necesarily. you can install a program for windows to recognize your linux partition. it should be a whole lot easier than installing write support for ntfs. i'm pretty sure the windows counterpart can write on the linux partition. but when it does, ubuntu does a default check on each partiton on startup - at least it did that in my case. 
check this link:[http://fs-driver.org/](http://fs-driver.org/)

---


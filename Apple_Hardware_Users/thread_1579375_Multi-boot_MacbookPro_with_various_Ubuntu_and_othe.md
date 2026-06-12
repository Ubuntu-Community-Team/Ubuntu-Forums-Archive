---
title: "Multi-boot MacbookPro with various Ubuntu and other Linux distros and versions"
date: 2010-09-21
forum: Apple Hardware Users
---

### Post by niyam on 2010-09-21
I have a MacbookPro 5,1 with 2GBRAM, which successfully dual-boots with Ubuntu 9.04 since a year.
I wish to urgently install ubuntustudio, and also wish to have one or perhaps two more partitions, where I may install the latest Ubuntu as well as another Linux distro.

Typically, think of a multi-boot scenario:
Mac OSX 10.5.x
Ubuntu 9.04 <<--working production install, not to be messed.
UbuntuStudio 10.4
Ubuntu 10.10 [just a few days  left!]
Fedora or Knoppix or Debian.

if possible, i'd also like to keep one partition free and unallocated, or reformat a partition, if i ever need to install windows. any thing i'd need to watch out for in this?

I've got no extra or free partitions, only free space on the mac partition, that i'd like to carve out and allocate to partitions.

Also, before i begin, is there a way I can clone my entire mac+linux hard-disk so in the event of a failure i can get *everything* back, mac as well as ubuntu? I bought a hd of an identical size, but use it with Time Machine. I'd rather use it to clone the entire hd.

Thanks for all your help,
i just need to get this done.

regards
niyam

---

### Post by majortom67 on 2010-09-22
I see no problem if you install more than 3 OSs (MBR's limit) on that machine as both Mac OS and Linux distros can benefit from MBRs with more than 3 partitions. With rEFIT of course.
Just be sure to install - for each distro - it's bootloader in its partition, not on the /dev/sda1 (EFI's partition).
The only problem I can see is if you install Win. This must be  into the 1st, the 2nd or at least the 3rd partition otherwise it wount' start (Win's MBR's management limit - horrible!!!).
HTH
major

FOR backup: Carbon Copy Cloner for Mac OS X (bootable clone partition, by the way) and Remastersys in Ubuntu. Here, Remastersys is just for OS and apps, you need to backup the HOme folder separately (Sbackup, Grsync or whatever you might prefer...).

---

### Post by niyam on 2010-09-22
Thanks majortom67, for your quick reply. Unfortunately am lost in the haze with MBRs and rEFIt. All that I gather is that there are 3 partitions, so mac stays in one, ubuntu 9.04 in one, and win in another.
Assuming I just keep one mbr for the unfortunate comedy of having to use windows some day, that leaves me with two.
So how do I actually affect the multi-boot with one mac partition, one ubuntu 9.04, one ubuntustudio, one ubuntu 10.10, and one (fedora, debian, or knoppix...) partition? That too carving all these from my existing ecosystem of a dual-boot machine, with only free space within the existing mac partition to play with?
Is there a how-to or steps-to-follow somewhere please? Been searching but haven't found any yet.

Don't you think the safest thing for me to do would be to first clone my entire hard-disk onto another. This way, if something goes wrong, I can just restore the entire hard-disk to its initial state and not skip a heart-beat? What tool would be suitable for this please?

Am feeling quite nervous and yet also excited about tinkering with the only machine I've got up and running for the moment. Whew!

Thanks

Regards
niyam bhushan

---

### Post by buntuLo on 2010-09-22
> **niyam said:**
> Don't you think the safest thing for me to do would be to first clone my entire hard-disk onto another. This way, if something goes wrong, I can just restore the entire hard-disk to its initial state and not skip a heart-beat? What tool would be suitable for this please?
yes, make a clone of it first. majortom67 already suggested you a tool to clone your hard drive. another possible way would be to boot up with a linux livecd, connect an external usb drive (equal or larger than your internal one), open a terminal, and use the command dd to clone the drive:
```
dd if=/dev/sda of=/dev/sdb
```
but do check before the correct letters of your drives! usually sda is the first hard drive, sdb the second one. 'if' stands for input file, 'of' for output file. if you swap them, you just wipe the internal drive. do read
```
man dd
```
before proceeding! it takes time, and it takes exactly the space of the drive.
majortom67' suggestion may instead use compression (i'm not really sure), therefore you may not need a drive as large as the internal one.
> **niyam said:**
> So how do I actually affect the multi-boot with one mac partition, one ubuntu 9.04, one ubuntustudio, one ubuntu 10.10, and one (fedora, debian, or knoppix...) partition? That too carving all these from my existing ecosystem of a dual-boot machine, with only free space within the existing mac partition to play with?
after the copy with dd, i would use the same livecd and run gparted from it. with that, i would resize the macosx partition and create empty partitions for installing new os'es. when installing them, take care of manually selecting the partitions where to install their bootloaders, as majortom67 wrote you.
ciao, Lo.

---

### Post by linuxopjemac on 2010-09-22
You can also burn [Clonezilla]("http://clonezilla.org/") to a CD and clone the hard disk. It will essentially do the same dd trick, but this is easier if you are not familiar with the terminal.

---

### Post by niyam on 2010-09-22
Thanks buntoLo for the clarifications. The all-powerful dd seems to be the safest choice with no compression. Will also verify the clone before i proceed to ensure no bits were harmed in the cloning. Just checked out Carbon Copy Cloner, its site's FAQ and KnowledgeBase doesn't really mention if it fits the bill for cloning the hard-disk with both mac and linux partitions, hence the initial confusion. CCC seems more mac-volume specific, or a hard-disk with multi-partitions for mac. Or not?
the tip on gparted is valuable. thanks.
will share my results here once i get started (and get over that nervous feelin').

regards
niyam


regards
niyam

---

### Post by niyam on 2010-09-22
Clonezilla! Just what the doctor ordered. Makes the task even easier, thanks! Me thinks will use clonezilla to not only backup, but transfer the clone of the smaller hard-disk to a newer, larger hard-disk. This way, I can hit the ground running with my dual-boot ecosystem, and have even more leg-room to evolve from dual-boot to multi-boot madness.
Thanks linuxopjemac.

regards
niyam

---


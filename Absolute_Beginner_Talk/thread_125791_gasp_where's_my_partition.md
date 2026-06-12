---
title: "*gasp* where's my partition?"
date: 2006-02-04
forum: Absolute Beginner Talk
---

### Post by Fffan on 2006-02-04
When installing ubuntu, i did 140gig Windows partition (i already had all kinds of crap on there) a 10gig linux partition (figured i wouldnt need much space for OS and programs) and a 30 gig swap partition. My question is, how do i detect the partition on either OS? this is an immediate concern because i currently have 189megs left on my windows partition, and i need to save a movie file, and i dont have anything to delete.

Right now i just need to know how to get 30 extra gigs in windows, later you can tell me how to get to those files in linux

---

### Post by Pragmatist on 2006-02-04
First, what does fdisk output:
1. type: sudo fdisk /dev/hda  (or hdb if the second disk drive sda sdb for SCSI etc.)
2. enter your root password at the prompt
3. type: p
4. paste the output in your reply

Now, you want to extend your windows partition by 30 gigs?

You can use a program called partition magic, or gnuparted (check out QTParted which is gnuparted graphical front-end), to change the size and type of your partitions.

Unless you have 15 Gigs of RAM, you don't need 30 Gigs of swap.  The general rule is 1-2X the amount of RAM for swap space.

Am I misunderstanding you?

---

### Post by Herman on 2006-02-04
> When installing ubuntu, i did 140gig Windows partition (i already had all kinds of crap on there) a 10gig linux partition (figured i wouldnt need much space for OS and programs) and a 30 gig swap partition. My question is, how do i detect the partition on either OS? this is an immediate concern because i currently have 189megs left on my windows partition, and i need to save a movie file, and i dont have anything to delete.
Right now i just need to know how to get 30 extra gigs in windows, later you can tell me how to get to those files in linux G'day, mate! Well, it seems as if there is a little confusion here to begin with our partitioning 'lingo'.
Let me try to explain some terms:
A 'swap area' is a special part of the hard-disk where our operating system can write some parts of the memory to when that part of the memory doesn't get used for a while, that leaves the faster RAM memory free for the most urgent jobs you need it for. A suggested size for your swap area is between one and a half to three times the size of your RAM, depending on how much disk space you can spare for it. If you have lots of RAM, like 1 GB os more, you might not need very much swap area.
A 'data partition' is an extra partition not used to accomodate an operating system. The most common format for a data partition is FAT32, since both Windows XP with an NTFS filesystem can 'see' it and read and write to it, and also your Linux (Ubuntu) operatiing system can read and write to it without harming it. 
If you have FAT32 in WIndows, like I do, you won't really need the seperate 'data' partition, since you should be able to click on the white icon on your 'Breezy' desktop and directly access your Windows files. 
If you have NTFS in Windows XP, a seperate FAT32 data partition is a good idea.

Oops, sorry pragmatist-simultaneous post-you were first, I'll 'bow out', over to you!

---

### Post by Fffan on 2006-02-05
Wow, dont i feel noobish, ilts late but i suppose ill go into linux and see what i can do with this swap partition changing it to a FAT32 partition (as Windows is on NTFS) yesm, i just needed 30gigs more is all, i have a gig of ram so i might do a gig or so swap still, maybe if im having fun with gimp, normal usage im at 700megs RAM usage, but it anycase, all those apps work with amd64?

---

### Post by Herman on 2006-02-05
>  all those apps work with amd64?
I have no idea about AMD64, I have never tried it, and I'm not sure what partitioning software will or won't work with it. 
My second sig link leads to the .iso download for GParted livecd-0.2 which is pretty good for regular 'garden variety' run-of-the-mill 32 bit computers. That should do what you need to do the easiest of anything I know, if it works with AMD64. :-D (Herman).

---

### Post by Fffan on 2006-02-05
Works great, thank you!

---


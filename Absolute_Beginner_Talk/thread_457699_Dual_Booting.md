---
title: "Dual Booting"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by Warpnow on 2007-05-28
I want to Dual Boot windows XP and Ubuntu 7.

From what I understand the best way is with 3 partitions. One for Windows, One for Ubuntu and one as a fat32 which they both can access. 

What I need is some info from someone who has done it before.

What sizes are optimal for the windows/ubuntu installs? How much does the OS need on its "main" partition in order to run quickly?

Also, I have 2 hds. One is an 80 gig Deskstar and the other a 160 gig WD Caviar. Should I try and raid them to make it easier? I'd prefer not to, because I'm afraid one would fail. If not, how should I do it? An OS on each of them, then the rest as fat32? Or both OSs on one, then the rest of that one fat32 and the other all fat32? Either way, I'm seeing 4 partitions, which is kind of annoying, but doable.

Any advice?

Edit: Oh, also, which should I install first? I was under the impression Windows autodetects other OSs, but maybe not. Also, is it wise to use a separate bootloader program?

---

### Post by rsambuca on 2007-05-28
20 gigs per OS is definitely plenty.  You seem to have enough space so I would go with that.

If you are starting fresh, I would make sure you install XP first, and then install ubuntu, so that the grub loader can detect both ubuntu and XP.  If you install XP second, it will not detect ubuntu.

---

### Post by bobplano on 2007-05-28
for ubuntu you need at least two partitions. swap and /(root). i think the best way would be to have both OSes on one and the fat32 on the other

---

### Post by freebeer on 2007-05-28
There really isn't any "optimal" setting... it depends on what you want to do and how you'll be using the machine.  Need lots of room for Windows games?  You'll want a decent sized Windows partition.  And so forth.

With two hard drives, I'd probably set one up with Windows (the full 80 gigs).  Then install Ubuntu on the second hard drive.  I'd partition the Linux drive into three areas... about 20 gigs for / (root), 1 or 2 gigs for swap (depending on your RAM size) and the third partition for /home.  

While you could set up a partition as FAT32 to share between the two OSes, I personally wouldn't.  I'd just install the drivers required to read/write ext3 from within Windows, and install the driver (ntfs-3g?) in Ubuntu to read/write on NTFS (Windows) files.  FAT32 isn't as robust as the other file systems.  But it's your call. :D

Remember... nothing is carved in stone or is irreversable.  You can resize the partitions later if you really want or need to.

---


---
title: "Two systems, no install..."
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by rorybellows on 2007-07-12
Brief summary. I have two PCs:

1) Intel C2D E6600, WD 160GB SATA II, WD SATA II 320GB, 8800GTS 320MB, 2GB DDR2
2) AMD Athlon64 3400, 1GB DDR, 80GB Seagate SATA

I tried installing the 7.04 live CD on system 1. Just hung for ages without getting anywhere. Went to 6.06. Got the live part up and running, went to install, got up to the partition stage - couldn't locate any disks, thus, couldn't install - just hung at the partition stage.

Switched to system 2. Same deal with 7.04, system hang before anything happens. Again, tried 6.06, exactly the same deal again, got all the way top partition in the install process, but hangs on the 'Select a disk' part. 

I seem to be doing the same thing wrong on both systems... I'd wager it's something simple. Can anyone help a gormless noob?

---

### Post by ianhaycox on 2007-07-12
I bit of a guess, but in the BIOS there may a section that tells the PC to advertise the SATA disk as an ATA disk. Sorry can't remember the exact configuration options but a bit of poking about should find it. 

I must admit I've only had this problem with Windows, not on Ubuntu. It's possible this may get you started.

---

### Post by sad_iq on 2007-07-12
Could be a bad disk...try burning at a low speed(4x), check md5 sum, check disk for errors and such...If install fails at partitioning try downloading Gparted LiveCd and do the partitions with it. And you don't have any Raid in there do you?...I think it causes problems!!!
 Here is where you can get Gparted LiveCd: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by rorybellows on 2007-07-12
Thanks for those ideas.

I will play in the BIOS and see what I can do. I have tried a couple of different versions of the cds, all burned at the lowest speed. Same error.

I tried GParted. It located the disks straight away, but, to be honest, I didn't know how to partition the disks, and am still at the stage of 'let the installer do it for me'. I'll read about the partitions and use GParted and see how I go.

---


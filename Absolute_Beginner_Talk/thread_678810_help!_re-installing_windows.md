---
title: "help! re-installing windows"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by xRockTripodx on 2008-01-26
I hope this is the right forum to post in.  I'm going to assume it is because I am, in fact, a total newb.  I recently received an Acer Extensa 4620z laptop loaded with Vista.  I wanted to try out Ubuntu since I really am not a fan of Microsoft's latest offering.  At any rate, I ran a dual-boot for a bit, but screwed up a few things in Ubuntu that I couldn't get back.  So, I re-installed it.  Over the whole HDD.  No more windows, no more hidden recovery partition.  I have the system and recovery disk from Acer, but whenever I try to run it, it simply says no partition is available.  Now, I'm guessing that it's looking for the hidden recovery partition, but I'm not entirely sure.  I want Windows back, since there are several things I need to be able to do with it.  Sorry if this is too specific a question about too specific a setup, but i've tried everything and all its done is driven me to drink.  Has anyone tried re-installing windows on a Vista before with the recovery disk?  I'm desperate for help!  Any pointers would be appreciated.  Btw, I thoroughly intend to dual boot again and do it the right way.  There's a lot to like about Ubuntu.

---

### Post by mikewhatever on 2008-01-26
That's odd. I always thought those recovery CDs would format the drive, no matter what's on it, and revert the computer to it's factory state. Hope someone know a solution. Have you tried contacting Acer?

PS: I'd gess your question is more appropriate in 'Other OSs' forum, cause it's not related to Ubuntu, by whatever.

---

### Post by mikeyphi on 2008-01-26
I think it's as you've guessed - you wiped the hidden partition......you need a proper Vista disk to reinstall from scratch...I believe the recovery disk is just that - for recovery if it can find the OS!!

---

### Post by mikewhatever on 2008-01-26
> **mikeyphi said:**
> I think it's as you've guessed - you wiped the hidden partition......you need a proper Vista disk to reinstall from scratch...I believe the recovery disk is just that - for recovery if it can find the OS!!

I have an HP laptop with recovery disks and partition, and there is an option of removing the latter to free disk space. I have not tried the OP's scenario, just resized Windows partition and installed Ubuntu, and everything seems to work. Yet, the recovery disks are not for simple recovering, but, as said before, for formatting and reinstalling the whole thing.

---

### Post by Raccoon1400 on 2008-01-26
It is not looking for a recovery partition, it is looking for an ntfs partiton.
 Ubuntu is installed on an ext3 partition, which windows cannot read. I have tried getting setup to format these, but it doesn't want to. You will have to use a partitioning tool like gparted on the live cd to shrink your ubuntu partition, and then, using the windows setup create a new ntfs partition.
I have never resized an ext3 partition, so I can't help you with that. The windows installation will require you to reinstall the grub bootloader to boot ubuntu, but I have never done that either.

---

### Post by mikewhatever on 2008-01-26
> **Raccoon1400 said:**
> It is not looking for a recovery partition, it is looking for an ntfs partiton.
 Ubuntu is installed on an ext3 partition, which windows cannot read. I have tried getting setup to format these, but it doesn't want to. You will have to use a partitioning tool like gparted on the live cd to shrink your ubuntu partition, and then, using the windows setup create a new ntfs partition.
I have never resized an ext3 partition, so I can't help you with that. The windows installation will require you to reinstall the grub bootloader to boot ubuntu, but I have never done that either.

Does it matter what size that ntfs partition is and where on the disk it is? What is it needed for? Are you saying that if the OP created a little ntfs partition anywhere on the disk, the recovery CD would work?

---

### Post by tekguy on 2008-01-26
> **xRockTripodx said:**
> I hope this is the right forum to post in.  I'm going to assume it is because I am, in fact, a total newb.  I recently received an Acer Extensa 4620z laptop loaded with Vista.  I wanted to try out Ubuntu since I really am not a fan of Microsoft's latest offering.  At any rate, I ran a dual-boot for a bit, but screwed up a few things in Ubuntu that I couldn't get back.  So, I re-installed it.  Over the whole HDD.  No more windows, no more hidden recovery partition.  I have the system and recovery disk from Acer, but whenever I try to run it, it simply says no partition is available.  Now, I'm guessing that it's looking for the hidden recovery partition, but I'm not entirely sure.  I want Windows back, since there are several things I need to be able to do with it.  Sorry if this is too specific a question about too specific a setup, but i've tried everything and all its done is driven me to drink.  Has anyone tried re-installing windows on a Vista before with the recovery disk?  I'm desperate for help!  Any pointers would be appreciated.  Btw, I thoroughly intend to dual boot again and do it the right way.  There's a lot to like about Ubuntu.

Looks like you might need to install Vista first then use the restore. Check this out. They so there is no OS on the disk and that Windows will have to be installed first.

[http://www.recovery-cds.com/recoverycd/acerextensa/acer-extensa-recovery.htm](http://www.recovery-cds.com/recoverycd/acerextensa/acer-extensa-recovery.htm)

---

### Post by xRockTripodx on 2008-01-27
Thanks all very much for the help.  Acer has been of no assistance so far.  I also received a system disk, which I am hoping has the OS on it.  I'm going to attempt shrinking the Ubuntu partition, but I think I'm gonna need the wonderful Microsoft gang to send me an install disc.  Legally, I'm allowed one, let's see if they give it to me.

---

### Post by sean42 on 2008-02-04
I have the same laptop and did the very thing you want to do.  In order to get vista back on the machine I formatted the drive in NTFS using Gparted then ran the restore discs I created when I bought the laptop.  when the restore discs were finished I still could not boot into vista, as I had blasted out the bootloader when I formatted the drive. to fix that I used a disc with the supergrub utility to fix the windows bootloader. good luck.

[http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/")

[http://supergrub.forjamari.linex.org/?section=download]("http://supergrub.forjamari.linex.org/?section=download")

---


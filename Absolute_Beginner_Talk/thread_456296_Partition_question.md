---
title: "Partition question"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by henthorn on 2007-05-27
I tried to install Unbuntu with the live disk. Got to the method of partitiioning choice, chose Guided with free space and up came a box saying any previous changes had to be taken care of first.  I had installed XP-home before I used the live CD. I couldn't see any option for doing what it wanted.  I aborted the installation to see if I can get an answer.

---

### Post by Bachstelze on 2007-05-27
Just fire up GParted (on it's own, not in the installer) and use it to resize your Win partition down. Then launch the installer, tell it to use all the free space, voilà :)

---

### Post by overdrank on 2007-05-27
> **henthorn said:**
> I tried to install Unbuntu with the live disk. Got to the method of partitiioning choice, chose Guided with free space and up came a box saying any previous changes had to be taken care of first.  I had installed XP-home before I used the live CD. I couldn't see any option for doing what it wanted.  I aborted the installation to see if I can get an answer.

Hi and welcome this link may help
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
Good luck and welcome!:D

---

### Post by henthorn on 2007-05-27
Thanks to both of the above replies.  I can't find gparted on the live disk I have, but I do have it on a CD I downloaded separately and it doesn't give me anything but the directory and I don't see an exe file or any way to open it.  I also was following the Psychrats.net method to install but the problem I ran into was not addressed. I figure I need to reformat the hard disk to eliminate any errors it might have on it and then reinstall XP-home before I try the Live disk again.  The problem is I don't know how to reformat the hard drive.  I tried using my XP-home CD but it tells me that the XP version on my computer is newer than the one on the CD and it can't do the install. Heck, I just installed the version on the CD on a new hard drive.  Computers drive me crazy.

---

### Post by ugm6hr on 2007-05-27
I'd recommend you download and burn the GParted LiveCD:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Given you've fresh-installed XP - I assume there's no critical data on their yet.  And it sounds as if you haven't created partitions on your drive yet. If so..

Boot from this CD (with the 2nd boot option) and shrink the partition with Windows XP on it to whatever size you want it to be.

Leave the rest unpartitioned / free / empty (whatever Gparted calls it) - however much you want to use for Ubuntu / swap.  I keep reading about using a separate /home partition - but I've not got that far.  Just in case - I'd create an extra partition for data storage (if you can spare some GB) - perhaps easiest to use fat32 format.

Then exit from Gparted LiveCD, and boot Ubuntu LiveCD.  Then use the guided free space option.  Everything should be automatic from there.

---

### Post by henthorn on 2007-05-28
Thanks.  It seems I get so many different answrs I stay confused.  However, I did manage to get the hard drive reformatted and have again installed XP-home on it. I started to load ubuntu again but didn't use the second option as you advise.  I am a little dense.  I do want to set up at least three and possibly four partitions.  I assume the swap file section counts as a partition.  Guess I will try your suggestion and see if it works.  I can alwas re-format the drive and start over.

---

### Post by dptxp on 2007-05-28
No need to be confused.

I assume that XP is fresh install

Run Live CD. Click Install

Choose Manual Mode for partitioning in step 4 (I think it is 4)

Resize the Single partition to 10 -15 GB for XP.

Resize available space to 6-8 GB , ext3 format, mount as root. As primary partition.

Resize the next space to as many partitions as you want for data, choose format ext3 or FAT32,
make sure that all partitions after 3rd one ( 3 incl Windows) are formatted as logical, not primary, and
you are left with 2 GB as last partition to be formatted as SWAP.

Simple and straight.

---


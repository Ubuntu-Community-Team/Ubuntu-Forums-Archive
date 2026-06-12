---
title: "Need Help With Dual-Booting, Partitioning, etc..."
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by gitar1 on 2007-05-21
Have been using Windows for a while, now testing out Ubuntu because of recommendations.

Anyways, I am at the stage where I need to install Ubuntu on a partition.

I have 2 partitions on my main 120GB Drive.
- 1 Windows partition, NTFS, (in use, 11 GB, around 1 GB free space) ---- C: drive
- 1 empty partition, FAT32, (99 GB, all files clear out and transferred to other drives) ---- E: drive

I want to use the empty partition for the Ubuntu installation. What options should I choose under "Select a Disk"?

I try the first option and saw that I need to import files from my Windows partition (C: drive). If I choose to import, would my Windows partition be wiped out? I prefer this to NOT happen.

If I continue the installation this way, do I have the option to dual-boot?

Any help appreciated...

---

### Post by overdrank on 2007-05-21
> **gitar1 said:**
> Have been using Windows for a while, now testing out Ubuntu because of recommendations.

Anyways, I am at the stage where I need to install Ubuntu on a partition.

I have 2 partitions on my main 120GB Drive.
- 1 Windows partition, NTFS, (in use, 11 GB, around 1 GB free space) ---- C: drive
- 1 empty partition, FAT32, (99 GB, all files clear out and transferred to other drives) ---- E: drive

I want to use the empty partition for the Ubuntu installation. What options should I choose under "Select a Disk"?

I try the first option and saw that I need to import files from my Windows partition (C: drive). If I choose to import, would my Windows partition be wiped out? I prefer this to NOT happen.

If I continue the installation this way, do I have the option to dual-boot?

Any help appreciated...

Hi and welcome this link may help lead you in the right direction
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
If you choose the manual install you will be able to choose the partition to install on and setup a swap file also. Hope this helps Good luck!:KS

---

### Post by drowner on 2007-05-21
> **gitar1 said:**
> Have been using Windows for a while, now testing out Ubuntu because of recommendations.

Anyways, I am at the stage where I need to install Ubuntu on a partition.

I have 2 partitions on my main 120GB Drive.
- 1 Windows partition, NTFS, (in use, 11 GB, around 1 GB free space) ---- C: drive
- 1 empty partition, FAT32, (99 GB, all files clear out and transferred to other drives) ---- E: drive

I want to use the empty partition for the Ubuntu installation. What options should I choose under "Select a Disk"?

I try the first option and saw that I need to import files from my Windows partition (C: drive). If I choose to import, would my Windows partition be wiped out? I prefer this to NOT happen.

If I continue the installation this way, do I have the option to dual-boot?

Any help appreciated...

I have actually never done an install from a live-CD, so I am NOT the person to give you the best advice.

I CAN tell you this: if you want to save your windows partition, select the 'manually edit partition table' option, i assume its the same in a live-cd?

---

### Post by amaroKer on 2007-05-21
I suggest "manual" partitioning.  Don't select either of the "guided" options.  I'd also suggest having a separate partition as your home folder as well.  Ubuntu will only really use about 10GB at the most including hundreds of programs, so the other 88-90 GB might as well be separated from it.

The disc(s) you're selecting are the main install partitions.  Put the root filesystem, called "/", on your 10+GB partition.  If you decided to make a separate /home partition, set "/home" to the other one.  Format / as ext3 or ReiserFS, and /home as the same as /, unless you want it to be FAT32 for windows to read.  Windows can be enabled to read Linux file systems with a simple program, but don't ask me what that is called.

Hope this helps...

You won't wipe your NTFS partition by importing settings.  I myself hold no value in importing Windows settings, because I would completely change everything anyway, but feel free to experiment with it.  If you don't like it, install it again.

Ubuntu will automatically setup dual-boot (don't quote me, you might need to check a box or something.  Just keep an eye out for the option).

---

### Post by gitar1 on 2007-05-21
Everything is working great.

The dual-boot screen popped up with options for Ubuntu and Windows.

Will slowly migrate from Windows to Ubuntu, so much cleaner.

Thanks for all the help!

---

### Post by overdrank on 2007-05-21
> **gitar1 said:**
> Everything is working great.

The dual-boot screen popped up with options for Ubuntu and Windows.

Will slowly migrate from Windows to Ubuntu, so much cleaner.

Thanks for all the help!

Congrats and welcome again!=D>

---


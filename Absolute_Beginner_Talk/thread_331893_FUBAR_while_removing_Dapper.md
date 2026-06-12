---
title: "FUBAR while removing Dapper"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by chroniker on 2007-01-05
Yep, I'm a linux noob.

I have a box that was dual-booted with xp pro and breezy which I installed dapper on once I got the disks. The 40 gig HD was partitioned with xp on 15 gig and ubuntu on the remainder with a 1 gig swap file partition. I also have a sepperate 80 gig HD that I use for storage that is NTFS.

During the installation of dapper and after checking the partitions after the install, I managed to convince myself that dapper didn't install over breezy. It looked to me like that it created a new partition and installed there (I may have some how told it to, don't know now).

Time marches on and xp and dapper are working great and I had no problems. However, I was bugged about the way the installation of dapper went and wanted to do a good clean install with just 3 partitions, xp/dapper/swap. 

So, earlier this week I start searching this forum for a way to remove ubuntu and found a way to do so. I drop in one of my dapper disks, get to the desk top, bring up the console and enter "sudo cfdisk /dev/hda". Since all partitions listed were labeled as linux, I remove all of them (I'm going to say it again, all partitions listed were labeled as linux). I then shut down ubunto and replace the dapper disk with xp and allow it to reboot. When I get to the xp recovery console I tell it to fixmbr and after reading the fubar warning I tell it to continue.

Some of you have already figured out where I'm going but for those who don't know .....now when I boot up, all I get is a blinking curser and nothing else. Zero, zip, zilch, nada.

Going back to dapper live I take a look at the partitions and find fubar indeed. Since there was no great loss there my only concern is the NTFS storage drive. So, my question to you who know more than I, if I go with a straight ubuntu box will dapper be able to read and write to the NTFS drive or am I going to have to reinstall xp?

---

### Post by petersjm on 2007-01-05
AFAIK, you can get Ubuntu to read/write to NTFS, but it's tricky and it's a little dangerous. To work successfully, it should be formatted as FAT32, but you'd lose your files if you did that. I'm really not 100% sure, but that's how I see it, anyway...

---

### Post by SyvanX on 2007-01-05
Ubuntu can Read NTFS just fine, it's the writing that's a problem.  I'm not sure how much you're using on the NTFS drive, but if you can back it up to your 40gig laptop, then convert to FAT32, and restore the data to the drive, it would be perfectly read/writable from ubuntu and windows.

---


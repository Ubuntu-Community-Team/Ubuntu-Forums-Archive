---
title: "External HDD"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by moebob24 on 2007-06-08
I have a 320GB iomega external USB 2.0 high speed hard drive, i use to back up everything for my computer. Can it be used with Ubuntu? what about flash drives?



Hey could i run Ubuntu off of the external hard drive and set up the BIOS to boot from that?????....just thought of that.:p:p:p:p:p

---

### Post by jonward0690 on 2007-06-08
Yes but the HDD will have to be reformated to Fat32.

---

### Post by jonward0690 on 2007-06-08
Yes Flash drives will work to and you can run Ubuntu off an external HDD.

---

### Post by moebob24 on 2007-06-08
sweeeeeet....im not sure i want to convert it to FAT32 though. Oh well maybe i will Thanks guys:)

---

### Post by Rocket2DMn on 2007-06-08
I have an external HD that is NTFS, it works fine with ntfs-3g and write enabled

---

### Post by moebob24 on 2007-06-08
> **Rocket2DMn said:**
> I have an external HD that is NTFS, it works fine with ntfs-3g and write enabled


I am wondering if i can boot ubuntu from the drive but still access the other data on the drive. What i am trying to ask is what are the rules for running ubuntu off an external drive? how would i go about doing this. I am pretty computer literate but not when it comes to the REALLY technical stuff that has to do with the OS and all that good stuff.

---

### Post by tdrusk on 2007-06-08
> **moebob24 said:**
> I am wondering if i can boot ubuntu from the drive but still access the other data on the drive. What i am trying to ask is what are the rules for running ubuntu off an external drive? how would i go about doing this. I am pretty computer literate but not when it comes to the REALLY technical stuff that has to do with the OS and all that good stuff.
I'm sure that would work. You would need to partition the drive with gparted (in the ubuntu live install), give it about 10 gigs since you have all that space. Then install Ubuntu onto that. After that  make sure your computer's BIOS is set to boot the external HDD.

---

### Post by moebob24 on 2007-06-08
> **fuzzyhair said:**
> I'm sure that would work. You would need to partition the drive with gparted (in the ubuntu live install), give it about 10 gigs since you have all that space. Then install Ubuntu onto that. After that  make sure your computer's BIOS is set to boot the external HDD.
 I have already checked...i was wrong my drive is FAT32 is there a program that will partition the drive? or does winXP have some sort of wizard or whatever for that. I am good on the BIOS and getting OS installed should be no problem. But setting up my drive is where i have the questions.

---

### Post by confused57 on 2007-06-08
The gparted live cd is an excellent partitioning utility:
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

If you have data on the hard drive that you don't want to lose, you could resize the FAT32 partition with the Ubuntu install cd(or the gparted live cd)...but you might need to defrag the drive, if it has data on it.  If you have a newer pc with the latest bios, you shouldn't have any problems installing Ubuntu on a partition at the end of the hard drive.  It's probably best to try to have Ubuntu on a partition at or near the beginning of the drive, just to be sure.

There's an excellent guide on this site for installing with the live cd:
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

You want to make sure to install grub to the external hard drive's mbr...set your USB drive in bios to boot before your internal hard drive, before booting up the live cd to install Ubuntu.  There is an "Advanced" button that you can select at the grub install stage...to be absolutely sure, you could type in /dev/sda(although your USB drive "should" be hd0, since it's selected to boot before you internal drive), or whatever your external drive is designated in Ubuntu.

---


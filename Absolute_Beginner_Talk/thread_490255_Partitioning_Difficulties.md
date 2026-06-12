---
title: "Partitioning Difficulties"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by prayingmantis on 2007-07-02
Hello,

I was trying to install Ubuntu on a Ferrari 4000 laptop that has a 100 gig drive. It was previously partitioned using Acronis Disk Director (with dual boot configuration) to be 3 drives under Windows (29.2, 29.2, and 22.4), with ext3 and swap partition at the end for Suse Linux (totalling about 10 gigs, if I remember correctly).

I wanted to give Ubuntu a try on the hard drive by replacing Suse. However, when I boot the 7.04 DVD (either live or text based), my only options for partitioning are to completely start over and repartition the drive. It detects it only as a 100 gig /hda drive, no other partitions are detected. I loaded gparted and the I received a message concerning not being able to have overlapping partitions - I do not know if this is the reason I can only view the entire 100gb drive as /hda within the Installer (it doesn't detect the current partition scheme). 

I wasn't able to get far with gparted either, as it gives the overlapping error and won't let me do anything besides completely repartition the drive.

If anyone has any ideas, I'd greatly, greatly appreciate it, as I would have loved to try out Ubuntu. It seems fast from the LiveCD, and I'd like to see how it compares to Suse (but at least Suse installed fine).

Thanks so much for any help!!! 
-Chris

---

### Post by vanadium on 2007-07-02
You should not have the need to repartition: you can use the existing ext3 and swap partitions. Alternatively, you should be able to delete these two Suse partitions and repartition for your Ubuntu installation. You have three Windows partitions. Your Suse partitions therefore both live in one fourth, extended partition because you can only have at most 4 primary partitions. Using gparted, yo might have overlooked something: you should be able to delete some partitions, otherwise it might be your Acronis utility that has a peculiar way of partitioning. In that case, you could try changing the partitions using acronis.

---

### Post by eternalsword on 2007-07-02
Using the install dvd you probably need to do the Manually Edit Partition tables option or something similar, otherwise it will assume you want to use the entire drive.  Hope that helps.

---

### Post by prayingmantis on 2007-07-02
Hi,

Thanks for the quick replies. Unfortunately, I tried the manual partitioning options, and the only option it gives me is to repartition the entire drive. It won't detect any of my other partitions, just the entire /hda one. 

From the manual partitioning screen, it comes up as /hda 100 gigabytes and all of it is listed as "freespace"

:-(

Not quite sure why Suse recognizes all of the partitions fine and Ubuntu doesn't on the install. Any ideas for a way around it would be greatles appreciated! Thanks again for the help.

-Chris

---

### Post by eternalsword on 2007-07-04
I suppose you could try gparted's livecd [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) to make a ext3 partition for ubuntu.  but this should probably filed as a bug on launchpad if the installer is not detecting the partitions.

---


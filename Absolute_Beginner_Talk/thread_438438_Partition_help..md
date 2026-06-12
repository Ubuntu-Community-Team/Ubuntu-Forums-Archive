---
title: "Partition help."
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by k0rn on 2007-05-09
On the manual parition screen this is what i get.

Device        Type       Mount Point   Format      size            used

/dev/sda

/dev/sda1   NTFS      /media/sda1              106303mb      unknown

free space                                                         8mb

/dev/sda2   FAT32     /media/sda2               12643mb      11200mb

/dev/sda3   NTFS       /media/sda3                1077mb         606mb


How would i go about doing the parition. With out loseing windows and haveing enough space to save stuff on windows and save stuff on ubuntu. I apreciate any help.

---

### Post by k0rn on 2007-05-09
Sorry it was spread out better with spaces when i wrote it out.

---

### Post by ghostboy on 2007-05-09
I would suggest that you use the GParted utility that comes with Ubuntu to resize your partitions.  HOWEVER!  Be very carfeul if you dont partition them correctly, your going to loose all of your work.  [COLOR="Red"]**BACK UP EVERYTHING BEFORE STARTING THIS PROCESS!!!!!!**[/COLOR]  Also I would check out this tutorial.  It may be able to help you.[http://www.howtoforge.com/partitioning_with_gparted]("http://www.howtoforge.com/partitioning_with_gparted")

---


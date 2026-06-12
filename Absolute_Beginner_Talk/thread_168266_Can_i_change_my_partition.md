---
title: "Can i change my partition?"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by Costas on 2006-04-30
Hi everybody, 

i got involved with Ubuntu 3 weeks ago and everything sems to be going alright so far. My laptop is dual boot with XP, since i u se 1-2 programs hat can not run in linux. 
The partition i have is: 

1) hda1, for windows platform (30 Gb) NTFS, 

2) hda2, a common Linux/XP (20 Gb) vFAT, 

3) hda3, the SWAP partition (1 Gb), and 

4) hda4, the Ubuntu one (6 Gb). 

Is there a way i can change this partition without having to format everything and start over again? what i want to do is decrease hda1 and leave more space for hda2 and hda4.....

Any help would be much appreciated!

thanx

---

### Post by Koybe on 2006-04-30
I think it will be tricky. The better way is to restart install. Anyway you can try to change this with gparted.

---

### Post by gborzi on 2006-04-30
There is a GNU tool called parted to modify the partition of your disk. In order to use it the partitions you are going to modify must be unmounted, so you should use it from a live distribution, such as the one provided here [http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

### Post by Costas on 2006-04-30
Just managed to decrease the XP platform down to 20Gb and increased the common partition to 30 Gb, using Magic Partiton....
next step will be to increase the linux one and further decrease the XP one...if i don't suffer from a heart-attack!  :-)

---

### Post by Sef on 2006-04-30
> ...using Magic Partiton....

If that is Partition Magic (PM), be careful.  PM and Linux tend not to get along very well.  Quite a number of posts with problems using it.  Best to use another partitioner.

---

### Post by Costas on 2006-04-30
Thanx for your repply/advise Sef... i used partition magic and i was able to play around the XP and the common directory.  PM sees all the partitions on my hd but can change only the ones used by windows (i think). Everything seems to be working out fine now (fingers crossed)!

---

### Post by MHlavsa on 2006-04-30
Is it possible to change the format of partitions without reinstalling everything?

---


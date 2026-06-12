---
title: "Imaging larger drive onto a smaller drive"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by hpm8120n on 2007-07-17
I have a new desktop machine with a 320GB hard drive and a clean, new Windows Vista on it.

I would like to transfer the Windows Vista installation to a 150GB 10,000 RPM raptor drive
and then later make it dual boot between Vista and Ubuntu.

I'm familiar with dd although I've only used it to clone drives with exactly the same size.

Can somebody tell me if there is an easy way to image the 320GB drive onto the 150GB
drive?  I'd like to use open source tools if possible and don't mind at all booting into a linux
live CD to get it done.

Thank you.

---

### Post by punx45 on 2007-07-17
it would seem to me that the only way this were possible is if the drive with vista was partitioned, and the partition was smaller than 150GB.    and im guessing its not.

however, seeing that your final goal is to dual boot, it is possible to dual boot with two disks.   this may save you some frustration.

---

### Post by hpm8120n on 2007-07-17
> **punx45 said:**
> it would seem to me that the only way this were possible is if the drive with vista was partitioned, and the partition was smaller than 150GB.    and im guessing its not.

however, seeing that your final goal is to dual boot, it is possible to dual boot with two disks.   this may save you some frustration.

The Vista box is a new box.  The size of the installation is far smaller than 320 GB or 150 GB.

Are you familiar with Ghost?  I'm wondering if there is an open source equivalent to Ghost.

Thank you.

---

### Post by hysteresis on 2007-07-17
Use HDClone free edition
[http://www.miray.de/products/sat.hdclone.html](http://www.miray.de/products/sat.hdclone.html)
Miray Software - HDClone - hard disk copy - hard disk backup - hard disk rescue
to transfer it to your smaller drive. I have used hdclone many times to transfer large drives to smaller drives;
The program just ignores all the extra space on the larger drive.

partimage is the open source equivalent to ghost. I have never used it.


Edit: If your partition size is larger than 150gb you need to resize with gparted before you use hdclone.

---

### Post by rscott5 on 2007-07-17
If the partition is ntfs:

ntfsclone works great for moving ntfs partitions. I've only used that for drive-to-drive where the drives as the same size though. One option might be to use something like Partition Magic or GParted(free, opensource) to resize the partition to fit on the Raptor, then copy it over. I'd say do some research on ntfsclone, it works really well and fast.

---

### Post by bodhi.zazen on 2007-07-17
The gparted live CD will do this work for you.

Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)
	Download: [Download Gparted](http://easynews.dl.sourceforge.net/sourceforge/gparted/gparted-livecd-0.3.4-8.iso)

	"2 Page review" [http://techgage.com/article/gparted_livecd_31-1/1](http://techgage.com/article/gparted_livecd_31-1/1)


======


There is also a clonezilla

[http://clonezilla.sourceforge.net/gparted-clonezilla/](http://clonezilla.sourceforge.net/gparted-clonezilla/)

---

### Post by punx45 on 2007-07-17
I stand corrected. :-D

---

### Post by crispy_420 on 2007-07-17
Couldn't you use the GParted LiveCD to shrink the NTFS partition and go from there?

---

### Post by punx45 on 2007-07-18
according to the docs, clonezilla will actually disregard unused blocks, which would appear to be more beneficial for this use.

---


---
title: "Help with partitioning"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by jgf621 on 2006-12-22
I'm trying to install ver. 6.10 on a 250gb drive.  I used QTparted (from Knoppix) to repartition , setting up a new virtual drive at 102 gb.  

Going to Ubuntu install, I used "manual partition" choice when asked.  message prompted me to set up another partition "/" of not less than 2 GB as a Root file structure.  I tried and failed. Hitting button that says go back and fix in QTParted kills entire install.

I couldn't find a choice that seemed to match.  I went back to (fuller featured) QTparted in Knoppix and tried there.  No luck.

I have created one large Linux-swap partition but am dead in the water until I can get by this smaller partition.

What have I missed?  Thanks in advance for any help .

---

### Post by bodhi.zazen on 2006-12-22
> **jgf621 said:**
> I'm trying to install ver. 6.10 on a 250gb drive.  I used QTparted (from Knoppix) to repartition , setting up a new virtual drive at 102 gb.  

Going to Ubuntu install, I used "manual partition" choice when asked.  message prompted me to set up another partition "/" of not less than 2 GB as a Root file structure.  I tried and failed. Hitting button that says go back and fix in QTParted kills entire install.

I couldn't find a choice that seemed to match.  I went back to (fuller featured) QTparted in Knoppix and tried there.  No luck.

I have created one large Linux-swap partition but am dead in the water until I can get by this smaller partition.

What have I missed?  Thanks in advance for any help .

You need a minimum of 2 partitions for ubuntu.

Swap = ram X2, 1 Gb max

root = 10-15 Gb max. 

Give the rest of your HD to a data partition.

If you keep having difficulty, boot to Knoppix, delete all partitions, and partition with the Ubuntu CD :)

---

### Post by Bartender on 2006-12-22
What do you mean by a "virtual drive"?

If you've got broadband, download [GParted]("http://gparted.sourceforge.net/livecd.php") LiveCD, make a bootable CD from the download, set your PC to boot from the optical drive, restart with GParted LiveCD in the tray.  Use the partitioner to unformat your "virtual partition" (whatever that is) and create an ext3 primary partition to the right of the Windows partition.
Close out of GParted, eject the CD, toss the Ubuntu CD in the tray, restart the PC, when you get to the partitioning section choose manually partition and point the Ubuntu install at the ext3 partition.

Also, read thru [aysiu's]("http://www.psychocats.net/ubuntu/index.php") guide.  That's his main page.  Look in the list over there to the left, about five down from the top.

---


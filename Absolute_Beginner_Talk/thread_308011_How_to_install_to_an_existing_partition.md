---
title: "How to install to an existing partition?"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by sling-shot on 2006-11-27
Hi,
I have downloaded the latest Ubuntu LiveCD after one week of sustained efforts! (Eh, i am on a dial-up connection you see)

Finally managed to launch the CD and into the install.
Then i run into this problem ](*,) 
Ubuntu Installer gives me only two options
1. Complete hard disk format and install
2. Manual partition
When i select manual partition, it does not recognize any existing partitions, instead showing the whole 160GB SATA harddisk as a single unit.

Now i already have the following installed there
1. WindowsXP Professional
peacefully co-existing with
2. PCLinuxOS
3. Two empty Ext3 partitions for a) Ubuntu b) Any other distro i may take fancy to... (after all it is an open world)

BASICALLY, is there any way to ask Ubuntu "Kindly install yourself into this particular partition because it is where i would like you to be!" ???

[PCLinuxOS has the best installer in this aspect: It allows you to manually partition the hard disk, installs to any partition you choose, and also gives you the choice of installing the bootloader to MBR or boot record of the particular partition (which is where it is lying now since i use Windows bootloader for my existing dual boot set-up.]

Thanks in advance,
-SS.

---

### Post by Bachstelze on 2006-11-27
As always :

get an "Alternate" CD, will be worth a few extra days of download ;)

---

### Post by sling-shot on 2006-11-27
Please........!!! That is another WEEK!
In case i muster up the courage to do that would you please tell me where can i find the suitable 'alternate' .iso?
-SS.

---

### Post by duality on 2006-11-27
You would have to resize an existing partition to make room for Linux partitions as Windows uses NTFS or FAT partitions, you need to make them smaller (i havent personally used the graphical installer) but im sure that there is an option to resize them,. As this is posted in the newbie forum i would suggest that you first make backup so nothing bad happens when you try to resize the NTFS/FAT, or make sure to really know what you are doing with some tutorial or guide to doing this.
Then for installing Ubuntu make a Swap partitions and one root partition (root with ext3).
GL

---

### Post by duality on 2006-11-27
[http://easylinux.wordpress.com/2006/04/30/ubuntu-dapper-drake-beta-installation-from-live-cd/](http://easylinux.wordpress.com/2006/04/30/ubuntu-dapper-drake-beta-installation-from-live-cd/)

heres a good guide, i hope it helps.

---

### Post by sling-shot on 2006-11-27
Since the partitions are not at all recognised as existing there is no question of resizing the partition.
And i already have suitable partitions, including  swap and home and root ready.
So it should be a fairly straightforward installation?
Is there any other way of installing (say commandline)?
-SS.

---


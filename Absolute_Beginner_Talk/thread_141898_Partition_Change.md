---
title: "Partition Change"
date: 2006-03-09
forum: Absolute Beginner Talk
---

### Post by seekyrr on 2006-03-09
Used my entire HD for Breezy 5.10 installation.  Would like to repartition and use some of the free space to install Windows for a dual boot.  

Is this possible, or do I have to do a fresh install?

Thanks

Seek

---

### Post by cilynx on 2006-03-09
Look into gParted.  It does exactly what you want.

---

### Post by StefanoCole on 2006-03-10
I think you have to repartition Breezy using a live cd and a partitioning tool like GParted or QTParted.

By the way, the Breezy live CD contains GParted.

Stefano

---

### Post by AtinLango on 2006-03-10
[QUOTE=seekyrr]Used my entire HD for Breezy 5.10 installation.  Would like to repartition and use some of the free space to install Windows for a dual boot. [/QUOTE]

Not quite clear to me what you want to do? Whatever it is, I think it is about resizing partitions.

I have successfully used Gparted many times for reducing partition size. I nearly used QTPatred but I think they pretty much do the same thing.

My comment is that you can use Gparted (and I think QTParted) for reducing partition size (re-sizing is an overstatement since it restricts movement of certain filesystems).

---

### Post by Jagot on 2006-03-10
GParted can certainly reduce your partition.  You will need to either do that from the Ubuntu Live CD as Stefano said, or GParted actually has it's own [Live CD]("http://gparted.sourceforge.net/livecd.php") which should also do the job.  Another alternative is the [SystemRescueCD]("http://www.sysresccd.org/Main_Page") which uses contains QTParted, amongst other tools, which essentially does the same thing.

You will have to format the free space you have made when you install Windows itself.  Installing Windows will overwrite the MBR so it will get rid of GRUB.  To be able to choose which operating system you use, you will need to reinstall GRUB from the Ubuntu install CD.

I have heard however that Windows likes being first on the hard disk (reducing your partition would I think automatically leave the free space at the end of the disk), so I'm not sure if that may cause any problems - not sure if GParted can move partitions - perhaps someone more knowledgeable can fill you in on that one.

Jagot

---

### Post by seekyrr on 2006-03-14
Got gparted.  It says I will loose all the data in the partion if I resize...if so I may as well redoo from scratch.

Am I doing something wrong?

Seek

---

### Post by AtinLango on 2006-03-15
[QUOTE=Jagot]not sure if GParted can move partitions - perhaps someone more knowledgeable can fill you in on that one.Jagot[/QUOTE]

GParted can move only fat16, fat32 and linux swap.

---

### Post by cotcot on 2006-03-15
Is your Breezy on LVM ? If yes , shrinking LVM is possible : see LVM howto. (sometimes Breezy install with LVM as a default).

If not you could try the following :
Shrink (not move) the Breezy partition with parted (G or QT) from a liveCD. This should be possible unless the partition is full.
Use "partimage" from a live CD to make an image of your HDD to DVD, CD or External HDD. You need to back-up anyway. If these are not available you could use the free space on the HDD to save the image to. 
Then delete the breezy partition. 
Then install windows and after it restore your image to a new partition on the HDD. This partition needs to have at least the same size as the partition from where you made the image from. Afterwards you can resize the Breezy to the size you want. At this moment you will only have windows when you boot. So you have to reinstall grub. This is explained in other threads of this forum (search on "MBR messed up".

---


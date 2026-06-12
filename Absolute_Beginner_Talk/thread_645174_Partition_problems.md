---
title: "Partition problems"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by arpeggi on 2007-12-19
[IMG]http://i2.photobucket.com/albums/y18/laurie_humphrey/PARTITIONSMedium.jpg[/IMG]

i have a 3 month old dell vostro 1700 with windows vista installed. i haven't made any alterations to partitions - this is how it came.  (ignore the z:/ that is an external HD).  i'm unsure about what these partitions are - i know i can only have 4 and i'm trying to create a new one for a gutsy installation.

any help greatly appreciated!

---

### Post by Beaucephus on 2007-12-19
It doesnt look like they saved you much room for another partition.  I'm not sure what the 118 MB partition is, but if your looking for a place to put Linux I would look at the 6GB Recovery partition.  I dont think NTFS partitions can be safely resized.  

If you have the Vista boot media (getting rare these days) you can partition the drives properly and start from scratch with 2 new partitions.  

BTW, 4 partitions is the limit to PRIMARY partitions.  You can create extended partitions to get more if you need.

---

### Post by bodhi.zazen on 2007-12-19
> **Beaucephus said:**
> It doesnt look like they saved you much room for another partition.  I'm not sure what the 118 MB partition is, but if your looking for a place to put Linux I would look at the 6GB Recovery partition.  I dont think NTFS partitions can be safely resized.  

If you have the Vista boot media (getting rare these days) you can partition the drives properly and start from scratch with 2 new partitions.  

BTW, 4 partitions is the limit to PRIMARY partitions.  You can create extended partitions to get more if you need.

You can resize a NTFS partition with no problems. Defragement it first.

Also you should back up any data you do not want to loose.

You will need to do some work though as you already have 4 partitions on the HD. You will need to delete one (you may be able to move the 2 Gb partiton) and make an Extended partition. You can the put logical partitions in the extedned partition.

Use the partition management tools in Vista to resize, then Gparted for partition management. 

I suggest a 10 Gb / (root) partition for ubuntu + a 1 Gb swap partition.

You should read this : [http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

And this : Gparted [Documentation](http://gparted.sourceforge.net/documentation.php)

---

### Post by bernied on 2007-12-19
Or you could install on a seperate hard drive, and save yourself a lot of anxiety and trouble - for a price (but if you can afford a PC that can run vista, then you can afford another drive for an OS upgrade).

---


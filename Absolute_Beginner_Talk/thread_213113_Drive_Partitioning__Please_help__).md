---
title: "Drive Partitioning?  Please help  :)"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by tees0230 on 2006-07-10
I would like to install Ubuntu on my laptop, but I only have one hard drive and I do not want to pay for a partitioning tool like partition magic.  Does the Ubuntu installer do the partitioning work for me, or do I need a separate program?  If I need a separate program, does anyone know which one I should use?  I have a bunch of stuff I've accumulated on this computer that I would hate to lose in the event of any partitioning gone wrong, so the more reliable and safe the program, the better.

Thanks in advance for any assistance I may receive.

-D-

---

### Post by briguy on 2006-07-10
Ubuntu will resize your partition for you, although I haven't tried myself.  As for Partition Magic, there is a gtkparted livecd out there - check out [http://www.reviewlinux.com/index.php/?m=show&id=2358](http://www.reviewlinux.com/index.php/?m=show&id=2358)

---

### Post by Sonofmoog on 2006-07-10
The GNOME Partitioner, GParted, is built into the Ubuntu livecd, and is very good.  You should have no problems creating a partition for Ubuntu.  Be sure to create a swap partition, too (2 x RAM is recommended).  How much space will you need for Ubuntu?  Only you can answer that .. And, be aware that while GParted works reliably, partitioning is high risk business, and there's always a chance of data loss.  Be sure all of your files are backed up before you begin.

---

### Post by orb9220 on 2006-07-10
also Also ALSO!  run Defrag on your windows partition when in XP first.

Gpart can have problems doing its magic on a fragged HD.

So Just Defrag HD three times to get all the files moved to front of the HD.

Then resize with Gpart.

](*,)

---

### Post by fhqwhgads on 2006-07-10
If you really want to save that data, back up to an external drive first. Better safe...

---

### Post by moshuptrail on 2006-07-10
Gparted works well, but if you have any bad blocks it will not operate on the drive, but gives only a cryptic message.
I had to use ntfsresize with the -b option (for bad blocks) from the command line instead.  That works well too and it will operate on a drive with bad blocks but gives you dire warnings.
I took a 20g HD and split it to 10G for win XP, 1G for home, 1G for swap, and 8G for Ubuntu.  Just a note: When I installed Ubuntu it didn't say it was creating a dual boot menu (or I missed the message), but it did it anyway.

---


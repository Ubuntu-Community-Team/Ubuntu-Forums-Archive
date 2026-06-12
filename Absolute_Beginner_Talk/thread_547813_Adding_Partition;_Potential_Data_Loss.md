---
title: "Adding Partition; Potential Data Loss?"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by Ek0nomik on 2007-09-10
I am looking at adding Windows onto my main box.  Quake Wars is coming out soon and I am looking at getting it, and as such I'll need Windows (until a Linux version gets released).

I have attached a picture of what gparted is showing about my hard disk.  Can I simply create another partition and add Windows onto it (I know that there's a bit more to it than that)?  Or will I be losing data at the end of the hard drive?  Is gparted actually showing me all the pieces of data or is there information at the end of my current partition?

Thanks!

---

### Post by toasterofirony on 2007-09-10
Always the potential for something to go wrong.

Back yo' stuff up.

---

### Post by Ek0nomik on 2007-09-10
> **toasterofirony said:**
> Always the potential for something to go wrong.

Back yo' stuff up.

Right, but how is Linux handling the writing to the hard drive.  I understand that there is potential for data loss, but to what degree?  In Windows if you look at your hard drive, data is completely scattered across the drive.  But GParted is showing otherwise.  Are they handling the writing to the disk differently?

---

### Post by shae on 2007-09-10
In linux, data is scattered across the drive with large open spaces between the clusters.  This allows for file expansion, which is why ext3 is so resistant to fragmentation.  When you resize the partition, the data should be moved, but in case of error, you should back up all important data anytime you resize partitions.

---


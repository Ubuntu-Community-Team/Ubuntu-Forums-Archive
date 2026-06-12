---
title: "Write to HDD failure during Partitioning"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by sperrett on 2007-05-17
I have windows installed on a 200Gb HHD formated to NTFS.  I run the live CD of Ubuntu 7.04 and have no problems.  I decided to install Ubuntu and it asks a few questions (although not exactly as shown in the official documentation, why?).

My problem occurs when the installation tries to partition my hard drive.  It first says that it has to write changes to the disk but comes back and say that it can't.  Then partitioning does not occur.

I trolled the forum but couldn't find anyone with this particular error.  I will try and use gparted to do the partition manually, but hoped their was another fix.

Any help would be great.

---

### Post by gn2 on 2007-05-17
It is possible that the Ubuntu partitioning tool is unable to create the desired partition because there is data on it.
.
For example if you wish to reduce a 200g NTFS drive to 150g leaving 50g unallocated to install Ubuntu on, if there's any data present in the last 50g, the partitioning will fail.

I use Partition Magic to re-size NTFS partitions, and leave free space to install Ubuntu to.

Sadly it's a paid-for app, but it's the only way I've found to reliably clear data out of the way.

---

### Post by sperrett on 2007-05-17
The hdd shouldn't have any data placed at the new section.  My windows installation was originally on a 60GB drive.  i used Seagate's free utility to make an exact copy of the drive onto the 200GB.  So at worst the data should only be scattered in the firse 60GB portion of the new hardrive.

But I feel the error I'm having occurs before it trys to partition.  Ubuntu says it is trying to write settings to the hard drive before it partitions and this is when it says it can't and hence won't start the partitioning process.

---

### Post by gn2 on 2007-05-17
A simple way to find out where the data is located is to run Disk Defragmenter.

You would think that the data would only go at the start, but it could be scattered across the whole  drive.

Lots of helpful info here: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by floke on 2007-05-17
I would advise against using the 7.04 partitioner, since whenever I've tried to use it, it has mounted the HDD after creating the partition, and cannot complete the process (scan for errors etc.). It's complete rubbish IMO. Use gparted for sure off its own cd or from 6.10.

---

### Post by sperrett on 2007-05-17
I read through the hermanzone site.  It seems very good.  I read the section on installing using the 'alternate CD' and found the screen when I come undone.

Its under the "Windows with NTFS + Feisty Fawn with /home Partition" figure 19.  I get an error here saying it can't write to disk.

I believe this is a different problem than just the method of partitioning, since partitioning hasn't started at this point.

---

### Post by floke on 2007-05-18
Make sure you do a full defrag and scandisc on your windows partition first.
Also - if in the defrag you have non-removable blocks on the right, you might need to turn off your hibernation + swap file in NTFS.
Also - you could try installing without creating a separate home directory, since this can be set up easily later

---

### Post by swudee on 2007-05-18
Yup I find feistys partitioner unusable, I have to use the one on edgy. It fails because it automatically mounts all of the partitions before it it changes them and then says it can't do it because the Partition is mounted!!!

---

### Post by sperrett on 2007-05-18
I finall got it to work using the 'alternate disk', plus a bit of mucking around switching drives from master to slave.

---

### Post by floke on 2007-05-18
Good for you!
And ballacks to the Feisty partitioner. It's crap!

---


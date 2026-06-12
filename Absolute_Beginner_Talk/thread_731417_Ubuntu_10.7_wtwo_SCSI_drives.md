---
title: "Ubuntu 10.7 w/two SCSI drives"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by Dana on 2008-03-21
First of all, kudos to Ubuntu for painlessly installing on a SCSI system. I expected all sorts of problems but it just worked.

Pc is an old Pentium class with an overdrive processor and to 18Gb SCSI drives with a Tekram DC390U2W controller. It looks as if as intended Ubuntu installed on SBA. What I don't quite fathom is, was anything done with second drive? Do I need to partition and mount this drive separately? My thought was to put /home on the second drive. 

I could just leave things alone and use the second drive for the new Ubuntu release when the time comes but maintaining my /home there appeals to me.

Dana

---

### Post by Redache on 2008-03-21
Unless the drive was partitioned before you'd need to repartition the drive using GParted. Usually you'd have to specify the mount point as /home during installation for it to work. It might be possible post install but there's a risk of data loss there so I won't recommend it. 

If you read up on GParted you should be able to get help on how to specify mount points.

---

### Post by Dana on 2008-03-21
I'll have to study this a bit. I deleted all the partitions on both drives before installing Ubuntu. I tried to do a manual partition for both drives but kept getting an error about not being able to do ext3, or some such. Settled finally for guided partition of SDA, figuring I'd figure out the second drive later. Will use the CD to partition the second drive.

Dana

---

### Post by Dana on 2008-03-22
gparted doesn't seem to be working for me with my default installation. I don't see any sort of partition manager under Administration or Preferences. Didn't work from the command line. Fired up Synaptic and it tells me at least part of it is installed, did not have time to explore what might be wrong. When time permits I'll get back to it.

Ubuntu does not see anything on the second drive since it obviously did not get partitioned, hardware manager does report that it is recognized as a second SCSI drive.

Dana

---


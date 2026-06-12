---
title: "Partitions not that easy"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by Anders J on 2007-06-11
I have a laptop running ubuntu in good health.

Now I want to make my desktop a dual boot system, but it isn't that self-explanatory.

I have two HDD's, the original 120 GB drive and a secondary 250 GB.

The 120 GB came installed as one 80 GB (NTFS, Windows) and one empty 41 GB partition. The 250 GB was added by me. All NTFS.

Running install from live CD and trying to get things right, the partition page currently shows:

hda NTFS 250 GB
hdb0 ext3 41 GB
hdb1 NTFS 80 GB (this is windows boot)

My plan was to create swap and root in the free 41 GB area, I think I can read instructions well enough but I just cannot figure out what to do?

I would prefer to do this graphically, because making a tiny mistake in "sudoing" can obviously get anything to happen.

---

### Post by freebeer on 2007-06-11
gparted is graphic (the leading "g" is a hint to that).

You should be able to select/highlight the 41 GB partition and tell it to delete the partition (so that it is unallocated).  Then repartition it into swap (1 or 2 gigs is plenty) and the rest as / - / will have to be reformatted, I believe but gparted will get that done for you.  

There's probably several other approaches, but I've done this type with success.  (I added a third partition for /home but not everyone does that.)

---

### Post by Inxsible on 2007-06-11
Also check out this link which details the screenshots in Gparted

[Installing]("www.psychocats.net/ubuntu/installing")

---

### Post by Anders J on 2007-06-11
Thanks.

This is what gparted shows me at this moment.

Partition, Filesystem, Mountpoint, Size, Used, Unused
/dev/hda1, ntfs, /media/Ny volym, 233.76 GiB, 129.97 GiB, 112.78 GiB 
/dev/hdb, unknown. /media/disk, 31.53 MiB, ---, ---
unallocated, unallacoted_
/dev/hdb2, ntfs, /media/50_08_40, 74.49 GiB, 32.82 GiB


I'm a bit worried that the windows "C:" is hdb2 and not hdb1 and in any case not hda1.

Would that be healthy for dual boot operation if I proceed or am I in any case ending up destroying my Windows boot possibility?

---

### Post by Inxsible on 2007-06-11
Could you take a screenshot of your drives thru GParted and post it here. It will help us see how you drives are partitioned and structured.

---

### Post by Anders J on 2007-06-11
OK, here we go:

---

### Post by Inxsible on 2007-06-12
on your hdb, you have a 31mb and a 7 mb partition. I do not know what use they are, but the 31 MB seems to be mounted too. You can delete those partitions, but since the space is too small, they wont be useful anyway.

Are you going to install Ubuntu on the internal 80 GB drive ?
if so, make sure you defrag your windows first. atleast a few times.

then come back to gparted and resize the windows partition to create some free space for Ubuntu and install it there. The link i gave you earlier, details this process. 

Oh and Windows being on hdb is not a problem for dual booting. When you install Ubuntu, the grub will automatically detect where you have your windows installed and add it accordingly.

---


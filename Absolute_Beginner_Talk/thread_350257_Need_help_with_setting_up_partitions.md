---
title: "Need help with setting up partitions"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by jqa on 2007-01-31
I want to install Ubuntu on an unused partition of one of my 3 hard drives. The partition is 92Gb. I originally split the 200 GB drive into 2 partitions, one formatted in Windows NFTS, the other untouched and intended for Ubuntu.

I am using a CD that I received directly from Canonical in October of 2006 so I assume it a recent version.

When I go through the installation process I am reminded to allocate  2 Gb (min) for the root (/) partition and 256 Mb for the swap partition. Since I have adequate disk space I want to make the root partition 4 GB and the swap partition 1 Gb.

When I get to step 5 I am instructed to set up the partitions but the only partition available is the root partition and it is using the entire 92 Gb. There is a window where I can specify other partitions (swap, bin, home, etc.) but there is no way to designate their size. There is also no provision for reducing the size of the root partition.

I have looked at some of the links to partitioning help that are in other posts but I have not found anything that addresses my situation.

Anyway, I appreciate help with this setup problem. I am anxious to get it installed and begin migrating from the Windows environment.

---

### Post by podunk on 2007-01-31
I got confused here also.

I used Windows <blushes furiously!> to carve out my partitions. I made 1 partition 20 gig for root, 1 - 2 gig for swap, 1 - 40 gig for /home, and one 50 gig for data (read weekly back ups, I only back up to an external once a month)

In the install I just told it to put root here, swap there, and /home here and format them. I formated the /data partition once the set u[p was complete.

To mount and assign the /home and /data partitions I followed this how to:
[http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

---

### Post by housam on 2007-01-31
First , back-up every thing. then you can use the Gparted partitioning tool to do the job. it is on the live CD . you boot through the live CD and click system >> admin. >> Gnome partition editor.
Repartition the 92Gb partition by clicking on the partition and delete it  to create an unallocated space.
Now devide the unallocated space to 3 new partitions:
10 Gb ext3 for the root ( / )
1 Gb swap for the ( swap )
The rest Gb ext3  as /home partition
After that go for the installation and when it comes to the partition mater , choose the manual way .

---


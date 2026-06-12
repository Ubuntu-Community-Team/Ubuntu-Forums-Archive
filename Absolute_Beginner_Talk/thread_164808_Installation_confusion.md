---
title: "Installation confusion"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by Olaniyan Ibn Yusuf on 2006-04-23
Okay this is what i have going on. I have two hard drives both 80 GBs. I want to be able to mount the /home directory so that it takes up PART of hda and then the rest of hdb

I figured I would use raid0 as this would be the most efficient way of writing data across to physical disks or so I have always been taught. While reading through a LVM guide supplied I found on the net it seems you can do similiar things with just using LVM which would mean I don't really need RAID0.

However I am still a little lost on the entire process and here is why.

1. I know that /boot and / can not be a part of a LVM group if I read properly so they will be created first on hda. /boot will get 100M and / will get 45 GB (do you guys think that is enough?)

2. Once /boot and / are assigned how do I go about assigning the rest of the space on hda as a logical volume so that I can created a volume group and add it to the group? Also how do i get it to span /home from part of of hda to part of hdb?

3. how do I leave a little space at the end of hdb so that I can maybe either create a /tmp folder which I heard was good to do or a /opt folder which I also heard was good to do. 

Long story short, I am not sure given my situation which is better to go with, a software raid or a LVM, and how do i go about setting up a /home partition with in the LVM system which will allow me to write data across to physical drivers.

---

### Post by skinnygmg on 2006-04-23
you should probably post this in regular "Hardware Support" not here in beginner talk.  you will get more replies there.  sorry i can't help any more.

---


---
title: "How do I reset the partitions?"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by kamil212 on 2006-06-13
I got no more hair to pull out:-x 
I just wanted to install a simple ubuntu distro and I got nothing but problems.
I have two SATA 160s on a via fakeRAID.
When I reach the Gparted screen on the installation in the drop down box I have the two drives hda and hdb as well as the 320GB via_%$^$%fee array that I got after installing dmraid.  I tried spiltting that into 3 partitions, root, swap and home and I ended up with two 160s hda and hdb as well as a 10GB viafee1, 2GB viafee2, and 308GB viafee.  When I tried formating the partitions I get the error and I refresh the partitions in the terminal as mentioned in [the guide ]("http://www.ubuntu-in.org/wiki/SATA_RAID_Howto"). But with no luck.  I can't get all of the three partitions to be ext3.  I got tired and restarted everything. Now after installing dmraid again I get the two harddrives and TWO viafee and viafee1 partitions at 300GB each, *&*(&%$!!! 
I have no idea on how to reset it back so I can start from the beggining.

---

### Post by zxee on 2006-06-13
Have you tried to go into a shell from the installer Alt + F1 and use cfdisk or fdisk to partition your drive(s)? Sometimes the command line tools will work when gparted hiccups. Either cfdisk or fdisk should allow you to change the partition type to anything you want.

---

### Post by kamil212 on 2006-06-13
Can somebody lead me through a command line partitioning of dev/mapper/via_dcotbecfee so I can have a 10GB root, 2GB swap and the rest as home.  Everytime I apply these partitions in Gparted I get an error: "Error while creating /dev/mapper/via_dcotbecfee1"
Thanks

---


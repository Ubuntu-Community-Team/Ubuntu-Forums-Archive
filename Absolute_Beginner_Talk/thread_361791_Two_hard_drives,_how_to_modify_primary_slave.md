---
title: "Two hard drives, how to modify primary slave"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-02-14
Dapper got broken fixing some sound problems.

I posted about this and was told (below is from memory NOT literal)

sudo dpkg --reconfigure xserver-xorg and x-something else.

The various screens came up about resolution, number of keys on the keyboard, etc. and all looked well. The "reconfig" finished and I rebooted. Now I have no GUI, only the command line. And dpkg-reconfigure xserver-xorg does NOTHING.

I have moved my "broken" 40gig to the primary slave on the IDE cable. The Pri-Master is the only way I have to get online.

How can I modify or work on the Primary-Slave disk, and is it MOUNTED, now that it's not the primary-master?

Yes, I have edited the FSTAB, etc. and can read files on the Pri-Slave disk.

---

### Post by aysiu on 2007-02-14
Alt-F2 ```
gksudo nautilus
``` should allow you to make any changes you want on the other disk if it's already mounted.

---


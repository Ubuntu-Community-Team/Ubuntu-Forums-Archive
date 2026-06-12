---
title: "How to expand windows xp partitions using gparted?"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by nanbudh on 2007-10-20
here is a problem. i have the gutsy live desktop-amd cd and i am raring to go. But before i install it i wish to modify my disk partitions a bit.here is the current scene:
partition  Device                Filesystem             Path                        Size
1           /dev/sda1                vFAT               /media/sda1       14.65 GB(2.5 free)
5           /dev/sda5                vFAT               /media/sda5       19.53 GB(9.85 free)
6           /dev/sda6                Ext3               /                        13.97GB(9.87 free)
7           /dev/sda7                Ext3               /home                13.97GB(10.38 free)
8           /dev/sda8                vFAT               /windows       11.08GB(8.66 free)
Swap    /dev/sda9                mem swap                                1.26 GB

Here is the scene i want:
partition  Device                Filesystem             Path                        Size
1           /dev/sda1                vFAT               /media/sda1       20 GB
5           /dev/sda5                vFAT               /media/sda5       30 GB
6           /dev/sda6                Ext3               /                        10GB
7           /dev/sda7                Ext3               /home                10GB
8           /dev/sda8                vFAT               /windows            7Gb(approx.)
Swap    /dev/sda9                mem swap                                1.26 GB

Now i used gparted(live cd 7.10) to first of all shrink sda5 by 5 GB.Gparted did that in around 10 mins. It then closed after succesful operation and when i started it again i could see unformatted space of 5 Gb after the windows XP partition. Now when i tried to resize the sda1(windows XP), gparted did not show any extra space which i could click and drag the partition border to make it 'expand'.in other words it showed 0 MB free space both before and after the partition.
What am i missing here?
Another query: i think if i expand the windows partition i would not be able to boot into it. what can i do to fix that?
any help greatly appreciated
regards
nanbudh

---


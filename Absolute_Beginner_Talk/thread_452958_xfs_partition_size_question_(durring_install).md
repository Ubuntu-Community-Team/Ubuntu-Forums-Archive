---
title: "xfs partition size question (durring install)"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by Whodoes on 2007-05-23
so im following the mythtv on ubuntu noob step by step guide [here]("https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop")

ive set the first two partitions with free space remaining, thusly...

/dev/sda
    /dev/sda1   ext3  /  29997mb
    /dev/sda2  swap       5996mb

freespace                  464111mb

when i use ALL the remaining free space for an XFS partion, what i get looks like this...

/dev/sda
    /dev/sda1   ext3  /              29997mb
    /dev/sda2  swap                    5996mb
    /dev/sda3   xfs     /var/lib    34611mb
   freespace                            429499mb

it REFUSES to use all the remainng freespace towards the XFS parttion. ive deleted it and tried again to no avail. on a prev install, from a few days ago, i had the same issue and once Ubuntu was up and running i seemed to be stuck with the 34gb XFS partition and none of the freespace useable....

---

### Post by jbrown96 on 2007-05-23
I'm no expert, but I would leave it as free space during install. After install, add a program called gparted (gnome partition manager), and you should be able to create the partition.

---

### Post by Whodoes on 2007-05-24
Im considering something like that. I read another post on XFS where someone was talking about "growing the partition" to a larger size. Im still not sure if the result Im getting is a mistake or not. the walkthrough doesnt give an example of how the partitions should look after the last step, it assumes all goes well and moves on to the next step...

---

### Post by Hobo Joe on 2007-05-24
Gparted is on the live CD, try using it instead of the partitioner that the installer uses.

---

### Post by jbrown96 on 2007-05-25
update. I reinstalled Ubuntu yesterday and found out that installs fail if XFS is your root filesystem (/). That could be the problem if that's what you're doing.

---


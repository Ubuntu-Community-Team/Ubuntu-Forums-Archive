---
title: "partitioning headache"
date: 2006-05-01
forum: Absolute Beginner Talk
---

### Post by Dark_Scythe7 on 2006-05-01
alright i currently have windows xp sp1 installed on my computer on a raid 0 array between two 320 gig hard drives. i split this into two major partitions and left 20 gig of free space for any linux distribution, in this case ubuntu linux (64 bit). This free space is not formatted at all keep in mind. 

During the windows installation i had to run Nvidia raid drivers so that windows would recognize that i had two hard drives on raid 0, when i try to install ubuntu linux it recognizes the hard drives, but it doesnt recognize that they are on raid 0 at all, and it doesnt recognize the 20 gig of free space i had left over, all it recognizes are the two seperate hard drives with 320 gig a piece.

is there any way to fix this? im kind of a newbie with linux.

---

### Post by catlett on 2006-05-01
[https://wiki.ubuntu.com/Installation/LVMOnRaid](https://wiki.ubuntu.com/Installation/LVMOnRaid) Hope this is relevent.

---


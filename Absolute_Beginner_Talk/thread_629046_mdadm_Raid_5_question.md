---
title: "mdadm Raid 5 question"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by SmokeMasta on 2007-12-01
hi, i've setup a raid 5 array recently in ubuntu using mdadm for a NAS. its working without any issues.
however today i noticed that one of the drives didnt do any HD activity (when looking at the leds) when writing or reading from the array.

when i did cat /proc/mdstat it showed

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sda1[0] sdd1[4](F) sdc1[2] sdb1[1]
      1465151808 blocks level 5, 64k chunk, algorithm 2 [4/3] [UUU_]
      
unused devices: <none>

```

i assume the  [UUU_] and the (F) stands for failed drive.

now is my main question is this a broken/failed drive and if so how do i do the recovery thing when i toss a new drive in there? (i got a seperate HD for booting so that isnt a issue)

and in all my newbieness can i turn off my system without data loss with that HD dead in the array ?

Thanks in advance.

---

### Post by SmokeMasta on 2007-12-02
bump

---


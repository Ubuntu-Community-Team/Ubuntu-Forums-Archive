---
title: "partitioning hd for dual boot"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by cyke on 2007-07-22
hi im new to linux and have been wanting to try it out on my laptop. i want to try ubuntu feisty and have been reading for sometime now on how to install it properly to dual boot with winxp.  i currently have 3 partitions on my HD (100GB),  primary ntfs(drive C), windows recovery, and an extended partition which is my drive D in windows.  i have resized the extended partition using gparted and successfully left an unused partition under the extended partition.  My question is when i created a new partition from the freed space and chose linux-swap, i can only choose logical partition as the type. is this correct? i did not continue coz i dont want mess my partitions. if i create the main linux partition what would be the type? should it be primary? is it possible to create a primary partition out of the freed space from the extended partition?  :confused:

---

### Post by annda on 2007-07-22
you have a limit on primary partitions - 4. both root ( / ) and swap can be logical partitions within an extended one. this is ok, you can go on.

---


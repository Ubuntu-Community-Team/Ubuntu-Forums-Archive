---
title: "Partition problems in 7.04"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by skyjacker on 2007-08-01
Please help Tried to partition my 80 GB hard drive which was all XP Home. Went thrru the Live Cd, and shrunk the XP drive to 27.95 GB which allowed me and additional 2.25 Cg in that partition. Clicked on the free space and "new", and gave the swap drive 2 GB. Everything OK so far. Then againg clicked on free space, and "new" and created a "/" partition of 8GB. Everything OK so far. Went to click on remaining free space to create/home, and the screen said that the remaining space was unusable.

Please help!!!

---

### Post by Inxsible on 2007-08-01
> **skyjacker said:**
> Please help Tried to partition my 80 GB hard drive which was all XP Home. Went thrru the Live Cd, and shrunk the XP drive to 27.95 GB which allowed me and additional 2.25 Cg in that partition. Clicked on the free space and "new", and gave the swap drive 2 GB. Everything OK so far. Then againg clicked on free space, and "new" and created a "/" partition of 8GB. Everything OK so far. Went to click on remaining free space to create/home, and the screen said that the remaining space was unusable.

Please help!!!
You can only have a max of 4 Primary Partitions. You should create an extended partition and put your /, swap and /home in it.

Read more about primary and extended partitions on this Wikipedia [page]("http://en.wikipedia.org/wiki/Partition_%28computing%29")

---

### Post by milosz.galazka on 2007-08-01
Hello,

Could you post output of fdisk command, something like *fdisk -l /dev/sda*?

You can have up to four main partitions, if you want to have more partitions then using extended partition (as one of main partitions) will allow you to create more inside it.

---

### Post by skyjacker on 2007-08-01
> **Inxsible said:**
> You can only have a max of 4 Primary Partitions. You should create an extended partition and put your /, swap and /home in it.

Read more about primary and extended partitions on this Wikipedia [page]("http://en.wikipedia.org/wiki/Partition_%28computing%29")

I do not know how to set up an extended partition.  Help appreciated

---

### Post by Inxsible on 2007-08-01
In Gparted or in the installer simply select logical partition or extended partition when you create a new partition

---


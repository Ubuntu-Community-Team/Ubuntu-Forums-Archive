---
title: "need help in creating new partition!"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by karthik_myself on 2006-09-25
hey..
i jus got rid of my windows and got an ubuntu installation....
the problem is while i ws installin ubuntu.. i let the default option of installin ubuntu by erasin my whole hard disk...
as a result i now have a single root partition of 37 gb and a swap partition of 700 mb (40 gb hard disk)....


system>administration>disks... does not give me an option of creatin a new partition with the free space remaining in my root partition...

how do i create a new partition then... ( i need to create a 30 gb fat32 partition)...???

---

### Post by anaconda on 2006-09-25
Öh.. ?
You have already partititoned your whole hard-disk.
You have 40GB hd, and it has 37GB linux-partition and 700MB swap partition, so you can't make a new 30GB fat32 partition.. or are you talking about a second hard-disk?

---

### Post by lamego on 2006-09-25
Free space inside a partition can't be used for a new partition unless you shrink it.
You will need to boot from a live CD and use the gnome partition editor to shrink your actual partition, then you can create the FAT32 part you are needing.

---

### Post by bigken on 2006-09-25
I would download [gparted]("http://gparted.sourceforge.net/livecd.php") liveCD  ;)

---

### Post by Wien_Sean on 2006-09-25
As with any file system, not all of the space can be used. I am using all 80 gb of my hard drive yet only 77 and some change shows up in the system. Also most of my extra hard drives are 40 gb and most of them only show 37gb.A certain amount of the full space is needed for files system files and whatnot. Also there is an option when making the fresh partition with the install cd of reserving a certain amount of space, usually 5%, that you won't be able to touch. Unless you want to shrink the partition to make a new one, I can't see the point in editing you part. tables.

---

### Post by CatKiller on 2006-09-25
40*1000^3/1024^3 is around 37.25. It's a widespread thing that hard drive manufacturers use base-1000 for their sizes, but computers and most people use base-1024. Hence all the 30GB and 30GiB things that people have to write for clarity.

---


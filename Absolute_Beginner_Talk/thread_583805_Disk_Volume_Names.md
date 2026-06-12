---
title: "Disk Volume Names"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by tgbrowning on 2007-10-20
I'm a bit mystifed about some of the rules governing the file system. My hardrive is partitioned as a dual boot and also contains an HP Recovery Partition as well as a FAT32 partition called "Work". 

When I originally got things set up, the different partitions showed up on the GNOME desktop as WinLin, HPRecovery and Work. All of a sudden, they went to sda1, sda2 and sda3.  

I know those are the mount points under the /media folder, but I'd like to go back to being able to refer to them with the labels I had before.

---

### Post by john.nicholls on 2007-10-20
It is possible to add labels to each partition. Open a terminal and type 
```
sudo e2label /dev/sda1 name
```, where /dev/sda1 is the name of the partition, and name is the label you want to add.

---

### Post by tgbrowning on 2007-10-21
I've got something really wrong, it appears, with my file system. Both e2label and tune2fs give me an error message saying they're getting a short read error and that there's no valid filesystem superblock.

What in blazes do I do to correct that??

Browning>>>

---

### Post by john.nicholls on 2007-10-21
I suggest you type the error message into Google and find out what other people have come up with when they had the same problem.

---


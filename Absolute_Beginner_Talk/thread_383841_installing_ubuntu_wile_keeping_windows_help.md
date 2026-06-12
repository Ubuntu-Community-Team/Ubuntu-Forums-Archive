---
title: "installing ubuntu wile keeping windows help"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by da1nonlymikeo on 2007-03-13
hey guys, i have windows xp on my laptop and i really want to put ubuntu on it and try to set up  compiz. how do i install ubuntu without erasing windows and all my work on the hard drive? im not to good with partitioning. any howto's or help would be great, thanks.

---

### Post by mikewhatever on 2007-03-13
[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)
Go over the guide, resize one of the existing partitions, create Ubuntu partitions, install, and you are done.

---

### Post by da1nonlymikeo on 2007-03-13
thanks mike, ill read it over and ill post up what happens.

---

### Post by da1nonlymikeo on 2007-03-13
i just looked at the site and when i get to the partition table i guess i have either a newer or older ubuntu cd. all the choices i have are..

1. erase entire disk.
2. use the largest continuous free space.
3 manualy edit partition table.


 i guess i have to manually do it. can someone walk me through??

---

### Post by da1nonlymikeo on 2007-03-13
can anyone help me?

 should i pick "use the largest continuous free space"? idk what to do

---

### Post by mikewhatever on 2007-03-13
The third option is the way to go. Right click on the partition you want to resize, select resize from the menu, resize to the desired size and create Ubuntu partitions in the unallocated space.

---

### Post by da1nonlymikeo on 2007-03-13
when i right click on the unlocated partition that i made, i have 

create as: Primary partition.. or extended partition?

and a lot of choices for File System:

how do i set it up if i want to dual boot windows.

---

### Post by mikewhatever on 2007-03-14
To the best of my knowledge, there should be no other options for partitions setup because a partition can be either primary or logical. You can have 4 primary partition per hdd, but creating an extended one enables to create more logical ones within the extended. You can read more about partitions here [http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
[http://www.theeldergeek.com/hard_drives_01.htm](http://www.theeldergeek.com/hard_drives_01.htm)
For Ubuntu, it does not matter whether a partition is primary or logical, so create whatever you want as long as you do not exceed the limit of four primary partitions. The guide I posted befor [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing) show how to choose the file systems for root and swap, as well as what to format and what not to. Remember, DO NOT FORMAT your Windows partition.

---


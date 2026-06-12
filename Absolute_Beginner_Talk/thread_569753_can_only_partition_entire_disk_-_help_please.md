---
title: "can only partition entire disk - help please"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by er20ic on 2007-10-07
Trying to install Ubuntu 7.04 for the first time alongside XP. Have reduced NTFS partition and left 25gb 'unallocated' (also tried it formatted as ext3) but during installation can only get guided partition option of entire disk (60gb). Have tried many times and with all the things I've read but I don't get the option with the 'freed space' on it. Haven't got the knowledge or confidence to take the 'manual' option. Please help in beginner's language. Really want to get this up and running!

---

### Post by bodhi.zazen on 2007-10-07
> **er20ic said:**
> Trying to install Ubuntu 7.04 for the first time alongside XP. Have reduced NTFS partition and left 25gb 'unallocated' (also tried it formatted as ext3) but during installation can only get guided partition option of entire disk (60gb). Have tried many times and with all the things I've read but I don't get the option with the 'freed space' on it. Haven't got the knowledge or confidence to take the 'manual' option. Please help in beginner's language. Really want to get this up and running!

You have to go the manual route ...

make a swap and root (/) partitions

Size of swap = ram X 2 up to 1 Gb, if you have a lap top and want to suspend then swap = ram

Basic partitioning: [http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

You can make a separate /home partition if you wish, make it say 15 Gb

---

### Post by petteriIII on 2007-10-07
You cannot install in an empty space when it has anything in it; it cannot even be formatted . So delete ext3 formatted partition and make install after doing so. But don't mess with Windows  - if you make harm to it it is pretty much final. Think thrice before doing anything !

---


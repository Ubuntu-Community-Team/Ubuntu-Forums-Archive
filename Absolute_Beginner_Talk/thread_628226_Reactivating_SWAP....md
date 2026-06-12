---
title: "Reactivating SWAP..."
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by Adam_clmns on 2007-12-01
I have an XP Ubuntu dual boot system, some repartitioning i did for windows deactivated my  SWAP partition, it's there, i can see it from "fdisk -l"  but i don't know how to reactivate it without reinstalling linux, which i don't want to do. i have a lot of files that won't back up (cause i have no SWAP), can i reactivate the SWAP partion from some rescue feature, or Terminal command?? 

please help, it's kinda important..

Thank You

---

### Post by Gone fishing on 2007-12-01
I think you need swapon -s to see if its working, swapon -a will activate the swap partition/s in fstab, swapon -a /dev/sda4 (or similar) will activate swap on partition /dev/sda4  swapoff -a deactivates swap

---

### Post by mcduck on 2007-12-01
Check that you still have correct UUID for the partition in /etc/fstab. (You can get a list of UUID's for your partitions by running 'blkid').

---


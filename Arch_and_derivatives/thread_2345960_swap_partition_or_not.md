---
title: "swap partition or not"
date: 2016-12-09
forum: Arch and derivatives
---

### Post by CarpCharacin on 2016-12-09
I have 64gb of ram.  Should I do a swap partition or not?

---

### Post by TheFu on 2016-12-09
Depends on the workload.  You may have the only desktop capable of running Java applications and NOT sucking all the RAM up?
For a server, I'd say probably not, if the workload is well understood.

For a desktop, I'd say 4G is still my minimal recommendation.  You'll probably never use it, but best to feel the slowdown first, before out-of-memory errors happen. I think there is little need to have more than 4G of swap on systems with more RAM ...6G, 8G, 16, 24, 32, 64G ... 4G is the swap size I'd set for a desktop.

However, if you hibernate, then you'll need 64G + 1MB of swap.

Good question, btw.

---

### Post by CarpCharacin on 2016-12-10
It is a desktop.  The SSD is 512gb.  What happens if I click hibernate and I don't have enough swap?  I don't want to do 64gb of swap space.  I like to sleep my computer, but isn't that different from hibernating?

---

### Post by TheFu on 2016-12-10
Hibernate and sleep (suspend) are different.

[https://help.ubuntu.com/stable/ubuntu-help/power-hibernate.html](https://help.ubuntu.com/stable/ubuntu-help/power-hibernate.html)
[https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)
No swap? [https://wiki.debian.org/Hibernation/Hibernate_Without_Swap_Partition](https://wiki.debian.org/Hibernation/Hibernate_Without_Swap_Partition)

I don't hibernate due to security considerations.  Only suspend when at home, never out in the world. Security considerations again.  Both of these things defeat the purpose for using disk encryption.

---

### Post by gordintoronto on 2016-12-10
I have 16 GB of memory and no swap. I use Conky to monitor several things, including memory usage. Even doing a little video editing, I've never used 50% of my memory.

---

### Post by CarpCharacin on 2016-12-11
So should I just do 4gb swap?

---

### Post by anakai on 2017-01-25
No need for swap! I have 8 gb and i have swap, but i never used it. I don't think it hurts to have it but you probably don't need it

---

### Post by Cavsfan on 2017-01-25
I have a 1MB swap partition. Just because...

I never hibernate, just suspend when needed so, no need for more.

I have Arch as my main OS but have Windows 10 for the wife and some games, plus a few other partitions; one has Xubuntu 16.04 on it.
Whenever I install an OS it auto detects the swap file and I just point the ext4 system to which ever partition I'm installing on.

---

### Post by opsusec on 2017-03-06
Of course! but just a small amount, in order for it to be beneficial that is; I'm only running 4GB ddr3 with 512mb swap at 8% cpu and 1.2G [0swap]

---


---
title: "Repartitioning after Install"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by snapcase16 on 2006-08-27
I recently installed Ubuntu 6.06 on an Intel machine running Windows XP. I installed Ubuntu in a dual-boot manner. Somehow, I managed to mix up the size of the partitions I desired. Windows XP ended up with 69 GB and Ubuntu with 36. I intend to use Ubuntu as my primary OS and I was wondering if there was any simple way to allow it more space. I've used Windows for years, but I'm not very experienced in the technical side of computing. Thanks for any possible recommendations.

---

### Post by gerbman on 2006-08-27
It would be useful to get some information about the current layout of your hard drive(s) and partitions. It sounds like you want to shrink the XP partition and expand your Ubuntu partition. What filesystems are you using for these partitions? Can you post screenshots of GParted? To install GParted, do```
sudo apt-get install gparted
```then```
sudo gparted
```to run the program.

Note:  playing with partitions is one of the riskier things you can do, so back up any critical data before even starting GParted.

---

### Post by meborc on 2006-08-27
what i would do is to minimize the windows partition... you could use gparted to make the hda1 partition (windows) smaller and create a new partition in free space... the new partition could be fat32 (since both win and linux can read/write in it) or ext3 (if you want windows to be able to read/write in it you need to install special patch-file)

be sure to defrag the win partition before so that all the data is in the beginning of the partition and to memorise the size taken by the win so you don't delete important stuff... of course make backups before starting :)

the advantage of having a third partition is that whenever you need to reformat/reinstall your OS you still have all your music and documents on the third partition... i for example always use at least 3 partitions... 1 small for win... one small for linux and then one really-big-one that both systems can read/write for my games, documents, movies etc... that way i never loose my data

btw- use wiki on partitioning and mounting the new partition :)

have fun

---

### Post by snapcase16 on 2006-08-27
Thanks for the replies and recommendations. I've installed GParted as suggested and I've included a screenshot of what the program displays when it opens. I'll have to make sure to consult wiki as well. Thanks again.

---


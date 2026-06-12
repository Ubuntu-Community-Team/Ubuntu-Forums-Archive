---
title: "Partitioning W/O data loss"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by pablo66 on 2007-05-10
Is there an ope nsource parttioning tool tool I can use to dual boot without losing my original OS (windozeXP)?

---

### Post by jkblacker on 2007-05-10
Yes the GParted software on the Ubuntu disk is what you're looking for (shuld be under System->Administration). 

To be 99% confident of no data loss, back up all your important files, then clean up (using whatever tools you normally use) and defragment your HDD several times, to push all that Windows goodness to the front of the drive. When it comes to GParted, right-click the Windows partition (almost certainly the only one showing) and make it smaller. Add ext3 partitions for Ubuntu after it, and you should be good to go. 

See this: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) for more info!

---

### Post by Martin on 2007-05-10
The Ubuntu install program has the ability to resize partitions or you can download gparted which is a collection of partition tools on a boot disk. It's about a 50mb download ifyou want to try it. Do a search on gparted to find it, I think its on sourceforge

---

### Post by indytim on 2007-05-10
It's here:

[GParted]("http://gparted.sourceforge.net/index.php")

IndyTim

---


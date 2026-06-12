---
title: "how to return to windoze only"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by Jbirdie1 on 2008-03-18
i have loaded linux 10 different times and it always makes me format my drive after i resize the drive, to return to a single windoze system. i heard that it is a fact that once linux is installed, as a dual boot with windoze, then the ONLY way to remove it is to format...that seems outrageous. i wanna try it some more but really dont want to format as punishment for not keeping it...help!!!

---

### Post by sayakb on 2008-03-18
Install Linux on a separate partition and dual boot it with Windows if you wish to (But you have to install Windows first and then Linux). Whenever you want to remove Linux, just insert your Windows CD/DVD, go to the recovery console and type these:
```
fixboot
fixmbr
```

This would overwrite the mbr and remoe grub. Your computer would directly boot to windows. From there, right click on My Computer and click Manage. There, click on Disk Management. You may delete the Linux partition and create a new one in NTFS/FAT32 fs to make it usable under Windows.

---

### Post by 3rdalbum on 2008-03-18
Why don't you use a virtualiser to try out the distributions, rather than constantly partition and repartition? VMWare Server and Virtualbox work very well.

---

### Post by sayakb on 2008-03-18
> **3rdalbum said:**
> Why don't you use a virtualiser to try out the distributions, rather than constantly partition and repartition? VMWare Server and Virtualbox work very well.

+1
Virtual machines are an excellent way to try out new OSs..
No formatting, no risk, just DELETE the machine you want to remove, and you can start over again. Plus you need not allocate huge spaces to each OS. After install XP takes 1.4GiB, Ubuntu takes 2.1GiB and FC7 takes 4.8GiB... So even if you allocate 50GiB to each, the amount you use will be the amount that is eaten up by the machine, unlike the fact that an entire 10GiB partition has to be dedicated to a distro, irrespective of how much the OS actually uses..

---


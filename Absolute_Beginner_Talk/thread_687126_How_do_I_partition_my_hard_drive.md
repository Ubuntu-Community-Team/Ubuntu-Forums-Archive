---
title: "How do I partition my hard drive"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by Djalmahal on 2008-02-04
So, 
i have Ubuntu 7.10 installed and now for my studies i have to run some windows program. I tried out virtual box, but my computer gets clumsy because of the limited memory i suppose.

Now, i will partition my 160 GB hard drive so i can have a section for windows. AM i using gparted to partition it, in which way should the new partition by formatted. i still have the Windows XP disk, how do i choose which of the two partition will get booted?

Thanks for the answers shouldn't be too difficult for you geeks

Andreas

---

### Post by mlissner on 2008-02-04
This isn't exactly a response, but you can find tons of info on dual boot windows ubuntu at google.com/linux. 

From what I understand, partitioning isn't that important...in the end, it's just allocating space. What matters is that things boot properly...after that, it's all gravy, more or less.

---

### Post by Rocket2DMn on 2008-02-04
You will need to use the [Gparted LiveCD]("http://gparted-livecd.tuxfamily.org/") to resize your root partition, create as much new free space as you think you will need for windows (50 GB maybe? only you can know).  
When you install windows it will overwrite the mbr so you won't have the option to boot linux any more, so you will have to recover GRUB by following this little tutorial - [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
You probably want to use 1.3 on that tutorial.

BEFORE you start, make sure you have backups of everything you need.  It shouldn't be a problem, but whenever you fiddle with partitions, things can go wrong and screw you over (not too likely, but still possible).

---

### Post by johnnyb1726 on 2008-02-04
This is a great guide to dual-booting.

[http://apcmag.com/node/5162/]("http://apcmag.com/node/5162/")

cheers

---


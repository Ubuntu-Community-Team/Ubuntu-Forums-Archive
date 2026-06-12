---
title: "[SOLVED] Partitioning help required"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by arpan on 2007-10-18
Hi All,

Happy Gutsy Gibbon time..!!! \\:D/

I need your help/guidance in partitioning the hard drive.

I've an 80 GB SATA drive, which already has 3 partitions of 20 GB(win), 5 GB(data), 20 GB(data) partitions.  Now I have 30 GB spare for Linux partitioning which I want to be able to use for Ubuntu + other Linux(study purpose).

So it becomes like this...
 20 + 5 + 20 + 30

I can not mess up my existing first 45 GB partition setup.

I already have win + fiesty setup, but now I want to have a win + gutsy + other distro, triple booting system.

Can someone help me on how to partition 30 GB of space for 2 Linux distros?  I want to setup the partitions in a manner that I'm able to store some personal data on a different partition other than /home and /, so if i need to have a fresh install, my data is safe and also I would like to share such a partition between 2 Linux installation, if possible. My system has 512 MB DDR of RAM.

Thanks in advance.. eagerly waiting for replies.. can't wait to install Gutsy.. =P~

---

### Post by overdrank on 2007-10-18
HI it should not be hard to do that just crate a extended partition. Because the limit to partitions is 4 to a drive unless you create a extended partition then you can create your partition with in it. Good luck!
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

### Post by arpan on 2007-10-18
Thank you.. quick and great help.

30 GBs that I wanna use is already inside an extended partition so this is how I'm gonna partition.

 / 5 GB(ubuntu) + / 5 GB(other distro) + 18 GB(data, ext3) + 2 GB(swap) = 30 GB

Let me know if you think I should lay out differently that is better than what I've thought.

Off course, I'll mark this thread solved..!!!

Once again, Thanks a lot.

---


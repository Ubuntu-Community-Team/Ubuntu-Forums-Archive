---
title: "I want to divide my hard drive, half ubuntu half osx, how?"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by ikilledclown on 2006-06-07
the title says most of it!
Basically is there a way I can divide my hard drive or something so I can have mac osx 10.4 and ubuntu running off the same machine?
I have seen it done and at the moment I have got mac os 9 running as well as osx 10.4 but I'm not sure if ubuntu is didfferent or something?


I have a apple g4, not intel based, just wondering if I can do it though really!

Cheers :mrgreen:

---

### Post by linear on 2006-06-07
Yes, you can!

First read these:

[https://wiki.ubuntu.com/Installation/PowerPC]("https://wiki.ubuntu.com/Installation/PowerPC")
[http://www.askdavetaylor.com/how_do_..._mac_os_x.html]("http://www.askdavetaylor.com/how_do_i_dual_boot_ubuntu_linux_mac_os_x.html")

This worked for me:

0. Read up in the PPC forums on any model specific quirks (the Breezy PPC forum has a lot of good material).
1. Back up OS X partition. ([Carbon Copy Cloner]("http://www.bombich.com/software/ccc.html") works well.)
2. Repartition disk. Make two partitions, leave first as free space and second for OS X. Disk Utility is destructive (another reason for the back up), or there is a howto [here]("http://ubuntuforums.org/showthread.php?t=89960") on using **parted** to resize non-destructively. Make the partition at least 5GB, but bigger is better if you really plan to use it.
2b. Restore or re-install OS X on its partition, if you used Disk Utility.
3. Boot from the Ubuntu install disk. When you get to the partitioning step, tell the installer to use the largest free space. It will take care of the rest.

---


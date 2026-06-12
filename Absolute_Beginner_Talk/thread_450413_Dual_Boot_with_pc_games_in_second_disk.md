---
title: "Dual Boot with pc games in second disk"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by Joca on 2007-05-21
Hi 

I have 2 hard disks.

In one i have 20GB space (17GB is windows and needed programs)
In other i have 30GB (15GB are windows games)

Is possible to dual boot Ubuntu/windows without destroying the 15GB of windows games in the second disk ? 

I cant pass the games to first disk, because only 3GB of space available. 

Thanks in advance
Joca

---

### Post by justleen on 2007-05-21
you can rezise the partition with Gparted, which is included on the Live-CD.
I have done so a couple of times without data loss.
Make sure you defrag your drive before doing so though.

---

### Post by stefaan.dutry on 2007-05-21
It is possible.

You need to defragment the disk and then use a program to partition your disk.  (Don't ask me for a name of a program to do it, i don't know any good free ones)  So you should look for a partitioning program first.
Be warned, i heard about programs that still damaged the data on the disk, so I hope you are lucky or have everything backed up just in case.

I also suggest only making that partition about 12GB (2GB is the minimum system requirement) this way you will easily be able to recognise the partition during the installation process too

You should now have 2 partitions on that HDD.
When installing ubuntu it should find the partitions on your HDD,  All you need to do is select the correct one (if you made it a different size it should be easy to recognise)

conclusion: start by looking for a way to make an extra partition.

I hope this helped.

---


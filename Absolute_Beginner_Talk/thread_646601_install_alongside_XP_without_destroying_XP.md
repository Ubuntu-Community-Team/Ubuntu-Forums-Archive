---
title: "install alongside XP without destroying XP"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by ubantunovice on 2007-12-21
I have XP installed on a PC with a lot of free space available to try Ubuntu 7.1 as a dual boot
The laptop (Toshiba) has a single 120GB HD partitioned as follows:
C: Windows XP system and program files (19 GB NFTS)
E: Data partition (36GB NFTS)
K: Data partition (renamed as K) (17GB NFTS)
* 40G unallocated at end of HD some of which I want to use for Ubuntu.

My concerns: 
1. I do not want to install Ubuntu and have it accidentally overwrite the existing NFTS partitions because of an error I might make being unfamiliar with the Linux naming system for partitions. I am therefore afraid to start the install procedure before knowing exactly what my options will be and how safe I will be during the install. (I already know about backups). Can someone tell me if I should create the partitions for Ubuntu ahead of time using Partition Magic (I own PM version 8 and am familiar with it).  If so what additional partitions should I create for Ubuntu and how will I recognize them in the Linux naming system during the Ubuntu install.

2. I've been told that if you install Linux as a dual boot system, Linux's grub booter will overwrite Window's own boot partition and then if you remove Linux, Windows will not boot unless you do something to restore the original windows partition.  This is scary.  Is this true?  Is there a way to avoid Ubuntu doing this? Can't it use the Windows boot partition to dual boot? If Linux does thiswhen installing a dual boot system, and I later decide to remove Ubuntu, how do I restore the Windows boot partition. (Someone mentioned something about mbr but I do not know how to go about that).

I would like to try Ubuntu but am obviously concerned it might mess up my present working system. I know I have a lot of reading to do, but I would like some clear answers to my above questions.

Thanks.

---

### Post by thelatinist on 2007-12-21
1) The Ubuntu installer will create the partitions for you.  Just make sure you don't choose the option to use the whole disk (this *will* delete your XP partition).

2) Ubuntu will overwrite your MBR with a new boot loader.  This is not a problem, GRUB has been used for years by millions of people, and is perfectly safe.  It is true that if you later want to remove Ubuntu you need to restore your MBR.  That's easily done from recovery console.  Just boot from your XP installation disk and type 'R' to enter the recovery console.  Then use:

```
fixmbr
exit
```

That's all there is to it!

---

### Post by mikewhatever on 2007-12-21
> My concerns:
1. I do not want to install Ubuntu and have it accidentally overwrite the existing NFTS partitions because of an error I might make being unfamiliar with the Linux naming system for partitions. I am therefore afraid to start the install procedure before knowing exactly what my options will be and how safe I will be during the install. (I already know about backups). Can someone tell me if I should create the partitions for Ubuntu ahead of time using Partition Magic (I own PM version 8 and am familiar with it). If so what additional partitions should I create for Ubuntu and how will I recognize them in the Linux naming system during the Ubuntu install.

2. I've been told that if you install Linux as a dual boot system, Linux's grub booter will overwrite Window's own boot partition and then if you remove Linux, Windows will not boot unless you do something to restore the original windows partition. This is scary. Is this true? Is there a way to avoid Ubuntu doing this? Can't it use the Windows boot partition to dual boot? If Linux does thiswhen installing a dual boot system, and I later decide to remove Ubuntu, how do I restore the Windows boot partition. (Someone mentioned something about mbr but I do not know how to go about that).

No you shouldn't. You can either manually create partitions during the installation or let the installer do the job, all from the CD. Use this guide [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing).

Grub is installed on Ubuntu's partition with only a very small portion going to MBR. You can backup your current MBR before installing Ubuntu, or restore it later with super grub or Windows recovery console.
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
[http://users.bigpond.net.au/hermanzone/p6.htm](http://users.bigpond.net.au/hermanzone/p6.htm)

---

### Post by Duck2006 on 2007-12-21
With the gude

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

that mikewhatever gave you, look at makeing a home partition as well.

---

### Post by dark_harmonics on 2007-12-21
I would just like to mention that if you are letting the ubuntu install resize a partition, you should backup all data first. This can potentially destroy your partition/data. I would highly recommend you run a defrag to make your data in one contiguous chunk on your disk before running the ubuntu installer. 

Hope any of this brain-dump helps.

---

### Post by ubantunovice on 2007-12-21
Thank you all for the helpful advice.

Will the Ubuntu installer allow me to choose the sizes of the new partitions it creates when I tell it to "?  I do not think it should need the entire unused 37 G of disk space.  What would be the recommended partition sizes for Ubuntu in an ideal but small trial system? (Thanks for the hint to also make a Home partition).

---

### Post by CCNA_student on 2007-12-21
You can easily tell the installer what size you want the partition to be. You said you only wanted to test Ubuntu so you should not need more that 10GB. I hope that this answers your question.

     Sin Cere,

     CCNA

---

### Post by ubantunovice on 2007-12-21
Thank you.

---

### Post by iammeagain on 2007-12-21
> **ubantunovice said:**
> 
My concerns: 
1. I do not want to install Ubuntu and have it accidentally overwrite the existing NFTS partitions because of an error I might make being unfamiliar with the Linux naming system for partitions. I am therefore afraid to start the install procedure Thanks.

There will be a visual showing of your partitions labeled with the sizes and filesystems making it real simple to recognize each partition. 
It would only be tricky if you installed through the alternate cd, my guess is your using the live cd.

---

### Post by ubantunovice on 2007-12-21
Yes I plan to use the live CD - when I get the courage to install.  Fortunately I have Acronis image backup software and, from past experience, I do know it can successfully restore a damaged system partition if necessary.

---

### Post by iammeagain on 2007-12-21
you can always test it out until then using the live cd.

 It does sometimes create problems since it runs slower and everything you install disappears after a reboot, making it hard to install correct drivers for some hardware on the live cd.

---


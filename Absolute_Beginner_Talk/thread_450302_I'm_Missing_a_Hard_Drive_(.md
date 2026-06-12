---
title: "I'm Missing a Hard Drive :("
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by e30ernest on 2007-05-21
Hello!  I seem to be missing a hard drive, or rather Ubuntu doesn't seem to see it.  I have 3 hard drives in my computer.  The BIOS screens shows all of them, and Windows can see all of them.  I seem to be missing "Drive D"

with fdisk -l I get:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5004    40194598+   7  HPFS/NTFS
/dev/sda2            9244        9729     3903795   82  Linux swap / Solaris
/dev/sda3            5005        9243    34049767+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401    7  HPFS/NTFS
```

I'm missing an 80gig SATA drive.  That's where I store all my favorite TV programs after I download them.  Many thanks for your help!

---

### Post by LaRoza on 2007-05-21
Would that be /dev/sdb1? That is a secondary hard drive and the primary partition.

---

### Post by overdrank on 2007-05-21
> **e30ernest said:**
> Hello!  I seem to be missing a hard drive, or rather Ubuntu doesn't seem to see it. *** I have 3 hard drives i***n my computer.  The BIOS screens shows all of them, and Windows can see all of them.  I seem to be missing "Drive D"

with fdisk -l I get:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5004    40194598+   7  HPFS/NTFS
/dev/sda2            9244        9729     3903795   82  Linux swap / Solaris
/dev/sda3            5005        9243    34049767+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401    7  HPFS/NTFS
```

I'm missing an 80gig SATA drive.  That's where I store all my favorite TV programs after I download them.  Many thanks for your help!

:-k

---

### Post by e30ernest on 2007-05-21
Nope sdb1 is another drive.  The drive I am missing doesn't even appear on that list so I am unable to mount it. :(

Even during the installation process, I was unable to find the drive when I was asked about my partition settings.

---

### Post by rich.bradshaw on 2007-05-21
Did you hibernate Windows? If so, it doesn't unmount the drive, so Linux can't read it.

Boot back to windows and shutdown properly, that might fix it.

---

### Post by LaRoza on 2007-05-21
In cases like this, first thing you do is check the cables. 

I noticed you had an NTFS partition, is that a Windows installation? Can you mount the drive from there?

---

### Post by overdrank on 2007-05-21
> **e30ernest said:**
> Nope sdb1 is another drive.  The drive I am missing doesn't even appear on that list so I am unable to mount it. :(

Even during the installation process, I was unable to find the drive when I was asked about my partition settings.

Hi, could you tell us which version of ubuntu you are using? I remember having trouble when I installed edgy with it finding all my drives because one was sata and the other was ide is the drive you are missing a ide?;)

---

### Post by e30ernest on 2007-05-21
Hi thanks for all of your responses.  I'll try to answer all of your questions:

rich.bradshaw: Yes I always shutdown windows when I am not using it.

LaRoza: Yes the NTFS partition is for Windows.  I can see the drive from both BIOS and Windows.  Could the cables still be a culprit?

overdrank:  I am currently using Feisty Fawn.  The drive where linux and Windows  is running is PATA (is this what you mean by IDE?), the missing drive is SATA.  

Thanks again folks!

---

### Post by LaRoza on 2007-05-21
The cables are not it.

ATA, Ultra ATA, PATA, are all IDE. IDE refers to these, I know, it's confusing.

Since you are using SATA and PATA, that could be the problem, I do not know the correct solution, but I can see how a problem would develop.

Searching the Web might give you results, I just did and found a similar problems.

---

### Post by Terl on 2007-05-21
It is the issue of the mix - there are multiple posts in this forum about issues with a mix of sata and ide drives.  I am not positive of a fix, but that seems to be the issue.

---

### Post by Inxsible on 2007-05-21
Yes your hard drive is an (H)IDE ;) (sic):o
 
 
Sorry, couldn't resist !
 
Jokes apart...Is this an internal or an external drive?

---

### Post by e30ernest on 2007-05-21
Lol!

Thanks for all your replies.  I guess I wouldn't be able to find a solution to the problem quickly.  In the meantime, I booted into Windows and transfered non-essential files to that missing drive and transferred my media files from that drive to one of the drives Ubuntu recognizes.  I know its not exactly a solution but there doesn't seem to be much choice.  ;)

---

### Post by rex_the_first on 2007-10-18
This seems similar to a problem I had
[http://ubuntuforums.org/showthread.php?t=419206](http://ubuntuforums.org/showthread.php?t=419206)
and nobody solved it.  I meant I skipped out on the whole of the Feisty. Formatted and started again with Feisty and waited for Gutsy.  It is still happening in Gutsy,  Please somebody help or tell me how to get this noticed so in 6 months I can upgrade.

Other people seem to have similar problems with no solution:

[http://ubuntuforums.org/showthread.php?t=556775](http://ubuntuforums.org/showthread.php?t=556775)

[http://ubuntuforums.org/showthread.php?t=577366](http://ubuntuforums.org/showthread.php?t=577366)

---

### Post by e30ernest on 2007-10-19
I solved the missing hard drive issue by swapping the cables it was connected to.  I hope this helps.

---

### Post by rex_the_first on 2007-10-19
Interesting, what type of hard drive was it (IDE or SATA) and which cable did you change?  I hope this is a simmilar problem to mine.

---

### Post by e30ernest on 2007-10-19
I was using a SATA drive.  I just connected the drive cable another interface connector at the motherboard.

---

### Post by rex_the_first on 2007-10-19
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94820](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94820) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Wow, I did something similar and to worked.  It seems like Ubuntu has a problem with SATA and how BIOS deals with it.  If you can add information at Launchpad it might help get this bug fixed.

---


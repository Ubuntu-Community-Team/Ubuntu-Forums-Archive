---
title: "Was going to install  6.06,got scared off"
date: 2007-03-11
forum: Apple PPC Users
---

### Post by macminiuser on 2007-03-11
Hi everyone

I was going to install Ubuntu 6.06 Lts on my mac mini (ppc only)
I got scared off by Mac OS 10.4 disk utility,because I have 37gb left of free space 
on my hard drive,so I booted off the 10.4 Mac cd opened up the disk utility,clicked on the free space,I was going to use only 15gbs of it,clicked the partition button
and it told me that if I did this I would lose all info on all 3 volumes,which would be Mac 10.4 and Fedora so I backed off.

Did I do something wrong?
I thought that you could partition on the fly with the Mac OS 10.4 partition tool and not harm the data on it.
Dang it and I wanted to put ubuntu on it!:mad: :mad: :mad: :mad:

---

### Post by calum on 2007-03-11
> **macminiuser said:**
> Hi everyone

I was going to install Ubuntu 6.06 Lts on my mac mini (ppc only)
I got scared off by Mac OS 10.4 disk utility,because I have 37gb left of free space 
on my hard drive,so I booted off the 10.4 Mac cd opened up the disk utility,clicked on the free space,I was going to use only 15gbs of it,clicked the partition button
and it told me that if I did this I would lose all info on all 3 volumes,which would be Mac 10.4 and Fedora so I backed off.

Did I do something wrong?
I thought that you could partition on the fly with the Mac OS 10.4 partition tool and not harm the data on it.
Dang it and I wanted to put ubuntu on it!:mad: :mad: :mad: :mad:

You can only resize partitions on the fly with the x86 version of OSX, IIRC.  The Ubuntu installer does have the ability to resize some partitions non-destructively, but you really ought to be backing everything up first whichever way you decide to do it anyway.

---

### Post by grazie on 2007-03-11
The ability to rework partitions from OS X is a fairly new addition (10.4.6?) and I too think it only works on Intel Macs. Personally I would prefer to use gparted on the ubuntu install cd which is an excellent tool. Folks who configure partitions themselves often forget to create an Apple bootstrap partition and/or swap partition. As you already have FC installed, these will almost certainly have been created already, but there's no harm in double checking. Anyone that plays about with partitions without having complete backups is on very thin ice.

Also, you've created two threads on the forum for same problem/query which is bad practice.

---

### Post by highlyjhi on 2007-03-11
I'm running OS X and Ubuntu 6.10 on a PowerBook G4 with the latest version of Tiger and I was able to change the partitions on the fly with Disk Utility and the Live CD. There's a guide somewhere and what you have to do is turn Journaling on or off. Do a search in the forums. I think I found the guide here.

---


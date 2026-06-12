---
title: "Automatic partition resizer not apperaring"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by Aseld on 2007-12-15
Greetings,

I'm trying to install Ubuntu on another computer, and when I get to the partition editing step the slider I'm used to doesn't appear. I'm confident to resize the Windows partition etc. manually with gparted, but I'm wondering if this may be an indicator of a more serious issue?

Running on a system with 512 meg of RAM and a 120 gig HD, all of which is at the moment taken up by Windows XP. 

Attached is a screenshot.

Thanks a lot :)

---

### Post by siciliancasanova on 2007-12-15
Just do it with the manual bubble.  You will need at least a /swap partition and a / partition

This machine that has had ubuntu for a long time on it and gone through several reinstalls used to show the slider as well but now it doesn't show it anymore when I install over the root system.  Never noticed any issues ever.

---

### Post by Aseld on 2007-12-15
Okay, thanks, I'll wait for a bit to see if anyone else says anything and then give it a go. Thanks :)

---

### Post by erfahren on 2007-12-15
I think that can happen if there are too many errors in the file system. Try running check disk 2 or 3 times and defrag it 

[JKDefrag](http://www.kessels.com/JkDefrag/) works better than the Windows one, it'll move everything to the beginning of the drive better. It's a standalone (no need to install, just put it somewhere and run it). - disable as many running processes you can when running it (antivirus, etc.) -Edit: oh yeah, and it's free of course

you *could* also try gparted (sudo gparted - while in the LiveCD) to resize the partition. I don't know about that though. Could mess up Windows if there's problems with the disk.

---

### Post by Aseld on 2007-12-15
Ah, that makes sense. Thanks, I'll run check disk and see if that works. I thought it might be something with the filesystem because gparted couldn't gauge the free space on the partition.

Thanks :)

---

### Post by siciliancasanova on 2007-12-15
> **erfahren said:**
> I think that can happen if there are too many errors in the file system. Try running check disk 2 or 3 times and defrag it 

[JKDefrag](http://www.kessels.com/JkDefrag/) works better than the Windows one, it'll move everything to the beginning of the drive better. It's a standalone (no need to install, just put it somewhere and run it). - disable as many running processes you can when running it (antivirus, etc.) -Edit: oh yeah, and it's free of course

you *could* also try gparted (sudo gparted - while in the LiveCD) to resize the partition. I don't know about that though. Could mess up Windows if there's problems with the disk.

I recommend gParted live cd also.  I've used it on NTFS partitions that had errors and it took care of and fixed the issue.

gParted live is just a good tool to have in your arsenal anyway, so whichever way you decide to go, I would still recommend burning it to a disk so you have it.

---

### Post by Aseld on 2007-12-15
> **siciliancasanova said:**
> I recommend gParted live cd also.  I've used it on NTFS partitions that had errors and it took care of and fixed the issue.

gParted live is just a good tool to have in your arsenal anyway, so whichever way you decide to go, I would still recommend burning it to a disk so you have it.

Absolutely - I actually have it in my CD case that I take everywhere - it's saved me many a time :D

---

### Post by Aseld on 2007-12-15
Wonderful! I ran check disk and now everything seems to be working. Thanks, you two.

---

### Post by siciliancasanova on 2007-12-15
And thanks for putting up a screenshot and being descriptive... it really does make a difference.

---


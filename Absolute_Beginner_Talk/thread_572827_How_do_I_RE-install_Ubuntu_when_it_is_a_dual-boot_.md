---
title: "How do I RE-install Ubuntu when it is a dual-boot with XP?"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by rayhorn13 on 2007-10-10
I am pretty new to Linux/Ubuntu.  On a scale of 1-10 with 1 being a total newbie, I am maybe a 2.5.

I have had Ubuntu successfully running & dual booting with Windows XP for a while, until I recently changed my video card (had problems) then lost internet connectivity (only on Linux - net was fine on XP) and then had problems bringing back the xserver.

***SO...  ***Instead of trying to work through all of the problems, I would rather reinstall it for a "fresh start."  It probably much easier and I know I could use the experience with the reinstall anyway.  I have found plenty on "installing" for a dual boot but have come up empty when looking for anything on "reinstalls."

I started to run the install CD and came to the repartitioning section when a few questions came to mind:

[I][B]When RE-installing Ubuntu, are there any "special" procedures I need to be concerned with?

Will the boot loader (Grub?) have any issues that I need to guard against?  Will the reinstall just overwrite what's there and still give me a clean "dual boot" configuration?

Partitioning: I just choose the same partition that I had Ubuntu installed on previously, correct?  The swap partition is still showing up so I don't need to do anything with that, right?[/B][/I]

-------------------

Any help and/or reassurance would be greatly appreciated.  The paranoia that all will be lost is keeping me from moving forward.

Thanks in advance!

:?:

---

### Post by rsambuca on 2007-10-10
Just reinstall onto the same partition and you are good to go.  Grub will re-install itself.  I would personally use the Manual Partitioning method, and then select the / and /swap as they were already setup.

---

### Post by skipbarker on 2007-10-10
> When RE-installing Ubuntu, are there any "special" procedures I need to be concerned with?
None that come to mind.

> Will the boot loader (Grub?) have any issues that I need to guard against? Will the reinstall just overwrite what's there and still give me a clean "dual boot" configuration?
You should not have any trouble with Grub.

> Partitioning: I just choose the same partition that I had Ubuntu installed on previously, correct? The swap partition is still showing up so I don't need to do anything with that, right?
If the partitioning scheme works for you then keep the old partitions.

---

### Post by notbitmonk on 2007-10-10
I did several reinstallations on dual boot and always had problems.  Main problem was that after I selected Windows to load into, I wasn't able because the NTSLDR (or something like it) was missing.  I tried several options that were posted here (I ran several threads that you can check) and ended up by reinstalling Ubuntu and XP.  Eventhough I ran into trouble, I'm using Ubuntu right now.

---

### Post by jpyanowski on 2007-10-10
I have Vista on my laptop and dual boot Ubuntu with no problem. I've reinstalled several times (due to my own experiments) #-o Ubuntu has not given me any problems.

---

### Post by rayhorn13 on 2007-10-20
***Thank you all for your replies.***  I would've replied sooner, but I didn't realize that I evidently wasn't subscribed to my own posting, so I thought there were no replies!

I'm going to go ahead and reinstall sometime this weekend (after preparing for an XP reinstall if necessary, of course) and hope for the best.  I hope I don't fall prey to the same pitfalls as you, Notbitmonk.

I will post back with my results - maybe they'll help some other poor soul like myself.

Thanks again.

](*,)

There should be a smiley that has crossed fingers.

---

### Post by ravenus on 2007-10-20
Best of luck. As others have said, I have never faced problems reinstalling ubuntu on the same partition. Important thing is to format any partition that you're installing or making swap. I have even installed different linux distros sequentially (not simultaneously) on the same partition, no problem.

---

### Post by rayhorn13 on 2007-10-20
Another positive vote of encouragement.  I hope you guys/galz are right, 'cuz I'm really not feeling like having to do the XP install, too.

---


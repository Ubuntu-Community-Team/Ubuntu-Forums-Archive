---
title: "MBP 6,2 Shutdown issues on Lucid"
date: 2010-05-18
forum: Apple Hardware Users
---

### Post by abel_bcn on 2010-05-18
Hey guys,

When I shutdown my mpb 6,2 from Ubuntu, It doesn't shutdown correctly. (Suspend and Hibernate don't work either but I'm not too worried now)

When it starts shutting down it gets to the purple screen and suddenly it halts with a 'pop' sound that's definitely not good.

When it boots again it runs fsck, clearly indicating the last shutdown wasn't ok.

Has anyone experienced a similar issue?

Thanks in advance.

---

### Post by abel_bcn on 2010-05-18
No one? It really doesn't sound to healthy for the computer nor the os... I've noticed it doesn't usually happen when rebooting, just on shutdown.

I'd appreciate any help or comments.

Thanks again.

---

### Post by linuxopjemac on 2010-05-19
maybe another forum?

---

### Post by bfroemel on 2010-05-19
> maybe another forum
which one do you propose?

> Has anyone experienced a similar issue?
My shutdowns are clean (MBP 6,2) - but I also hear the popping sound. I think the front speakers should be muted before the acpi shutdown call is issued... but because suspending is working like a charm here, I am not too irritated.

Do you use the proprietary Nvidia drivers? They solved a lot of problems (no working suspend, sudden freezes) on my setup.

---

### Post by abel_bcn on 2010-05-19
> **bfroemel said:**
> 
My shutdowns are clean (MBP 6,2) - but I also hear the popping sound. I think the front speakers should be muted before the acpi shutdown call is issued... but because suspending is working like a charm here, I am not too irritated.

Do you use the proprietary Nvidia drivers? They solved a lot of problems (no working suspend, sudden freezes) on my setup.

Hey thanks for your interest!

I do use propietary nvidia drivers, which I enabled first thing under System -> Admin -> Hardware drivers.

I however applied some power-saving settings described here, but a bit modified for my needs. I'll re-check to see if this may be causing any trouble. Could it?

[http://ubuntuforums.org/showthread.php?t=1215928](http://ubuntuforums.org/showthread.php?t=1215928)

Thanks again.

---

### Post by bfroemel on 2010-05-20
Seems to be the only difference to my setup - so one of those settings may cause the grief.

btw: I run pretty much a stock Ubuntu system (2.6.32 Kernel) and did the installation/configuration according to [https://help.ubuntu.com/community/MacBookPro6-2/Lucid](https://help.ubuntu.com/community/MacBookPro6-2/Lucid)

---


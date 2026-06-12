---
title: "How Long?"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by johnbull on 2007-09-03
I'm attempting to install as a dual-boot alongside my XP Home on a 80Gig disk. The disk is defragged and has oodles of free space (50 plus Gig).
I opted for the "Guided" partioning and it told me the new partition would use 42 Gig and could take "A LONG TIME".
Well, that was fine by me so Iturned it loose.
That was ten hours ago! The system hasn't hung-up. There is twitchy hard disk activity and I have control of the mouse pointer.
So, just how long is a "LONG TIME" ???

---

### Post by MenZa on 2007-09-03
Umm, definitely not 10 hours. I don't like the guided install myself---try the "Manual" way. If that doesn't work, try the alternate CD.

---

### Post by johnbull on 2007-09-03
Thanks for that MenZa.
However I appear to be digging my hole deeper.
Trying the Manual method you suggested, I noticed that it is calling my hard drive SCSI1 - it isn't. It's a bog standard MaxStor 80G IDE-ATA disk.

Nevertheless I tried to proceed with the repartioning but it showed every sign of heading off on another 10 hour marathon - same feeble hard disk access twinkling, same control kept on mouse pointer, so this time I didn't give it half a day.

Took out the CD and XP still boots OK. However looking at My Computer XP now bellieves that C Drive is only 40GB. (and no sign of another drive suddenly appearing) So, it seems Ubuntu re-partitioning has made a start on dividing up the drive.

I'll find out about this Alternate CD you mentioned and give it a go, but it is looking mighty like a complete F-Disk, re-load XP and start again. (Unless anyone has any ideas).

---

### Post by miggols99 on 2007-09-03
Maybe you could try using Gparted. It is included in the live cd. I think it's in System >> Administration >> Gnome partition manager

Then make an ext3 partition and a swap partition double the size of your ram. Then try the installation again. Set the ext3 partition as root / and the swap as swap.

---

### Post by johnbull on 2007-09-03
Thanks Miggols - I'll give it a go.

---

### Post by johnbull on 2007-09-03
Miggols,

Thanks for the pointer to Gparted.
I've now managed to get the partitioning sorted and a dual boot sytem up and running.
Now to start poking around and see what it is you Linux fans get so excited about.
:)

---

### Post by MenZa on 2007-09-04
> **johnbull said:**
> Miggols,

Thanks for the pointer to Gparted.
I've now managed to get the partitioning sorted and a dual boot sytem up and running.
Now to start poking around and see what it is you Linux fans get so excited about.
:)

Ahh, good, good---remember, if you need further help, the forum is always open. :)

---


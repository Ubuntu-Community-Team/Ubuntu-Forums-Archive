---
title: "Ubuntu shuts down SATA drive on reboot"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by Smirre on 2006-09-13
Not sure if this has been answered, I searched around for a thread but couldn't find anything related to it. 

Anyways... Got Ubuntu (Dapper) installed on my main rig at last, which has a SATA drive (in addition to two PATA harddrives).  Everything works peachy, but what annoys me is that when I restart the computer, Ubuntu turns my SATA harddrive off (but apparently not the PATA ones) just before reboot as I hear the drive heads park and motor spin down.  Of course, it starts back up again at the POST screen, but I find it annyoing nevertheless.  Windows XP doesn't do this though.  Is there anything I can do to avoid it?  :-k 

The drive in question is a Western Digital 250 GB SATA.  Mainboard is Asus P4P800, with the SATA controller natively integrated into the mainboard chipset. 

Thanks in advance.

---

### Post by bluntu on 2006-09-13
Same here, each time I want to use it I have to mount/enable it via SYSTEM --> Administration --> Disks.

By the way, mine is also 250gig. How come it's only 217gig when I mounted? What is eating up the 33gig?

---

### Post by Smirre on 2006-09-20
Sorry to bump, but any tips regarding my question would be appreciated. It's become a bit of a nuisance to have the drive spin down every time I reboot from Linux. Been struggling to sort it out for the past few days to no avail.

---

### Post by LarsBjerregaard on 2006-10-23
Same "problem" here. More like an annoyance actually.

I have breezy on the same machine, and it doesn't do the spinning down on reboot. Would appear at first glance to be an issue with dapper + sata.

It _is_ slightly more than an annoyance though.
1) It prolongs the reboot time
2) It wears the harddrive. Spinning up and down is, as I understand it, one of the absolute top things that wears a hard drive.

---

### Post by LarsBjerregaard on 2007-05-29
Update: Feisty fixed the problem, yay!

---


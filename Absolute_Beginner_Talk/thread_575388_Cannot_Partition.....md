---
title: "Cannot Partition...."
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by SuperHumanly on 2007-10-14
I have Windows XP installed on my laptop, and when i try to install Ubuntu 7.10 (alternate iso), i get an error message when I try to resize my hdd(SATA).

----------------------------------------------------------------------------------------------
The resize operation is impossible
Because of an unknown reason it is impossible to resize this partition.
Check /var/log/syslog or see virtual console 4 for details.
--------------------------------------------------------------------------------------------------



This problem also happens when i use the 7.04 alternate iso, and both normal iso's won't install, they freeze up on Loading.



Laptop Specs:

Windows XP MCE 2005
1GB DDR2 RAM
1.6GHz Core Duo
120GB HDD (All 120 is on C:\ Partition)

---

### Post by markusf21 on 2007-10-14
try defragging windows if it is really fragmented u cant resize

---

### Post by logos34 on 2007-10-14
This guide might help:

[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html)

---

### Post by SuperHumanly on 2007-10-14
Wow, I never knew defragmenting actually did anything :(

Doing that now, thanks.

---

### Post by bigken on 2007-10-14
you should also backup your data and if it still fails try the gparted liveCD
its in my signature

---

### Post by SuperHumanly on 2007-10-14
The gparted livecd didn't even see my hard drive (SATA), so that's not an option...

---

### Post by GutsyGibbon on 2007-10-14
Defragamantation is the most common solution for this problem. 
try performing one on your C: drive.
Good luck!

---

### Post by SuperHumanly on 2007-10-14
Alright, well can I just run the defragger once and fix it?

---

### Post by GutsyGibbon on 2007-10-14
> **SuperHumanly said:**
> Alright, well can I just run the defragger once and fix it?

Yes.

---

### Post by SuperHumanly on 2007-10-14
Good. Thanks a lot, I hope this fixes my problem

---

### Post by GutsyGibbon on 2007-10-14
> **SuperHumanly said:**
> Good. Thanks a lot, I hope this fixes my problem

Let us know if it fixed the problem when you're done. :)
if you have any other question or stuff you might wanna know you're more than invited to ask me.

Good luck,
***GutsyGibbon (Dean)***

---

### Post by SuperHumanly on 2007-10-14
I'll be sure to let you know if it fixes it. :) Thanks.

--it's 47% done defragging now.

---

### Post by SuperHumanly on 2007-10-14
That didn't work, windows defrag finished, says I do not need to defrag anymore, and I still get the error.


BTW: I have the page file & hibernation off, i read in another post that those 2 things could cause a conflict with partitioning.

Do i need to somehow run a SATA driver or something with the ubuntu installer? & I do not have a floppy disk drive.

---

### Post by SuperHumanly on 2007-10-14
Ran Windows Defrag 4 times, O&O Defrag twice, then chkdsk /f and partition magic did the partitioning just fine

PROBLEM SOLVED.

---


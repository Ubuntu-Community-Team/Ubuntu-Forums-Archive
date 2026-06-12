---
title: "resizing a raid array in ubuntu"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by bigmonmulgrew on 2007-10-27
Hi my dads computer has a raid array made of 2x WD 250GB
This is setup in the BIOS.
Windows sees this as 1 drive.

The ubuntu live CD see it as seperate drives.
Normally I would resize the partition and install linux on the new free space but I'm worried this will corrupt the array.
Will I be able to reinstall the array. What do I need to do.

I could just reinstall windows but that really seems like the long way round

---

### Post by toddward on 2007-10-27
I might be incorrect, but it sounds like ubuntu doesn't have the appropriate driver to load up in order to see the RAID array. 

Figure out your RAID card (even if it's onboard) and see if you can load the driver up before ubuntu starts it's live cd.

---


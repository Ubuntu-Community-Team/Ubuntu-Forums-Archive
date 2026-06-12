---
title: "grub error 18"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by troutski on 2006-12-03
I am trying to install a dual boot system. 2 HDD.
I can not seem to partition the primary dirve to get grub to run. I keep getting ERROR 18.
The MBR is hosed as Win XP will not load, even after trying to system repair with the XP disk

This is a dell p4 1.6 

80mb primary
40md secondary

Have searched the forums, but so far, none of the fixes works....

thanks,
M

---

### Post by sardion on 2006-12-03
How did you partiton to do the dual boot?
Did you let the ubuntu installer do it automatically?

Do you have a /boot partition separate from your / partition?

Have you tried changing the geomtry setting (do you even know what I am tlaking about here)?

What fixes did you try that didn't work?

---

### Post by Sef on 2006-12-03
GRUB error 18 from the GRUB Manual:

> 18 : Selected cylinder exceeds maximum supported by BIOS
    This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).

> 80mb primary
40md secondary


Are you talking of the hard drives?  If so, do you mean gb instead of mb?

---

### Post by troutski on 2006-12-03
Shouldn't do that so late a night...

yes 80gb
and 40gb drives

How do I get a partition for grub in front?
I'm not understanding how to do this in the manual partition screen.

thanks and sorry for the confusion.

M

---

### Post by troutski on 2006-12-03
I just blew out the whole xp install and jumped in the deep end.....:o

---

### Post by bulldog on 2006-12-03
And it works fine now?

Welcome to ubuntu.:D 

But you don't make a 'partition' for GRUB,this will be written in the MBR of your hard disk.
You only have to make a / [root] partition and a swap that's all.
You can make more partitions of course,but these two are enough to install ubuntu.

---


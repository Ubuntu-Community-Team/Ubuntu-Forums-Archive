---
title: "Stuck!"
date: 2005-09-21
forum: Absolute Beginner Talk
---

### Post by ALumsden on 2005-09-21
Hi, I am completely new to Linux and have a problem.

I have an Acer Travelmate 8104 - Pentium M 2Ghz, Intel i915PM/GM chipset, 1Gb DDR RAM, 100Gb hard drive, Ati Radeon mobility X700.  Initially 2 partitions, one with windows XP with service pack 2 (25Gb) and one partition with my data (68Gb).

I used to CD to load Linux and all seemed to go well.

Now..Grub loader loads and offers me the choice between Linux and Windows.

The Ubuntu splash screen opens and it runs through the loading process. It shows 'failed' for sync clock and control console font t_kernel font but continues.  

The screen then goes black and the system hangs?

To get out I press the power button once and the screen shows a list of the same information.  The last item it seems to be working on is 'checking battery state'.  After this the computer reboots and the whole process repeats...

What can I do??

Thanks in advance for any help!

---

### Post by towsonu2003 on 2005-11-24
try editing grub menu and append a ```
acpi=off
``` at the end of the long kernel line (follow instructions when grub comes up to edit it temporarily...

---


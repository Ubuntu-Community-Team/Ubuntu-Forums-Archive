---
title: "Ubuntu on Mac cube"
date: 2007-04-20
forum: Apple PPC Users
---

### Post by Dan194 on 2007-04-20
I have installed Ubuntu 6.06 on a mac cube g4 with a 15 inch studio cinema lcd monitor.It installed fine but on reboot the screen stays blank.It has an ATI rage 128 video card 16 meg.I can hear it booting up but can't see anything.I followed advice that was received here on the xorg.conf file but to no avail.It has done this with every version of linux I have tried.Please help this newbe because the cube just sits there unused.Thanks in advance.   Dan

---

### Post by matt_risi on 2007-04-21
Jeez, that's a cryin' shame. Why not just put Mac OS on it?

---

### Post by stmiller on 2007-04-21
Hi Dan, try the newer version of Ubuntu, Feisty. There are updated video drivers and such esp for ppc.

---

### Post by brackishboy on 2007-04-21
Try this: When the boot: prompt appears (I assume it gets that far?) type the following;

linux video=ofonly

Both my iBook and my Power Mac struggled with this problem initially, and using Open Firmware video rather than the accelerated drivers seems to sort it. If that works, there are ways you can add that option to the boot sequence.

---

### Post by LususX on 2007-05-01
> **Dan194 said:**
> I have installed Ubuntu 6.06 on a mac cube g4 with a 15 inch studio cinema lcd monitor.It installed fine but on reboot the screen stays blank.It has an ATI rage 128 video card 16 meg.I can hear it booting up but can't see anything.I followed advice that was received here on the xorg.conf file but to no avail.It has done this with every version of linux I have tried.Please help this newbe because the cube just sits there unused.Thanks in advance.   Dan


[http://ubuntuforums.org/showthread.php?t=225897](http://ubuntuforums.org/showthread.php?t=225897)

---


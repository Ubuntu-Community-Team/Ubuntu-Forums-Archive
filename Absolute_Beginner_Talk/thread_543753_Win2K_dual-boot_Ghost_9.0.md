---
title: "Win2K dual-boot Ghost 9.0"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by dizmayed on 2007-09-05
I have Win2K on one physical drive and 6.0.6 on a separate drive. The GRUB bootloader lets me pick the OS when the computer starts. All is well.

I regularly use Norton Ghost 9.0 to backup  the entire Win2K disk. *Perhaps* since the install of Ubuntu, Ghost doesn't recognize the Win2K disk&#8212;it shows with a red "X" over it or not at all. In other words, I can't backup that drive.  Norton Disk Doctor now says the "second boot sector is unwritable." Might that refer to the GRUB bootloader?

Is the install of Ubuntu related to this? Did Ubuntu install something on the Win2K physical drive? You can tell I don't understand much abt the workings of Linux but I'm learning.

THX

---

### Post by gn2 on 2007-09-05
You could do a fixmbr on the W2k drive and re-install Grub to the 6.06 drive and put the 6.06 drive first in the BIOS boot order.
.
Lots more dual-booting info in the Hermanzone link in my sig.
.

---

### Post by asmoore82 on 2007-09-05
and you could replace Ghost with Clonezilla, the Open-Source Cloning System;
which would let you easily back up your Linux setup too if you want.

[http://clonezilla.sf.net/](http://clonezilla.sf.net/)

---


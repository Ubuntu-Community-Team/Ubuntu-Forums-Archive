---
title: "boot Table become like this after updates"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by seuzo on 2007-08-09
hi, after i update my ubuntu 7.04. my boot table from this

Ubuntu, Kernel 2.6.20-15 -generic
Ubuntu, Kernel 2.6.20-15 -generic (recovery mode)
Ubuntu, memtest86+
other operating systems:
Microsoft windows xp professional

to this

Ubuntu, Kernel 2.6.20-16 -generic
Ubuntu, Kernel 2.6.20-16 -generic (recovery mode)
Ubuntu, Kernel 2.6.20-15 -generic
Ubuntu, Kernel 2.6.20-15 -generic (recovery mode)
Ubuntu, memtest86+
other operationg systems:
Microsoft windows xp professional

any way i get rid of the old one? Kernel 2.6.20-15
my Ubuntu is installed only in my second harddisk.

---

### Post by splintercellguy on 2007-08-09
You can either edit /boot/grub/menu.lst OR (the easier way) simply remove the 2.6.15 kernel using Synaptic.

---

### Post by overdrank on 2007-08-09
> **seuzo said:**
> hi, after i update my ubuntu 7.04. my boot table from this

Ubuntu, Kernel 2.6.20-15 -generic
Ubuntu, Kernel 2.6.20-15 -generic (recovery mode)
Ubuntu, memtest86+
other operating systems:
Microsoft windows xp professional

to this

Ubuntu, Kernel 2.6.20-16 -generic
Ubuntu, Kernel 2.6.20-16 -generic (recovery mode)
Ubuntu, Kernel 2.6.20-15 -generic
Ubuntu, Kernel 2.6.20-15 -generic (recovery mode)
Ubuntu, memtest86+
other operationg systems:
Microsoft windows xp professional

any way i get rid of the old one? Kernel 2.6.20-15
my Ubuntu is installed only in my second harddisk.
Hi and yes after the updates you have the new kernels. You can comment them out of your grub but I would at least leave them in case the updates don't play well with your system you can boot into them and save any and all data you need. Good luck!

---

### Post by seuzo on 2007-08-09
> **splintercellguy said:**
> You can either edit /boot/grub/menu.lst OR (the easier way) simply remove the 2.6.15 kernel using Synaptic.

Synaptic is under application?

---

### Post by splintercellguy on 2007-08-09
System -> Administration -> Synaptic.

---

### Post by seuzo on 2007-08-09
cool thanx.

---

### Post by seuzo on 2007-08-19
sorry what name of the kernel to remove? i can't find in synaptic.

---

### Post by mcduck on 2007-08-19
> **seuzo said:**
> sorry what name of the kernel to remove? i can't find in synaptic.

search for "kernel image", "kernel headers" and "restricted modules".

---

### Post by Raptor45 on 2007-08-19
Search for 2.6.20-15 in synaptic, and remove.

Its not necessary to get rid of old kernels, so you may be better off just leaving it.

---

### Post by seuzo on 2007-08-19
ok thanx for the help

---


---
title: "[SOLVED] oem partition deleted, new installation needed ?"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by neoragexxx on 2008-03-08
hi people i would really  appreciate any help . i deleted one of the oem partitions i had which i thought were useless. my root partition of ubuntu remains intact but i can't access it. i get error 17 on grub. 

grub works fine and i access my windows os through grub and i can read my main linux drive with linux reader from windows . 

is there any chance i can access ubuntu without a fresh install ?

---

### Post by Hendrixski on 2008-03-08
Are you trying to access the partition that you deleted with GRUB?  I mean, the only partition you need to boot Linux is the "/" partition.  If Grub is not pointing to it.. that could be the problem, grub may be pointing to the wrong partition.

This is an oem partition that came with Ubuntu? Or was it like the OEM "backup" partition that comes with Windows, like how Dell just installs 2 copies of Windows so that you can re-install it every 6 months without needing the install disk just copy the partition.

You rarely need to re-install Linux, it's hard to hose it beyond repair.  However , sometimes re-installing is just plane easier.

---

### Post by logos34 on 2008-03-08
You could try pressing 'e' on the ubuntu kernel in the grub menu screen, then 'e' again on the 'root' line and change it--i.e. try (hd0,2) or (hd0,1), (hd0,3) etc.

---

### Post by neoragexxx on 2008-03-09
thanks logos34 i'll try that. i think i changed the sequence of the partitions and that's why it's not finiding it.

---

### Post by ByteJuggler on 2008-03-09
Also download the ["SuperGRUB" boot CD]("http://supergrub.forjamari.linex.org/"), which is pretty good at getting existing installations booting.  That would help you boot/fix your setup I think.

---

### Post by neoragexxx on 2008-03-09
i already have supergrub boot cd ! 

logos34 solution worked perfectly ;) thanks a ton man !

---


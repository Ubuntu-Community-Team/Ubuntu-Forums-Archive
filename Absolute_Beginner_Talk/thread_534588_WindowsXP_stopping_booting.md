---
title: "WindowsXP stopping booting"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by Diamyst on 2007-08-25
After installing a dual boot on a Desktop system, Feisty Fawn dual boot with XP, both systems booted beautifully.  After installing Java and updating several programs, windows would no longer boot.  It says unmountable boot volume.   Now it booted into windows many times before it decided not too anymore.   During the Ubuntu install we let it parition itself automatically.  It has a 160 gig hard drive.

Computer is a Compac Presario SR1520NX   AMD Semperon 3500+, 1.4 gig of ram and 1.2 ghz.  160 meg hard drive.

I think my daughter would bypass windows altogether if Ubuntu ran the online games faster.  WOuld they run faster if windows wasn't installed as well.  She plays on Pogo Games.

Thanks

---

### Post by meindian523 on 2007-08-25
Just check whether Java or the other updates altered Grub or the partition table in any way.

---

### Post by jnorthr on 2007-08-25
No the games would not run any faster than the hardware permits. The video drivers for your particular machine may have an effect on how they perform, but keeping windows in a spare partition is just that - spare. If it's not in use it's not costing you anything but disk space.

---

### Post by gensdazz on 2007-08-28
> **meindian523 said:**
> Just check whether Java or the other updates altered Grub or the partition table in any way.

How do i check and see if it  altered it ? and how do i fix it?

---

### Post by meindian523 on 2007-08-28
In terminal

```
fdisk -l
```
This will give you your partition table.Just see whether you remember whether the partition numbers are different........

---


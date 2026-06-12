---
title: "mystery partition on eeepc"
date: 2011-08-27
forum: Asus Ubuntu Support (CLOSED)
---

### Post by pratikk on 2011-08-27
Hi, I run 10.04 on a 1005HA eeepc. Gparted reports a partition of size 47.07 Mb and unknown filesystem. It's not the PE partition for reinstalling the Windows the machine shipped with. Does anyone know what this tiny partition is for? Specifically, is it OK to resize and format it to swap?

Thanks

Pratik

---

### Post by Linuxisfast on 2011-09-01
Its most likely for the minimal ASUS OS that you access during boot process, it lets you surf without going into Windows, you can safely delete that partition, I have done so without any ill effects.

---

### Post by pratikk on 2011-09-04
Thanks for the reply, but this machine predates the browse before boot feature. But it may have something to do with boot. I'm a bit wary about deleting it without knowing precisely what it does, for fear of crippling the Win partition. This is a dual boot and both OSes are in use.

---

### Post by Linuxisfast on 2011-09-06
If you are retaining Windows, I would keep that partition as well.

---

### Post by pratikk on 2011-09-08
Yeah, guess that's safer. Pity, I was hoping to create a swap. I hit the four partitions limit on this machine and couldn't create a swap, and a neat trick I'd heard of, by which partitions are created within an extended partition, did not work.

Thanks for your advice, I'll play safe.

---


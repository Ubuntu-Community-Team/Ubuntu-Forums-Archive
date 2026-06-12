---
title: "Boot question"
date: 2005-06-23
forum: Absolute Beginner Talk
---

### Post by jsimmons on 2005-06-23
I don't want to repartition my windows boot drive because there's simply too many opportunities to screw the pooch and the last thing I want to have to do is re-install Windows.

I have room for another SATA drive, and I was wondering  - If I put in a new 160gb SATA drive and put Linux on that drive, would it boot in a dual-boot environment?

(And yes, it's worth $100 to me to buy a 160gb drive just for Linux if it means I won't be taking a chance on ruining my Windows boot partition.)

---

### Post by Dragonfly_X on 2005-06-23
You can't install it on the same partition as windows, create a new partition or (I personally recommend this) just add a HD and install Linux on it keeping windows on the other. The boot loader "GRUB" will detect windows and at start-up it will present you with a menu with all OS's on the system, choose one and it boots that OS

---

### Post by jsimmons on 2005-06-23
[QUOTE=Dragonfly_X]You can't install it on the same partition as windows, create a new partition or (I personally recommend this) just add a HD and install Linux on it keeping windows on the other. The boot loader "GRUB" will detect windows and at start-up it will present you with a menu with all OS's on the system, choose one and it boots that OS[/QUOTE]
 I think you mis-understood.  I don't want to mess with my windows boot partition *at all*.  I want to know if I can put Linux on a completely different drive and still be able to dual boot.  Specifically, can I use a SATA drive (I seem to remember there being a question about SATA drives, but for the life of me, I can't find the darn thread)?  I don't see any reason why not, but I thought I'd ask before I bought the drive.

---

### Post by Alexander Kirillov on 2005-06-23
[QUOTE=jsimmons]I I want to know if I can put Linux on a completely different drive and still be able to dual boot. 
[/QUOTE]
Definitely yes. However, GRUB will be installed in master boot record (MBR) of the first HD. Shouldn't be a problem - and your windows partition will be untouched
> 
 Specifically, can I use a SATA drive (I seem to remember there being a question about SATA drives, but for the life of me, I can't find the darn thread)?  I don't see any reason why not, but I thought I'd ask before I bought the drive.
In theory, SATA drives should work fine under Ubuntu.

---

### Post by jsimmons on 2005-06-23
[QUOTE=Alexander Kirillov]Definitely yes. However, GRUB will be installed in master boot record (MBR) of the first HD. Shouldn't be a problem - and your windows partition will be untouched

In theory, SATA drives should work fine under Ubuntu.[/QUOTE]
 Perfect. :)

---


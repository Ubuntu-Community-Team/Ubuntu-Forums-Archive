---
title: "Grub error 21"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by Raincaller on 2007-07-30
Hello all. 

First disc specs: 

2 x 150GB WD Raptors in RAID 0
2 x  250GB Seagate HD as separate disks

Situation:

I have installed Ubuntu 7.04 FF on one of the Seagate 250 disks, using "Use entire disk" installation method. 

I have Vista Ultimate 32 bit on the RAID 0 disks. 

Result of the installation is Grub error 21. 

I tried swapping boot order of drives, etc, in BIOS  but nothing seems to work 

Any insights ?

Thanks in advance

---

### Post by ZX3Junglist on 2007-07-30
I just tried running grub in conjunction with a RAID setup earlier, and didn't have much luck.
While I'm no expert, I know that error 21 is "disk not found" probably relating to "i'm not seeing the windows partition you want me to boot from"

try posting the contents of /etc/fstab, /boot/grub/menu.lst and /boot/grub/default.map

someone can better help you then i think

---

### Post by Raincaller on 2007-07-30
Thanks ZX3,

Anyway I tried installing again, and noticed that there is ADVANCED button available just before entering the actual installation. When I clicked it, it asked where to install the boot loader, its default was HD0 or something. I didnt do anything with it, but should I ?

ps Using Ubuntu 7.04 FF

---


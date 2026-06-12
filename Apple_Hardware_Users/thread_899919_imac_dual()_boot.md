---
title: "imac dual(?) boot"
date: 2008-08-24
forum: Apple Hardware Users
---

### Post by Intuvati on 2008-08-24
this is all hypothetical. lets say i have a new intel imac (dual core 3ghz, nvidia 8800, 4 gigs ram, etc etc). after purchasing my new apple computer, lets say i decided to use bootcamp to install windows (probably vista). so, now i would have mac os x and vista smoothly dual booting. now, lets say i went crazy and decided to add yet another OS (fancy that) and it j ust so happened to be linux. i'm aware of rather sticky methods to obtain a triple boot using rEFIt and lilo/grub etc, but thay're pretty complicated with a high risk of error. my question is; would installing linux after all of the drama of bootcamp be catastrophic, and is it even possible?? i've heard that mac computers dont even have a real bios but use bios emulation (something along those lines) along with the use of efi before mbr, etc. I would not (sadly) be using linux as my *main* OS but i cannot live in this world without my linux fix every now and then. I would mostly use OS X for every day things and only use windows for casual gaming. but it not like i'm abandoning linux altogether, after all, i'm still using unix :P . *if* i am shooting for the moon, i dont have a *huge* problem with running linux under vmbox but...
     any ideas?

---

### Post by cyberdork33 on 2008-08-24
refit is not at all risky, it is just a menu interface for the EFI bootloader.

You have to use grub/lilo to load the linux kernel. every machine requires that (including non-macs as well).

Windows tends to get very upset if you change the partitioning of the disk after it has already been installed. You would likely have to reinstall again after partitioning to make space for Ubuntu.

Using a VM is a great option, but you do lose some functionality such as 3D graphics.

---

### Post by Intuvati on 2008-08-24
thanks

---


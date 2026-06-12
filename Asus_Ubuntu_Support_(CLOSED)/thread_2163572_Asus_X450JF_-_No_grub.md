---
title: "Asus X450JF - No grub"
date: 2013-07-18
forum: Asus Ubuntu Support (CLOSED)
---

### Post by dudumomo on 2013-07-18
Hi there,

I've been trying to install Ubunru on my new laptop, an Asus X450JF.
The installation is working well, but when I restart the computer, it directly boot on Windows 8.
There isn't any grub.

I believe it is coming from the UEFI...and something needs to be done haha.... But don't know what?

How does it work?

Thanks for your help !

---

### Post by dudumomo on 2013-07-18
Okay Solved ! Nice !

I had to disable CSM and Fastboot + boot on the USB key as UEFI in the BIOS.
During installation, I have to make sure the EFI partition is recognized and assigned /boot/efi as mounting point.

Now it works !

Thanks

---


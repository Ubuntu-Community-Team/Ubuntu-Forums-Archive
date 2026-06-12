---
title: "EFI 64bit, Grub, and Nvidia w/ elio questions"
date: 2009-06-28
forum: Apple Hardware Users
---

### Post by dman777 on 2009-06-28
I am prepareing for a new 13" Macbook Pro. I have a couple of questions:

is the EFI 64 bit? If so, do I have to use a 64 bit Grub? And can I use Grub 1 or do I have to use Grub 2? And I read where only elio will recoginize Nvidia driver, is this true?

---

### Post by pxwpxw on 2009-06-28
> **dman777 said:**
> I am prepareing for a new 13" Macbook Pro. I have a couple of questions:

is the EFI 64 bit? If so, do I have to use a 64 bit Grub? And can I use Grub 1 or do I have to use Grub 2? And I read where only elio will recoginize Nvidia driver, is this true?
 
EDIT: 

You can use grub2 grub-pc or grub1, both booting with pc-bios, no efi problems with video, they dont use efi. There may be some other MBP issues (theads on mbp5).

If you wanted to use efi booting - 

MBP will be 64 bit efi. You need Grub2 grub-efi and grub-common 64 bit package. Ubuntu Karmic one or debian sid versions from june 2009, not the earlier versions march 2009 or 2008. There is a 64 bit package built on the grub-efi thread, my post #772. See post #1 for other info.

Elilo won't run on Apple efi last time I tried it, so if it does support nvidia 3d its only on IA32/64 CPU on pc machines, maybe others but not Apples, nobody seems to have done any special hacks for elilo on Apple efi.

I think the following applies generally to intel, ati radeon, and nvidia graphics on Apple intel efi across the various mac models, but also depending on the linux kernel version.

grub.efi supports xorg Driver fbdev (no 3d agp ) on all Apple Intel Macs, any graphic chips.

grub.efi booting will not support driver Nvidia on MBP41.

grub.efi will support ATI Catalyst fglrx 3d accel driver on iMac81 for Intrepid 810, and debian 500 (2.6.26 kernels) but not for Jaunty 904, have not tried for Karmic 2.6.30 kernels, probably no go.

Dont know for debian 2.6.29 kernels, possibly

grub.efi will support agp on intel chips, with intel driver, as in earlier MacBooks, but  only ubuntu810, not later, for MacBook21,

EDIT - grub2 can be grub-pc or grub-efi or even grub-ieee1275

---

### Post by dman777 on 2009-06-28
Can I use GRub(1 or 2) instead of EFI for booting? In that case can it be 32 bit grub?

---

### Post by pxwpxw on 2009-06-28
> **dman777 said:**
> Can I use GRub(1 or 2) instead of EFI for booting? 

Yes, but I dont know if there may be a booting problem with the latest MBP. For MBP41 or earlier there is no problem. 

> 
In that case can it be 32 bit grub?


A ubuntu or debian i386 or amd64 install will autmatically select the 32 or 64 bit grub or grub-pc package install it in the linux system and install the bootloader on the hard disk where it works with the Apple pc-bios emulation, not with the EFI.

The standard installer bootloader package is currently grub or grub-pc, but not grub-efi.

However the grub-efi package is also separately downloadable and usable and has to match the Mac EFI.

---

### Post by dman777 on 2009-06-28
I was going to do a triple boot with OSx, Windows Xp, and Linux. Isn't the EFI the firmware? What file is the Apple PC bios emulation called and where is it stored at?

---

### Post by pxwpxw on 2009-06-29
You need to get the Mac and try it yourself to answer those detailed questiosns.;)

---


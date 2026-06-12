---
title: "Win7 - Win8 - Ubuntu - Triple boot on UEFI (GPT partition)"
date: 2012-11-21
forum: Any Other OS
---

### Post by aigljd on 2012-11-21
Hi everyone,

I recently bought an asus X401A and I'm trying to do a triple boot win7/win8/ubuntu 12.10

I can't figure out how to boot my win8 usb key using UEFI (i/o classic BIOS) ?
Because my partition table is GPT (i/o MBR) I can only install win8 by this method.

I formatted my USB key in FAT32 and followed diverse tutorials that are using copy/paste methods but my computer doesn't seem to boot my USB key in UEFI and I can only use the BIOS method that get my stuck in the install.

Does anyone know how to do this ?

Thanks a lot !

PS : the UEFI settings are configured in my BIOS.

---

### Post by oldfred on 2012-11-21
If using gpt and UEFI, all other systems must be booted in UEFI mode. And you have to boot installer or repair disks in UEFI mode to have them work.

       Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

Someone with Asus just had to turn off secure boot to get it to boot anything after Ubuntu was installed over Windows. But install with secure boot did work.
With Ubuntu you have to use 64 bit version and boot in UEFI mode.

 [https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

---

### Post by aigljd on 2012-11-22
I don't have a secure boot option in my BIOS, my USB key is formatted in FAT32 but it won't boot into UEFI, I don't know why?

---

### Post by oldfred on 2012-11-22
Which system will not boot, Windows or Ubuntu? I think both have to be the 64 bit version to offer the UEFI boot option.

---

### Post by aigljd on 2012-11-23
Every OS is booting fine, Win7 x64 and Ubuntu 12.10 x64 that are both installed over UEFI.

But my USB key doesn't boot in UEFI for win8 installation, only Legacy seems to work but doesn't allow me to install it on GPT partitions.

Any ideas ?

---

### Post by oldfred on 2012-11-23
Moved to OtherOS since Windows 8 issue.

Do you have a good copy, not sure how you verify Windows.

May be better on a Windows forum?

---


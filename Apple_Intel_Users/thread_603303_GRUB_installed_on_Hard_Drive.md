---
title: "GRUB installed on Hard Drive"
date: 2007-11-05
forum: Apple Intel Users
---

### Post by Xranger60 on 2007-11-05
Ok, so for some background... I originally installed Windows XP via bootcamp, and had a simple bootcamp Mac OS/Win. Setup.  I then made another partition for Linux, and installed Ubuntu to it.  However, during the installation process, I forgot to specify to install GRUB to the linux partition (Doh!).  Mac OS and Ubuntu load fine, but Windows will not boot.  

I am not concerned about Windows, I plan on running "fixmbr" to remove grub from that partition.  However, since grub was installed on my entire mac hard drive, I would like to know how to remove it from my mac boot partition.  I feel a little iffy about having GRUB in the MBR even tho it's not doing anything detrimental.  Any suggestions?

---

### Post by cyberdork33 on 2007-11-05
> **Xranger60 said:**
> Ok, so for some background... I originally installed Windows XP via bootcamp, and had a simple bootcamp Mac OS/Win. Setup.  I then made another partition for Linux, and installed Ubuntu to it.  However, during the installation process, I forgot to specify to install GRUB to the linux partition (Doh!).  Mac OS and Ubuntu load fine, but Windows will not boot.  

I am not concerned about Windows, I plan on running "fixmbr" to remove grub from that partition.  However, since grub was installed on my entire mac hard drive, I would like to know how to remove it from my mac boot partition.  I feel a little iffy about having GRUB in the MBR even tho it's not doing anything detrimental.  Any suggestions?
fixmbr will replace grub with the windows bootloader. First, you should install grub manually to your Ubuntu partition.
[http://www.rickycampbell.com/2007/10/31/booting-windows-linux-and-osx-on-your-mac-without-using-grublilo-to-boot-windows/](http://www.rickycampbell.com/2007/10/31/booting-windows-linux-and-osx-on-your-mac-without-using-grublilo-to-boot-windows/)

---


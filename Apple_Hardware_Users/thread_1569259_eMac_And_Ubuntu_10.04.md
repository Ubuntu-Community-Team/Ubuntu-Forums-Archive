---
title: "eMac And Ubuntu 10.04"
date: 2010-09-06
forum: Apple Hardware Users
---

### Post by skfunnyboy on 2010-09-06
Hi, i have a eMac G4 ( 800MHz, 256MB RAM ) and i try to install Ubuntu 10.04 on it
So i downloaded the iso from : [http://cdimage.ubuntu.com/ports/releases/10.04/release/](http://cdimage.ubuntu.com/ports/releases/10.04/release/)
The name of the iso is : ubuntu-10.04-desktop-powerpc.iso So yes its the PPC version...
Si i burned the image on MagicISO, the mac detect the cD on Mac OS X 10.4 but when i reboot and i hold the c key, nothing happen.
I tried with Poweriso too, but the cd dosen't work, the OS X dosent detect it.
I re-downloaded the iso on the eMac and burned it with Disk Utility but the cd do the same thing as the MagicISO CD...
When i try to boot with the C key i got a gray screen, no apple logo, no Yaboot command prompt...
I tried the cd on my iBook and its work so i think its the eMac...


Thanks.

---

### Post by linuxopjemac on 2010-09-06
Probably the CD was not written correctly.
I would go for an alternate installation though, or netboot:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by skfunnyboy on 2010-09-06
EDIT : its work,i had to wait for like 4 minutes...
Thanks for your help

EDIT (X2) i finally got the yaboot command prompt, i pressed enter and now i got a black screen...only a black screen.....
Should i wait or i close the mac?

---

### Post by linuxopjemac on 2010-09-07
do an alternate installation without GUI or a netboot (also without GUI).

---

### Post by skfunnyboy on 2010-09-10
> **linuxopjemac said:**
> do an alternate installation without GUI or a netboot (also without GUI).

The alternative one?

---

### Post by linuxopjemac on 2010-09-11
[http://cdimage.ubuntu.com/ports/releases/lucid/release/ubuntu-10.04-alternate-powerpc.iso](http://cdimage.ubuntu.com/ports/releases/lucid/release/ubuntu-10.04-alternate-powerpc.iso)

---

### Post by kjkrum on 2011-04-13
I think the published .iso may be corrupt.  I downloaded two images today: xubuntu 10.10 for AMD64 and ubuntu 10.04 for PowerPC.  Both md5s check good.  OSX happily mounts the 10.10 image, but it will not recognize the 10.04 image as a valid filesystem.

---

### Post by linuxopjemac on 2011-04-14
Try to boot the damned iso from open firmware:
[http://mac.linux.be/content/booting-open-firmware](http://mac.linux.be/content/booting-open-firmware)

---

### Post by B_Free on 2011-04-15
The people who are really knowledgeable about Linux tend to forget how easy it is to install a MAC OS, and how different and difficult the installation of Linux.
The AMD 64 is for Intel. You can throw that out. The 10.04 iso will not recognize your hard drive to partition, so download the 8.04 release, install it, and upgrade to 10.04 online. That is what I had to do. It takes about 4 hours to do that. Download from the site you got the 10.04 iso.

---


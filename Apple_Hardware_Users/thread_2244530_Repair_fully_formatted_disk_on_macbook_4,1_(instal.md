---
title: "Repair fully formatted disk on macbook 4,1 (install ubuntu on it)"
date: 2014-09-17
forum: Apple Hardware Users
---

### Post by Forux on 2014-09-17
Hello,


I have macbook 4,1 without efi partition on the head of disk (200Mb).


There are:
1. Any way to make ubuntu bootable on it without stock efi?
2. Any way to restore efi, or make it bootable in any other way?


Many thanks for any help!


P.S. What already done, and dont help:
1. I tried to restore disk with gpart, using gparted (it found nothing)
2. I tried to make apple rescue disk from os x 10.8.3, on running vmware - got this logo on boot: [http://www.pcfriends.jp/img/support_mac79.jpg](http://www.pcfriends.jp/img/support_mac79.jpg)
3. I tried to boot from bootable OS X 10.7 disk, also got [http://www.pcfriends.jp/img/support_mac79.jpg](http://www.pcfriends.jp/img/support_mac79.jpg)
4. Tried to install ubuntu on whole disk, got error "grub can not be installed"

---

### Post by este.el.paz on 2014-09-18
@forux:

What happened to the efi partition?  Seems like that would be a "minimum requirement" for booting an apple . . . but these "bootable systems" are any of these OSX install disks?  Or just a clone of an already installed system?  I think you would need to get the efi partition installed . . . even if you try rEFInd I think you need the EFI installed . . . .  You possibly could try the "tonymacx86" site and see if they have something that will let you turn an apple into a system that can run linux . . . .  

Have you tried to boot a "live DVD" of Ubuntu?  But, probably you need an OSX install disk . . . although that might not  be "boot-able" either w/o the EFI, so some other computer repair  disk???   Or prof'l repair shop to re-install the EFI?  Maybe someone else will stop by and comment . . . .

e.e.p.

---

### Post by Forux on 2014-09-19
I can boot via ubuntu usb-stick. Apple rescue disks and bootable and install disks show that: [http://www.pcfriends.jp/img/support_mac79.jpg](http://www.pcfriends.jp/img/support_mac79.jpg)

Will search tonymacx86, if something will help - i will say here.

---

### Post by este.el.paz on 2014-09-19
> **Forux said:**
> Hello,

1. I tried to restore disk with gpart, using gparted (it found nothing)
2. I tried to make apple rescue disk from os x 10.8.3, on running vmware - got this logo on boot: [http://www.pcfriends.jp/img/support_mac79.jpg](http://www.pcfriends.jp/img/support_mac79.jpg)
3. I tried to boot from bootable OS X 10.7 disk, also got [http://www.pcfriends.jp/img/support_mac79.jpg](http://www.pcfriends.jp/img/support_mac79.jpg)
4. Tried to install ubuntu on whole disk, got error "grub can not be installed"

@forux:

Reading your subject line again for the first time, it says, "fully formatted disk" . . . is this format "FAT32" or "Journaled(extended)??  If it's formatted to FAT32, indeed OSX will not recognize it . . . if journaled(extended) then linux won't recognize it as "available."

If you can boot the ubuntu usb stick . . . did you try to install "automatic" or did your do "manual" . . . sometimes depending on which ubuntu version, the installer doesn't create a small (10MB or so) partition for GRUB.  Using GParted in the "choose other option > manual" . . . you have to create the 3 partitions, one small one for GRUB, flagged "bios_grub" . . . home/root flagged "/" and RAM amount as "swap" and then run the install and see if it works.

The general wisdom is to have an OSX partition on the computer for firmware stuff, OSX should be installed first, then you could add rEFInd . . . and that might make the difference in the deal . . . .  But, there is now a "mac" friendly distro available . . . which also might be worth trying.  Still think for the base operation of the computer the EFI partition should be there . . . .  But try to run the install from the usb stick and see what happens . . . .

e.e.p.

---


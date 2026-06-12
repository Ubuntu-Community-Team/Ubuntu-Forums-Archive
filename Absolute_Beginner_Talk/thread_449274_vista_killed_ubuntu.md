---
title: "vista killed ubuntu"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by hpurvis on 2007-05-20
I have ubuntu 606 on my computer but after I nstalled vista it changed the boot sectors and I cant get to ubuntu, is there any way to fix this or do I have to install ubuntu again!

---

### Post by the.dark.lord on 2007-05-20
Did you wipe out the HD while installing Vista?

---

### Post by Famicommie on 2007-05-20
Windows overwrites the MBR which subsequently deletes grub. Pull out your Dapper liveCD and follow these instructions:

[http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+GRUb](http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+GRUb)

---

### Post by ugm6hr on 2007-05-20
Haven't tried it myself. but EasyBCD (or perhaps VistaBootPro) runs in Vista, and should allow you to use the Vista Bootloader to find Ubuntu again.  It should be pretty good for what you need.  Probably easier than reinstalling GRUB, largely because it uses the Vista GUI to edit the bootloader.

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by Computer Guru on 2007-05-21
With EasyBCD, if you don't want to re-install GRUB you shoud use the "NeoGrub" module.

However, if you plan on using the normal (and recommended) Linux boot system, you'll have to install GRUB to the bootsector of the Ubuntu partition. Detailed instructions: [http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

VistaBootPRO author's stole code from the EasyBCD project and publicly admitted to the reverse engineering of EasyBCD. Don't support anyone that steals from from freeware projects!

---


---
title: "Second hard drive install"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by natman on 2008-04-08
I have a PC with a HDD hooked up and i just installed a second one ( i had the jumper to cabel select, and have the second HDD hooked up via a SATA cabel )
When i tried the install cd i get two options sda (first HDD ) and sdb (second HDD ) my question is if i install on sdb how will i boot from the second hard disk there is only 3 options in the boot menu (HDD1, CD, Floppy )

---

### Post by red_Marvin on 2008-04-08
When you install ubuntu, a program called GRUB is installed on the master boot record on the first hard drive (IIRC).
When the compter boots, it starts and brings up a list of the operating systems that was detected when installing, so you can choose which one you want to boot.

---


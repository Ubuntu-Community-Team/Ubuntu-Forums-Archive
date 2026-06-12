---
title: "Grub Loader errors"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by frog3764 on 2007-08-07
Greetings to the Group - My system is AMD 2400 512 RAM 80 GB HD and 320 GB slave HD GeForce FX5200 128 MB Ubuntu Feisty and XP Pro.  The other day the system was on all day as usual but no one using it.  Something happend as the Logitech wireless mouse wouldn't work to shut down, so I hit the button to shut down.  The next day XP wouldn't load but Ubuntu did.  When I rebooted to get XP it would just keep in a loop mode going through the boot selection screen and keep looping.  I had to get my PC Doctor floppy and and try to get XP back, but couldn't.  So I "messed" with Fdisk, format, and "install a new system" and I started getting Grub Loading, then Error 22 or 17.  I can't load Windows at all even though the C Drive seems OK as I've run Scandisk and formatted.  So, is Grub for Linux and XP or just linux?  Something happend when I took out the Linux partitions I think.  I sure need some help here and appreciate all I can get.

Frog

---

### Post by aquavitae on 2007-08-07
Not sure if I've understood you right, but this may help:  Grub will load any system (linux, windows, osx, whatever) but to do so reads setup files from your linux partition.  If you've removed the linux partition then you've basically removed grub too.  Well, except for the small part of grub which lives in your hard drives MBR (a few bytes at the start of the drive).  The way it works is your pc goes to the mbr for boot instructions, and finds grub stage 1.  This points the pc to the linux partition for further isntructions.  To fix it, you'll need to reinstall linux, or if you don't want linux any more you've have to replace it with the windows boot loader.  Either way, super grub disk should help.  Do a google "super grub disk" to find it, it will pop up quickly.

---

### Post by frog3764 on 2007-08-07
Hey thanks aquavitae - That sounds like it.  I tried to re-install Ubuntu but it came up with the Grub error 17.  The other errors were 22.  I would like to get the Ubuntu in then go for Windows install, which I think will take out Ubuntu anyway, then re-install Ubuntu.

Frog

---

### Post by nitro_n2o on 2007-08-07
reinstalling grub will fix it 
search the forum for "reinstalling grub" using the google search and get the first page

---

### Post by aquavitae on 2007-08-07
> **frog3764 said:**
> I would like to get the Ubuntu in then go for Windows install, which I think will take out Ubuntu anyway, then re-install Ubuntu.
Yes, it will.  Why not install windows first.  It will also overwrite grub, which you'll reinstall when you install linux.

---


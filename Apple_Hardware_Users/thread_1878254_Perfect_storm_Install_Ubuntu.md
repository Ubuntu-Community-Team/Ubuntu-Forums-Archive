---
title: "Perfect storm: Install Ubuntu"
date: 2011-11-09
forum: Apple Hardware Users
---

### Post by tobyk100 on 2011-11-09
Hi all,

Yesterday the unibody A1342 crashed and now will only boot into a GNU Grub screen with Ubuntu version 1.99-12ubuntu5. When I select the option to boot Ubuntu it boots a command line. Well, I thought it was an easy fix: pop in the Ubuntu cd and reinstall. Nope, seems like the cd-rom drive is shot because it immediately ejects any cd I put in. 

So, I need a way to boot Ubuntu from the USB without actually being able to do anything special to my macbook (there’s no way to install any other software like rEFit). I’ve tried a USB boot but when I hold down option I just get one drive (called "windows" for some reason?).

Please, I’m about to rip the cd-drive out of my girlfriend’s macbook (same model). I don’t think she will like that.

P.S. tried this [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick), but I can’t enter BIOS?

---

### Post by coldraven on 2011-11-09
I know nothing about Macs but the USB drive might be called Windows because it is FAT32 formatted. maybe?

---

### Post by MacPenguin1972 on 2011-11-09
> **coldraven said:**
> I know nothing about Macs but the USB drive might be called Windows because it is FAT32 formatted. maybe?

I know FAT 32 is Windows and HFS is Mac. but what is the correct file sytem format for Ubuntu? And does that file format share among all linux versions or just Ubuntu? 

Thanks. :D

MP

Oh, and I'm finally past "5 Cups of Ubuntu"! (yippie!) lol!

---

### Post by tobyk100 on 2011-11-09
> **MacPenguin1972 said:**
> I know FAT 32 is Windows and HFS is Mac. but what is the correct file sytem format for Ubuntu? And does that file format share among all linux versions or just Ubuntu? 


I'm using my GFs macbook to try to format the USB stick and mount the ISO using the previous link: "InstallFromUSBStick."

How can I format the USB stick and mount the ISO, on the mac, then boot from the USB on another Mac (which happens to have Ubuntu that is booting Grub).

Alternatively, is there some trick to getting "regular" Ubuntu to load when my Mac wants to load Grub?

---

### Post by coldraven on 2011-11-10
> **MacPenguin1972 said:**
> I know FAT 32 is Windows and HFS is Mac. but what is the correct file sytem format for Ubuntu? And does that file format share among all linux versions or just Ubuntu? 

Thanks. :D

MP

Oh, and I'm finally past "5 Cups of Ubuntu"! (yippie!) lol!

For the last few versions Ubuntu uses ext4 but other Linuxs can use others
[http://en.wikipedia.org/wiki/File_system#Linux](http://en.wikipedia.org/wiki/File_system#Linux)
Congratulations Mr.5cup :)

---


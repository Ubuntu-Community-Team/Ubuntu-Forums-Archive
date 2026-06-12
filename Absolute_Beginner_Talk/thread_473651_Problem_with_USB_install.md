---
title: "Problem with USB install"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by bbyte on 2007-06-14
I have tried to find a solution by searching but didn't stumble on one (I am sure that it is here but didn't find it).  I installed Ubuntu 7.04 on a 6GB flash drive but never saw the opportunity to modify Grub.  It ended up on my laptops's hard drive and screwed up the Windows boot but the forum showed me the fixmbr method and that is working.

Now when I boot up it just goes to windows even though I am selecting the flash drive (I have a Toshiba satellite system where there is an option on booting to select your device).  I am not certain what I should set the menu list too.  The flash is listed using sudo fdisk -l as /dev/sdb.

TIA

---

### Post by tgalati4 on 2007-06-14
Try installing Grub to the USB drive.  When you fixed the MBR, you trashed the Grub bootloader that was installed in the MBR.  The menu's and second stage loader don't change, but you don't have the initial kicker that loads the menu.

---

### Post by floke on 2007-06-14
I think you have to use the alternative installer to get an option as to where to put grub. I've done it myself this way and confirm it works fine. Before installing though, make sure you know whan your drive is referred  to  - eg /dev/sdb1 - then enter this (eg /dev/sdb - note NOT the sdb1, sdb2 whatever - keep it numberless since it has to go to the mbr of the external disk) when you get to the grub install section, and all should be fine.

---

### Post by bbyte on 2007-06-14
Where do I find the alternate installer?

---

### Post by domat00 on 2007-06-14
[http://releases.ubuntu.com/7.04/](http://releases.ubuntu.com/7.04/)

---

### Post by bbyte on 2007-06-15
Thanks for your responses.  I gave up after using the alternative install and getting Grub properly loaded but still couldn't boot.  I believe that my laptop may not support booting from the flash.  I went ahead and installed a dual boot this morning; again thanks.

---


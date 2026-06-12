---
title: "GRUB problem!!! (HELP)"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by kbsuperstar on 2007-02-05
Ok, here's the situation:

I had 55 GB of my HD partitioned to Ubuntu, and 5 GB to Dreamlinux. I wanted to delete Dreamlinux and resize my HD so it was entirely dedicated to Ubuntu. So, after doing so, I rebooted and got the GRUB load 22 error, or whatever.

I then realized that when I had installed Dreamlinux, it had installed GRUB onto its own partition, and possibly erased the GRUB I had on Ubuntu. So, now I can't boot up into Ubuntu anymore.

How can I re-activate(?)/install GRUB onto the Ubuntu partition?????

This is really frustrating!!! I will be forever grateful to whoever helps me :D

---

### Post by phersotty on 2007-02-05
I am assuming that you installed Ubuntu before DreamLinux.  If so then you probably still have a a Ubuntu version of the Grub menu.  Try booting with the live cd and then goto /boot/grub/menu.lst on your Ubuntu partition.  You might have to chroot and reinstall grub, but I don't remember how to do that off the top of my head.

---

### Post by shareMenaPeace on 2007-02-05
Checkout

[http://www.arsgeek.com/?p=655](http://www.arsgeek.com/?p=655)

---

### Post by John E on 2007-02-05
Which was first on the drive - Dreamlinux or Ubuntu? If you've deleted a partition then Ubuntu (which might have been /dev/hda2) has possibly now become /dev/hda1

---

### Post by kbsuperstar on 2007-02-05
WOOHOO! It worked! Thank you!!! I am eternally grateful :D!!!!!!!!!!!!!!!!!!!


=D>

---


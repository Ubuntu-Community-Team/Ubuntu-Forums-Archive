---
title: "xunbuntu on a usb flash drive"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Russellvg on 2007-03-11
I have an xubuntu live disk and I installed xubuntu on my 2 gig usb flash disk. but when i go to start linux from thy grub menu it says cannot mount selected partition, press any key to continue and brings me back to the grub menu.  I know that linux is installed because when i look at the partitions with gnome partition editer, theres linux and linux's swap space. can someone help?

---

### Post by kerry_s on 2007-03-11
Xubuntu is not made for flash and you need to install the boot loader to the usb device and boot from that. Hope you don't mine losing that drive because a plain distro will reach the max amount of writes really quick.

---

### Post by Russellvg on 2007-03-11
what do u mean by max amount of writes?

---

### Post by dstew on 2007-03-11
Flash memory has a limited number of write cycles, maybe several million. So after a while, it fails to hold what is written to it. I have never tried it myself, but I suppose it would still last several months in constant use. That's just a guess though.

---

### Post by nhandler on 2007-03-11
So in other words, if this is going to be your main os, you should back up your data often to another drive. I would advise installing xubuntu to a hard drive. They are able to be written to more than a flash drive, and will last longer.

---


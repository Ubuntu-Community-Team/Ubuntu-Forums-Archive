---
title: "Can't install ethernet driver"
date: 2011-05-01
forum: Any Other OS
---

### Post by terrapin893 on 2011-05-01
I got my start on Ubuntu and I like it.  I am not a huge fan of Unity but I'm not one of those screaming about the horrors of it either . . .   I decided I'd like to try a couple of other distros.  I started with Arch and then Debian.  

On neither of these distros can I get my ethernet drivers installed.  Installing Ubuntu . . . it just works, it loads the e1000e kernel module and Im good.  I can even test it by removing the module with modprobe -r e1000e which will cause me to lose internet connectivity and then adding it back with modprobe e1000e and I will gain back connectivity.  

However when trying to install either Arch or Debian it is not working.  It has me completely baffled because my ethernet is not detected, and even adding the e1000e module does not do anything.  At first I thought it was just a problem I was having with Arch but after duplicating it with Debian I just do not know what to think.  

Any ideas?  I would love to try another distro.  Still have a laptop running Lubuntu . . . but I would like to branch out some more.

---

### Post by doorknob60 on 2011-05-05
Try installing the linux-firmware package in Arch. Got this by googling "e1000e Arch"

---


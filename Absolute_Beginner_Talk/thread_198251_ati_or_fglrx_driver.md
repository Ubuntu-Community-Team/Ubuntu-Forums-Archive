---
title: "ati or fglrx driver?"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2006-06-16
I have a ati agp radeon 9600 graphic card.. Which driver should i install for max performance??

---

### Post by x64Jimbo on 2006-06-16
The ati driver does not support 3D rendering, so your best option is to go with fglrx... However, there is a caveat. Have a look at this thread:
[https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/30447](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/30447)
Be warned. My machine will not do a clean shutdown with the fglrx driver installed. I've heard that it happens sometimes with the ati driver too. If you don't need 3D support right away, I'd suggest laying low for a little while and use whatever driver is working for you right now.  They'll probably have this bug fixed in the next round of patches, but in the mean time, you'll probably want to be able to reboot/shutdown your machine.

---

### Post by lime4x4 on 2006-06-16
currently running the fglrx drivers just seem to have really lof frame rates
And my machine shutsdown fine

---


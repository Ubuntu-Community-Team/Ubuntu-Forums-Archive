---
title: "usbvision help"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by Broken9754 on 2007-05-11
Sorry, I've tried searching the forums and found similar topics, but none of the solutions seem to be working. I'm trying to install the usbvision drivers but this is what happens when I try to "make"

make -C /lib/modules/2.6.17-11-generic/build SUBDIRS=/driver/usbvision/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
  CC [M]  /driver/usbvision/src/i2c-algo-usb.o
/driver/usbvision/src/i2c-algo-usb.c:45: error: expected ‘)’ before string constant
make[2]: *** [/driver/usbvision/src/i2c-algo-usb.o] Error 1
make[1]: *** [_module_/driver/usbvision/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
make: *** [default] Error 2
david@david:/driver/usbvision/src$ 

help please

---

### Post by Broken9754 on 2007-05-11
Nevermind, installing from CVS fixed it.

---

### Post by seriousstorm85 on 2007-06-13
Hi,

Can u please tell me what steps u took to fix your problem I am having the problem you had.
Here is my thread of my problem which is identical to yours [http://ubuntuforums.org/showthread.php?p=2815088#post2815088](http://ubuntuforums.org/showthread.php?p=2815088#post2815088)

---

### Post by wieman01 on 2007-08-24
To spread the word here as well... You don't need to install 'usbvision' from Feisty Fawn onwards as it has become part of the official kernel (2.6.20 onwards?). Upgrade to Feisty in that case.

---


---
title: "uvcvideo not working"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by foxjwill on 2006-08-18
Here's what I've done:
```
svn co http://svn.berlios.de/svnroot/repos/linux-uvc/linux-uvc/trunk/
make
sudo make install
```

Here's the outcome of make:
```
Building USB Video Class driver...
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
```

Here's the outcome of sudo make install:
```
Installing USB Video Class driver...
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-386'
  INSTALL /home/avi/checkout/linux-uvc/linux-uvc/trunk/uvcvideo.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
depmod -ae
```

However, the lines that were supposed to appear in dmesg did not.

---

### Post by foxjwill on 2006-08-18
Would somebody reply? I've posted this in a few different threads and nobody's said anything!

---


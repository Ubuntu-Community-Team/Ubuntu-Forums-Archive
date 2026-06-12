---
title: "A-link WL54H WLAN PCI Card driver problems"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by fi0na on 2008-02-02
I was referred to this page by the manual of my device: [ftp://ftp.a-link.com/wl54h/WL54H_WL54PC_RT61_Linux.tar.gz](ftp://ftp.a-link.com/wl54h/WL54H_WL54PC_RT61_Linux.tar.gz)
I downloaded and extracted the files. When I go to the Module folder and type "make", I get this error message:

:~/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module$ make
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/fi0na/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/fi0na/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.o
/home/fi0na/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c: In function ‘RT61_probe’:
/home/fi0na/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:197: error: ‘struct net_device’ has no member named ‘get_wireless_stats’
/home/fi0na/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c: In function ‘RT61_open’:
/home/fi0na/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:326: warning: ‘deprecated_irq_flag’ is deprecated (declared at include/linux/interrupt.h:66)
/home/fi0na/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:326: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
/home/fi0na/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c: In function ‘rt61_init_module’:
/home/fi0na/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:893: warning: implicit declaration of function ‘pci_module_init’
make[2]: *** [/home/fi0na/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/fi0na/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [all] Error 2

Does anyone have any ideas how to solve this and get my WLAN drivers installed properly?
Ndiswrapper might be an idea, huh?

---

### Post by Hightide on 2008-02-02
Hi fiOna

i would have a look at Kevdog's wireless [tutorial]("http://ubuntuforums.org/showthread.php?t=571188") to diagnose

and kevdog also does a good ndiswrapper [how to]("http://ubuntuforums.org/showthread.php?t=574501")

hope this helps

regards

:lolflag:

---

### Post by fi0na on 2008-02-09
I got stuck on that one immediately "Pre-requisites
1. Properly installed network driver" <- as you can see I got the error message when I tried to setup the driver for my Wi-Fi PCI card.

What to do?

---


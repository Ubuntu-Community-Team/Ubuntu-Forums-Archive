---
title: "Wireless enlwi-g2"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by hack13 on 2008-02-08
hey i have the ENLWI-G2. I used the driver from its site and this is what happend:

```

hack13@hack13:~$ cd Desktop/rtl8185_linux_26.1010.0531.2006 
hack13@hack13:~/Desktop/rtl8185_linux_26.1010.0531.2006$ sudo ./makedrv 
[sudo] password for hack13: 
Sorry, try again. 
[sudo] password for hack13: 
ieee80211/ 
ieee80211/ieee80211_tx.c 
ieee80211/Modules.symvers 
ieee80211/ieee80211_softmac_wx.c 
ieee80211/LICENSE 
ieee80211/ieee80211_rx.c 
ieee80211/ieee80211_crypt_tkip.c 
ieee80211/ieee80211_crypt.h 
ieee80211/ieee80211_crypt_ccmp.c 
ieee80211/ieee80211_module.c 
ieee80211/Makefile 
ieee80211/.tmp_versions/ 
ieee80211/.tmp_versions/ieee80211_crypt-rtl.mod 
ieee80211/.tmp_versions/ieee80211_crypt_wep-rtl.mod 
ieee80211/.tmp_versions/ieee80211_crypt_tkip-rtl.mod 
ieee80211/.tmp_versions/ieee80211_crypt_ccmp-rtl.mod 
ieee80211/.tmp_versions/ieee80211-rtl.mod 
ieee80211/ieee80211.h 
ieee80211/ieee80211_softmac.c 
ieee80211/README 
ieee80211/ieee80211_wx.c 
ieee80211/ieee80211_crypt_wep.c 
ieee80211/ieee80211_crypt.c 
rtl818x-0.1/ 
rtl818x-0.1/r8180_wx.h 
rtl818x-0.1/r8180_wx.c 
rtl818x-0.1/r8180_rtl8225.h 
rtl818x-0.1/r8180_rtl8255.h 
rtl818x-0.1/AUTHORS 
rtl818x-0.1/r8180_max2820.c 
rtl818x-0.1/r8180.h 
rtl818x-0.1/r8180_max2820.h 
rtl818x-0.1/tags 
rtl818x-0.1/r8180_sa2400.h 
rtl818x-0.1/r8180_93cx6.c 
rtl818x-0.1/ieee80211.h 
rtl818x-0.1/r8180_gct.c 
rtl818x-0.1/r8180_gct.h 
rtl818x-0.1/.r8180_core.o.d 
rtl818x-0.1/r8180_rtl8225.c.old 
rtl818x-0.1/Modules.symvers 
rtl818x-0.1/CHANGES 
rtl818x-0.1/LICENSE 
rtl818x-0.1/r8180_93cx6.h 
rtl818x-0.1/README.master 
rtl818x-0.1/r8180_hw.h 
rtl818x-0.1/README 
rtl818x-0.1/r8180_pm.c 
rtl818x-0.1/r8180_sa2400.c 
rtl818x-0.1/COPYING 
rtl818x-0.1/README.adhoc 
rtl818x-0.1/r8180_rtl8225.c 
rtl818x-0.1/.tmp_versions/ 
rtl818x-0.1/.tmp_versions/r8180.mod 
rtl818x-0.1/INSTALL 
rtl818x-0.1/r8180_rtl8255.c 
rtl818x-0.1/r8180_core.c 
rtl818x-0.1/r8180_pm.h 
rtl818x-0.1/Makefile 
rtl818x-0.1/ieee80211_crypt.h 
rm -f *.mod.c *.mod *.o .*.cmd *.ko 
rm -rf /home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/tmp 
make -C /lib/modules/2.6.22-14-generic/build M=/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211 CC=gcc modules 
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic' 
  CC [M]  /home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.o 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_scan_wq’: 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:391: warning: ISO C90 forbids mixed declarations and code 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:412: warning: passing argument 2 of ‘queue_delayed_work’ from incompatible pointer type 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_stop_scan’: 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:486: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_associate_abort’: 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:885: warning: passing argument 2 of ‘queue_delayed_work’ from incompatible pointer type 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:1359:4: warning: #warning CHECK_LOCK_HERE 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:1399:2: warning: #warning CHECK_LOCK_HERE 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_rx_frame_softmac’: 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:1470: warning: ISO C90 forbids mixed declarations and code 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_stop_protocol’: 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2059: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2167:78: error: macro "INIT_WORK" passed 3 arguments, but takes just 2 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_init’: 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2167: error: ‘INIT_WORK’ undeclared (first use in this function) 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2167: error: (Each undeclared identifier is reported only once 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2167: error: for each function it appears in.) 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2168:88: error: macro "INIT_WORK" passed 3 arguments, but takes just 2 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2169:94: error: macro "INIT_WORK" passed 3 arguments, but takes just 2 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2170:96: error: macro "INIT_WORK" passed 3 arguments, but takes just 2 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2171:82: error: macro "INIT_WORK" passed 3 arguments, but takes just 2 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2172:82: error: macro "INIT_WORK" passed 3 arguments, but takes just 2 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_free’: 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2191: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type 
make[2]: *** [/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.o] Error 1 
make[1]: *** [_module_/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211] Error 2 
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic' 
make: *** [modules] Error 2 
rm -f *.mod.c *.mod *.o .*.cmd *.ko 
rm -rf /home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/tmp 
make -C /lib/modules/2.6.22-14-generic/build M=/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1 CC=gcc modules 
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic' 
  CC [M]  /home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.o 
In file included from /home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:61: 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180.h:29:26: error: linux/config.h: No such file or directory 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c: In function ‘rtl8180_rx’: 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:2080: warning: implicit declaration of function ‘rdtsc’ 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:2953:67: error: macro "INIT_WORK" passed 3 arguments, but takes just 2 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c: In function ‘rtl8180_init’: 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:2953: error: ‘INIT_WORK’ undeclared (first use in this function) 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:2953: error: (Each undeclared identifier is reported only once 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:2953: error: for each function it appears in.) 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:3276: warning: ‘deprecated_irq_flag’ is deprecated (declared at include/linux/interrupt.h:66) 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:3276: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c: In function ‘rtl8180_pci_probe’: 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:4031: error: ‘struct net_device’ has no member named ‘get_wireless_stats’ 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c: In function ‘rtl8180_pci_module_init’: 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:4156: warning: implicit declaration of function ‘pci_module_init’ 
make[2]: *** [/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.o] Error 1 
make[1]: *** [_module_/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1] Error 2 
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic' 
make: *** [modules] Error 2 

```

I am running duel boot so i can get online the wireless enlwi-g2 is my only way to get online. so can some one please help!!! Also i am new to Linux and but i did use another linux version but yours is more beginner friendly so i came here so can someone please help me use this card and i could not get it to work on the other linux dist. i used so I really want to use linux and get off window!!! 
Thank you in advance.

---

### Post by Hightide on 2008-02-16
HI Hack13

have a look at Kevdog's wireless [tutorial]("http://ubuntuforums.org/showthread.php?t=571188") for guidance.


regards
:)

---


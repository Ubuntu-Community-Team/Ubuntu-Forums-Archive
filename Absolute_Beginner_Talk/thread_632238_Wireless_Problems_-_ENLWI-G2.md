---
title: "Wireless Problems - ENLWI-G2"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by forbushbl on 2007-12-05
I'm having problems getting my wireless card to work. The card is made by Encore Electronics, Inc. which is definitely not top of the line by any means. The Model is ENLWI-G2. I found the driver [**[COLOR="Blue"]HERE[/COLOR]**]("http://www.encore-usa.com/product_item.php?region=us&bid=2&pgid=81_4&pid=285#DOWNLOAD"). On the Encore website they provide a linux driver but i couldn't get the scripts to do anything. Well they did something but it just returned an error. Does anyone have any idea where I can get some decent installation instructions? I have no idea how to install the driver manually. Any help would be appreciated!

---

### Post by OffAxis on 2007-12-05
> i couldn't get the scripts to do anything.
did you run the scripts preceded with the **sudo **command?

for instance, once in the rtl8185_linux_26.1010.0531.2006 directory
```
sudo ./makedrv
```

---

### Post by forbushbl on 2007-12-05
I will give that a try.

---

### Post by forbushbl on 2007-12-05
Here is what it gives me, same problem... Any other suggestions?

```
[root@localhost asdf]# sudo ./makedrv
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
./makedrv: line 6: make: command not found
./makedrv: line 7: make: command not found
./makedrv: line 9: make: command not found
./makedrv: line 10: make: command not found
[root@localhost asdf]# 
```

---

### Post by Aperion on 2007-12-15
> **forbushbl said:**
> Here is what it gives me, same problem... Any other suggestions?

```
[root@localhost asdf]# sudo ./makedrv
...
./makedrv: line 6: make: command not found
./makedrv: line 7: make: command not found
./makedrv: line 9: make: command not found
./makedrv: line 10: make: command not found
[root@localhost asdf]# 
```

if it can't find the make command, then you probably haven't installed the build-essentials package. install this will install make. I'm interested in this driver, so post up here again if you get it to work.

---

### Post by ronniemiller on 2007-12-20
Hi, I'm not trying to hijack, but I'm having the same issue. I'm on a clean install of gutsy. I installed the build-essential package, then tried running the manufacturer's install script. I got a lot of output, but couldn't make much sense of it.

```
ronnie@ronnies-desktop:~/Desktop/rtl8185_linux_26.1010.0531.2006$ sudo ./makedrv
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
ieee80211/.tmp_versions/ieee80211_crypt- rtl.mod
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
rtl818x-0.1 /r8180_wx.c
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
rtl818x-0.1 /CHANGES
rtl818x-0.1/LICENSE
rtl818x-0.1/r8180_93cx6.h
rtl818x-0.1/README.master
rtl818x-0.1/r8180_hw.h
rtl818x-0.1/README
rtl818x-0.1/r8180_pm.c
rtl818x-0.1/r8180_sa2400.c
rtl818x-0.1/COPYING
rtl818x-0.1 /README.adhoc
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
rm -rf /home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/tmp
make -C /lib/modules/2.6.22-14-generic/build M=/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.o
/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c: In function 'ieee80211_softmac_scan_wq':
/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:391: warning: ISO C90 forbids mixed declarations and code
/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:412: warning: passing argument 2 of 'queue_delayed_work' from incompatible pointer type
/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c: In function 'ieee80211_softmac_stop_scan':
/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:486: warning: passing argument 1 of 'cancel_delayed_work' from incompatible pointer type
/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c: In function 'ieee80211_associate_abort':
/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:885: warning: passing argument 2 of 'queue_delayed_work' from incompatible pointer type
/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:1359:4: warning: #warning CHECK_LOCK_HERE
/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:1399:2: warning: #warning CHECK_LOCK_HERE
/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c: In function 'ieee80211_rx_frame_softmac':
/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:1470: warning: ISO C90 forbids mixed declarations and code
/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c: In function 'ieee80211_stop_protocol':
/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2059: warning: passing argument 1 of 'cancel_delayed_work' from incompatible pointer type
/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2167:78: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c: In function 'ieee80211_softmac_init':
/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2167: error: 'INIT_WORK' undeclared (first use in this function)
/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2167: error: (Each undeclared identifier is reported only once
/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2167: error: for each function it appears in.)
/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2168:88: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2169:94: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2170:96: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2171:82: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2172:82: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c: In function 'ieee80211_softmac_free':
/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2191: warning: passing argument 1 of 'cancel_delayed_work' from incompatible pointer type
make[2]: *** [/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.o] Error 1
make[1]: *** [_module_/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211] Error 2
make[1]: Leaving directory `/usr/src/linux- headers-2.6.22-14-generic'
make: *** [modules] Error 2
rm -f *.mod.c *.mod *.o .*.cmd *.ko
rm -rf /home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/tmp
make -C /lib/modules/2.6.22-14-generic/build M=/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x- 0.1 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.o
In file included from /home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x- 0.1/r8180_core.c:61:
/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180.h:29:26: error: linux/config.h: No such file or directory
/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c: In function 'rtl8180_rx':
/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:2080: warning: implicit declaration of function 'rdtsc'
/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:2953:67: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c: In function 'rtl8180_init':
/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:2953: error: 'INIT_WORK' undeclared (first use in this function)
/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:2953: error: (Each undeclared identifier is reported only once
/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:2953: error: for each function it appears in.)
/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:3276: warning: 'deprecated_irq_flag' is deprecated (declared at include/linux/interrupt.h:66)
/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x- 0.1/r8180_core.c:3276: warning: passing argument 2 of 'request_irq' from incompatible pointer type
/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c: In function 'rtl8180_pci_probe':
/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x- 0.1/r8180_core.c:4031: error: 'struct net_device' has no member named 'get_wireless_stats'
/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c: In function 'rtl8180_pci_module_init':
/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x- 0.1/r8180_core.c:4156: warning: implicit declaration of function 'pci_module_init'
make[2]: *** [/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.o] Error 1
make[1]: *** [_module_/home/ronnie/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x- 0.1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [modules] Error 2
ronnie@ronnies-desktop:~/Desktop/rtl8185_linux_26.1010.0531.2006$
```

Any help would be greatly appreciated.

---

### Post by Presto123 on 2007-12-20
Is this card not available in the "Restricted Drivers Manager"?

---

### Post by ronniemiller on 2007-12-20
Nope, looks like its not. When I go to the restricted drivers manager it just says "Your hardware does not need any restricted drivers."

---

### Post by Presto123 on 2007-12-20
Ew...okay.

It looks as if you haven't navigated to the folder location. I could be wrong, but on the safe side, lets try this:

```
cd Desktop/rtl8185_linux_26.1010.0531.2006
```

And try the code listed above.

**Edit**Crap, I just noticed you did.

---

### Post by Presto123 on 2007-12-20
I tried it, and it gets me the install, but with an error 2 (I am assuming that this is because I don't have it installed).

**Edit this too**I got the same error as Ronnie. Bah!

---

### Post by hack13 on 2008-02-07
hey i have the ENLWI-G2. I used the driver and this is what happend:

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
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_softmac_scan_wq&#8217;: 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:391: warning: ISO C90 forbids mixed declarations and code 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:412: warning: passing argument 2 of &#8216;queue_delayed_work&#8217; from incompatible pointer type 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_softmac_stop_scan&#8217;: 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:486: warning: passing argument 1 of &#8216;cancel_delayed_work&#8217; from incompatible pointer type 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_associate_abort&#8217;: 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:885: warning: passing argument 2 of &#8216;queue_delayed_work&#8217; from incompatible pointer type 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:1359:4: warning: #warning CHECK_LOCK_HERE 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:1399:2: warning: #warning CHECK_LOCK_HERE 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_rx_frame_softmac&#8217;: 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:1470: warning: ISO C90 forbids mixed declarations and code 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_stop_protocol&#8217;: 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2059: warning: passing argument 1 of &#8216;cancel_delayed_work&#8217; from incompatible pointer type 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2167:78: error: macro "INIT_WORK" passed 3 arguments, but takes just 2 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_softmac_init&#8217;: 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2167: error: &#8216;INIT_WORK&#8217; undeclared (first use in this function) 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2167: error: (Each undeclared identifier is reported only once 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2167: error: for each function it appears in.) 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2168:88: error: macro "INIT_WORK" passed 3 arguments, but takes just 2 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2169:94: error: macro "INIT_WORK" passed 3 arguments, but takes just 2 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2170:96: error: macro "INIT_WORK" passed 3 arguments, but takes just 2 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2171:82: error: macro "INIT_WORK" passed 3 arguments, but takes just 2 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2172:82: error: macro "INIT_WORK" passed 3 arguments, but takes just 2 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_softmac_free&#8217;: 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:2191: warning: passing argument 1 of &#8216;cancel_delayed_work&#8217; from incompatible pointer type 
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
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c: In function &#8216;rtl8180_rx&#8217;: 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:2080: warning: implicit declaration of function &#8216;rdtsc&#8217; 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:2953:67: error: macro "INIT_WORK" passed 3 arguments, but takes just 2 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c: In function &#8216;rtl8180_init&#8217;: 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:2953: error: &#8216;INIT_WORK&#8217; undeclared (first use in this function) 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:2953: error: (Each undeclared identifier is reported only once 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:2953: error: for each function it appears in.) 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:3276: warning: &#8216;deprecated_irq_flag&#8217; is deprecated (declared at include/linux/interrupt.h:66) 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:3276: warning: passing argument 2 of &#8216;request_irq&#8217; from incompatible pointer type 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c: In function &#8216;rtl8180_pci_probe&#8217;: 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:4031: error: &#8216;struct net_device&#8217; has no member named &#8216;get_wireless_stats&#8217; 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c: In function &#8216;rtl8180_pci_module_init&#8217;: 
/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.c:4156: warning: implicit declaration of function &#8216;pci_module_init&#8217; 
make[2]: *** [/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.o] Error 1 
make[1]: *** [_module_/home/hack13/Desktop/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1] Error 2 
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic' 
make: *** [modules] Error 2 

```

I am running duel boot so i can get online the wireless enlwi-g2 is my only way to get online. so can some one please help!!! Also i am new to Linux and but i did use another linux version but yours is more beginner friendly so i came here so can someone please help me use this card and i could not get it to work on the other linux dist. i used so I really want to use linux and get off window!!! 
Thank you in advance.

---

### Post by hack13 on 2008-02-08
can anyone please help!!! I am using grusty gibbin

---


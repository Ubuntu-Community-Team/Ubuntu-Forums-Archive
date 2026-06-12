---
title: "tried to patch wireless card now its not working"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by usmc1991 on 2007-12-16
I am trying to install aircrack -ng on my computer. I downloaded the injection patch for the ipw2200 driver and the ieee80211-1.2.17 library. I did not install the ieee80211-1.2.17 library fist but i executed these two commands:

patch -p0 < ipw2200-1.2.1-inject_Makefile.patch
&
patch -p0 < ipw2200-1.2.1-inject.patch

after i did that my wireless card stopped working. I suspect the only thing i need to do to fix it is install the rest of the ipw2200 patch but to do that i have to install the above library. However, when execute the sudo make command i get this:

Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
Checking in /lib/modules/2.6.22-14-generic for ieee80211 components...
make -C /lib/modules/2.6.22-14-generic/build M=/home/kyle/ipw2200-1.2.1/ieee80211-1.2.17 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
/home/kyle/ipw2200-1.2.1/ieee80211-1.2.17/Makefile:17: 
/home/kyle/ipw2200-1.2.1/ieee80211-1.2.17/Makefile:18: WARNING: $SHELL not set to bash.
/home/kyle/ipw2200-1.2.1/ieee80211-1.2.17/Makefile:19: If you experience build errors, try
/home/kyle/ipw2200-1.2.1/ieee80211-1.2.17/Makefile:20: 'make SHELL=/bin/bash'.
/home/kyle/ipw2200-1.2.1/ieee80211-1.2.17/Makefile:21: 
  CC [M]  /home/kyle/ipw2200-1.2.1/ieee80211-1.2.17/ieee80211_tx.o
/home/kyle/ipw2200-1.2.1/ieee80211-1.2.17/ieee80211_tx.c: In function ‘ieee80211_classify’:
/home/kyle/ipw2200-1.2.1/ieee80211-1.2.17/ieee80211_tx.c:232: error: ‘struct sk_buff’ has no member named ‘nh’
make[2]: *** [/home/kyle/ipw2200-1.2.1/ieee80211-1.2.17/ieee80211_tx.o] Error 1
make[1]: *** [_module_/home/kyle/ipw2200-1.2.1/ieee80211-1.2.17] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [modules] Error 2

Please help!

---


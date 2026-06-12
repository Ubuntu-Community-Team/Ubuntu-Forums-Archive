---
title: "G5 and xgl help"
date: 2006-06-07
forum: Apple PPC Users
---

### Post by elementxyz on 2006-06-07
Can i get the wonderfull xgl desktop to run?
I have a G5 with a ATI 9600. I have searched the forum for information but I'm not sure. I have found some threads. And they say i must install a ati driver. If i type fglrxinfo in the terminal. It says command not found. If i try 
sudo apt-get install linux-restricted-modules-$ (uname -r)
It says that no packages available for 64. Must i ad a new repository?

---

### Post by stmiller on 2006-08-15
I've also got a powermac G5 with a Radeon 9600. Were you able to get 3D going? I'm running kernel 2.6.17.8 with radeon and ati support enabled. Also have installed ubuntu's xserver-xorg-drivers-radeon pacakage, but cannot load the radeon module (says not found).

Contact me via PM if you have had any luck. Thanks,

---

### Post by rasec on 2006-08-15
ATI hasn't release their fglrx drivers for the powerpc, and I doubt they ever will. The driver that you're trying to install is for the x86/x86_64 only. 

You might have better luck getting aiglx/compiz working if you can find a radeon 8500/9x00 card, as those have open source accelerated dri drivers. I think there might be pre-beta state drivers the the 9600, but the last time I checked on them they were still in their infancy state.

---


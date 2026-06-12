---
title: "[SOLVED] Ethernet problems in arch"
date: 2008-02-08
forum: Arch and derivatives
---

### Post by sujoy on 2008-02-08
from hwd -s

Ethernet : NetLink BCM5906M Fast Ethernet PCI Express module:tg3

the problem is that my ethernet works only when i boot into the Arch Linux Fallback, in the normal boot it doesn't work.

ifconfig only shows the lo
ifconfig eth0 shows the usual data, like Bcast, Mask, inet addr, etc, etc,
but ifconfig eth0 up shows
SIOCSIFFLAGS: No such file or directory.

also while boot up it shows starting network and then SIOCSIFFLAGS error............and once again while shutdown

/etc/rc.d/network restart shows

Stopping Network
SIOCDELRT: No such process

Starting Network
SIOCSIFFLAGS: No such file or directory
SIOCADDRT: No such process

please help me on this.

---

### Post by pelle.k on 2008-02-08
You might want to use *arch* subforum for this thread.
You need to add tg3 to MODULES="" in rc.conf.

---

### Post by sujoy on 2008-02-08
i guess a moderator can move the thread to its proper place.

yes the tg3 module was already there in MODULES=""  in rc.conf

strangely it works fine when i boot to fallback!! 
and more strangely, the problem is with eth0, that is the ethernet
i can do ifconfig eth1 up without any problem, which is my wireless interface !!!

---

### Post by fwojciec on 2008-02-08
OK, this is a random suggestion... Try adding the tg3 module to the MODULES section in /etc/mkinitcpio.conf and, afterwards, regenerate the kernel image with mkinitcpio -p kernel26 (as root) + reboot.  The only thing different between the regular and fallback boot options is the configuration of mkinitcpio.conf (the fallback uses /etc/mkinitcpio.d/kernel26-fallback.conf) so you might want to compare the two and see what's different between them.

---

### Post by sujoy on 2008-02-08
> **fwojciec said:**
> OK, this is a random suggestion... Try adding the tg3 module to the MODULES section in /etc/mkinitcpio.conf and, afterwards, regenerate the kernel image with mkinitcpio -p kernel26 (as root) + reboot.  The only thing different between the regular and fallback boot options is the configuration of mkinitcpio.conf (the fallback uses /etc/mkinitcpio.d/kernel26-fallback.conf) so you might want to compare the two and see what's different between them.

thank you so much! it works great now :)
spend the whole evening trying to figure this out .......

---

### Post by fwojciec on 2008-02-08
No problem -- have fun with Arch!!

---

### Post by K.Mandla on 2008-02-10
Moved to Arch subforum, even though it's solved. Just because I can. :mrgreen:

---


---
title: "Cannot capture with kino"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by adam s on 2007-03-26
Hi,

I have just installed a PCI Firewire card.

I have tested this with gscanbus and the firewire card appears to be working  (it recognises my camera when plugged in)

I have just tried to capture using kino and I get the following warning :

WARNING: dv1394 kernel module not loaded or failure to read/write /dev/ieee1394/dvhost0/PAL/in

I get this error running as myself and with sudo. and the directory /dev/ieee1394 does not exist.

I have installed kino and kinoplus, libavc1394-0, libavc1394-13, libraw1394-5 and  libraw1394-8

Any ideas?

Thanks,

Adam

---

### Post by adam s on 2007-03-27
Any ideas?

Would a Feisty install in a few weeks time solve the problem?
(Definitely not my first solution choice.....)

Thanks,

Adam.

---

### Post by adam s on 2007-03-27
I have managed to solve the capture problem. I now need to sort out sound.....

The solution was to open kino, and change the dv1394 device in the menu option Edit > Preferences > IEEE1394 to /dev/dv1394-0

Adam.

---


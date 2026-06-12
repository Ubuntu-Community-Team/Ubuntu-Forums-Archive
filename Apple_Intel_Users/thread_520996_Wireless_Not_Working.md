---
title: "Wireless Not Working"
date: 2007-08-08
forum: Apple Intel Users
---

### Post by johnsdr on 2007-08-08
I cannot seem to get my wireless working on this iMac. Could someone please offer me some assistance. Thanks

---

### Post by cyberdork33 on 2007-08-08
ndiswrapper

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29)

---

### Post by sefs on 2007-08-10
Is ndiswrapper the only way to get wireless working with the mac book?

---

### Post by cyberdork33 on 2007-08-10
> **sefs said:**
> Is ndiswrapper the only way to get wireless working with the mac book?

no
MacBooks have a different WiFi chip than iMacs. I am not sure what your MacBook has, but it is likely atheros and shouldn't take much to get working.

---

### Post by bimo on 2007-08-11
just follow this guide

[http://www.penlug.org/twiki/bin/view/Main/LinuxHardwareInfoAppleiMac24](http://www.penlug.org/twiki/bin/view/Main/LinuxHardwareInfoAppleiMac24)

mine work perfectly although everytime i log in
the wireless didn't detect automaticly

---

### Post by cyberdork33 on 2007-08-11
That guide is for broadcom and ndiswrapper. i.e. iMac, not MacBook

---

### Post by zAo on 2007-08-14
This is still the only reason I don't run Ubuntu on my iMac C2D: I need my WPA connection.

Why aren't there any drivers in development for this chip!?

---

### Post by cyberdork33 on 2007-08-14
> **zAo said:**
> This is still the only reason I don't run Ubuntu on my iMac C2D: I need my WPA connection.
ndiswrapper works fine with WPA

> Why aren't there any drivers in development for this chip!?
There is, sort of... bcm43xx. [http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/)
The issue is Broadcom. If you want linux drivers bug them, because they have refused for YEARS to develop their own drivers and/or give information to the community so that we can make our own.

---


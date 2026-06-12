---
title: "Apple PPC: WLAN"
date: 2010-09-18
forum: Apple Hardware Users
---

### Post by newbody on 2010-09-18
Hei,

I'm running Ubuntu 10.4 on Apple PPC G5!
I found a WLAN-Stick: AVM Fritz Stick
To install it, with drivers I used this (german) tutorial: [http://wiki.ubuntuusers.de/FRITZ%21WLAN_USB_Stick](http://wiki.ubuntuusers.de/FRITZ%21WLAN_USB_Stick)
But for some steps I need ndiswrapper, which isn't availabale for PPC.
So can I use my stick?

Lg

---

### Post by linuxopjemac on 2010-09-18
I would try to install the linux-backports-modules-wireless-lucid-generic package and see if your card is recognised then (dmesg). Then network-manager to see if you can connect to a network.

---

### Post by newbody on 2010-09-19
> **linuxopjemac said:**
> I would try to install the linux-backports-modules-wireless-lucid-generic package and see if your card is recognised then (dmesg). Then network-manager to see if you can connect to a network.

Where / How  can I install this package?

---

### Post by barbaGNU on 2010-09-19
> **newbody said:**
> Hei,

I'm running Ubuntu 10.4 on Apple PPC G5!
I found a WLAN-Stick: AVM Fritz Stick
To install it, with drivers I used this (german) tutorial: [http://wiki.ubuntuusers.de/FRITZ%21WLAN_USB_Stick](http://wiki.ubuntuusers.de/FRITZ%21WLAN_USB_Stick)
But for some steps I need ndiswrapper, which isn't availabale for PPC.
So can I use my stick?

Lg

ndiswrapper doesn't work on PPC 'cause his massive use of x86 assembler code.

---

### Post by newbody on 2010-09-19
> **barbaGNU said:**
> ndiswrapper doesn't work on PPC 'cause his massive use of x86 assembler code.

I know! But, exist an alternative solution :KS

---

### Post by linuxopjemac on 2010-09-19
```
sudo apt-get install linux-backports-modules-wireless-lucid-generic
```

---

### Post by newbody on 2010-09-19
Paket linux-backports-modules-wireless-lucid-generic konnte nicht gefunden werden

(german)

= he didn't found the package

---


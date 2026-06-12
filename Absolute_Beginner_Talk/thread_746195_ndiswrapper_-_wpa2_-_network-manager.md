---
title: "ndiswrapper - wpa2 - network-manager"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by benste on 2008-04-05
Hy guys, I'm using Ndiswrapper on hardy with a fwlan usb stick.
It was a very long way of getting this to work 
1. 2.6.24.13 ndiswrapper BUg
than - 2.6.24.14 nvidia glx problems, because of dpkg-reconfigure xserver (without -phigh)

and now. It works
but only wihtout security key, 

I can connect to a none secured network, maybe also WEP but WPA and WPA2 doesn't work, my router reports wrong key, and my computer keeps asking for passwort,

someone an idea what to do?

---

### Post by techolous on 2008-04-05
Im having the same problem. I can connect to unsecured networks, but I have to manually configure it to connect to a WPA2 protected network (**left** click on the network-manager icon and select 'Manual configuration'). Even after configuring it manualy, I still have to go into a terminal and reload ndiswrapper on occasion.

EDIT: fixed the spelling of 'network-manager'

---


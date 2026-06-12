---
title: "need help with usb ethernet"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by mªrty on 2006-07-24
hi,

i have a netcomm np1010 usb ethernet adapter i'm attempting to use  with a computer i just installed ubuntu 5.10 on.
the irony is i need the internet to get updates so i can use my wireless adapter (a netgear wg311 v3) ](*,)  ](*,) 

apparently this device uses the rtl8150 module, which is on the system.
when connected, the '100meg' led comes on, but not the ACT led.
EDIT: i managed to get the lan key working. don't really know how.

---

### Post by mªrty on 2006-07-24
wow! i got the usb ethernet to work...

any suggestions on getting my wg311 v3 to work?

i think i have _ndiswrapper_ installed. i installed the wireless tools via synaptic package manager. but when i go to network settings, there is only eth0 and lo.

when i do *modprobe ndiswrapper* i get: **FATAL: Module ndiswrapper not found.**

iwconfig shows wlan0 has signal -51dB...but it won't let me set the ESSID or key, even when i use 'sudo'

---


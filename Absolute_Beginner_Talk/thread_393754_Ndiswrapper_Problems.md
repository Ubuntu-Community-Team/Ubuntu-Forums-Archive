---
title: "Ndiswrapper Problems"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by sunexplodes on 2007-03-26
Okay, I am using Feisty Beta. I have a D-Link DWL g132 USB Wireless adapter. I've got NDISWrapper set up well enough that the wireless WORKS. 

What it doesn't do, is work painlessly as it did in Dapper and Edgy. 

1) If I leave the usb dongle plugged in on boot, the startup freezes indefinitely at the networking stage. I unplug when rebooting, plug back in when i reach GDM.

2) When I DO get into my desktop, NetworkManager attempts to connect to my default network and fails. I open a terminal and type "/etc/init.d/network restart", it does its thing, and then NetworkManager has no problem connecting.


Any ideas for solving these irritations?

---

### Post by mi_were on 2007-03-26
i had the same problem after upgrading the linux image I uninstalled the wireless windows driver and reinstalled it. It has worked like a charm ever since. Hope it does the same for u.

---

### Post by sunexplodes on 2007-03-26
No luck, sadly. Thanks though.

Any other ideas, anybody?

---


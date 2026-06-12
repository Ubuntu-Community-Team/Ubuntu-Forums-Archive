---
title: "Macbook Wireless"
date: 2008-08-01
forum: Apple Hardware Users
---

### Post by Meepzorzes on 2008-08-01
Okay, i have a macbook4,1 C2D (Broadcom BCM43xx card) and i've successfully installed the drivers and I can recognize wireless networks, but cannot connect to any of them. Have tried WPA2, open, and WEP networks with no luck. Ideas as to how to fix this?

-Ubuntu Hardy 8.04

---

### Post by hajk on 2008-08-01
Can't you do better than "BCM43xx"? There have been reports in these forums on WPA/WPA2 Personal problems with Broadcom 4328 rev 05 wireless chipsets, might also pertain to you. Use the "sudo lsusb" command to know for sure, and then (if applicable) the search function in this forum.

---

### Post by cyberdork33 on 2008-08-01
> **hajk said:**
> Can't you do better than "BCM43xx"? There have been reports in these forums on WPA/WPA2 Personal problems with Broadcom 4328 rev 05 wireless chipsets, might also pertain to you. Use the "sudo lsusb" command to know for sure, and then (if applicable) the search function in this forum.
If it is a MacBook4,1 then it should be the rev5 card.

---


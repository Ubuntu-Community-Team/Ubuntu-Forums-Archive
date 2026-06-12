---
title: "USB ether-net connection"
date: 2013-02-08
forum: Any Other OS
---

### Post by ikrum on 2013-02-08
BackTrack is ubuntu based, So i want to share my problem here !

I am using wired connection. ISP has given me **a username , password** and they noted my **mac address.**

I have configured PPPOE connection by **pppoeconf** using my username and password. it works fine when i connect through my main laptop lan port. When i connect through usb ether-net port and reconfigure it shows eth1 [installed].

But the main problem is my mac address. since my usb ether-net MAC is different i can't use internet.

so i have to use my main Mac. i have changed mac from ```
/etc/udev/rules.d/70-persistent-net.rules
```.
but when i want to configure / restart it creates another one with its own mac.

i downloaded Network manager , but i cant fix it.

**is there any way to make connection through my Ether-net usb device in UBUNTU / Backtrack.**

Please Help !!!!

---

### Post by coffeecat on 2013-02-08
*Thread moved to **Other OS/Distro Talk**.*

---

### Post by mips on 2013-02-09
Why don't you let your router handle the authentication?

---


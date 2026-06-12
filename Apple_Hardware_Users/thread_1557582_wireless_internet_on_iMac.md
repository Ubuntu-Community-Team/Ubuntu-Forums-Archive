---
title: "wireless internet on iMac"
date: 2010-08-20
forum: Apple Hardware Users
---

### Post by laurenbanjo on 2010-08-20
How do I set up the wireless internet on Ubuntu 10.04 on my iMac?

Mac OSX 10.6
2.4 GHz Intel Core 2 Duo
4 GB Memory 800 MHz DDr2 SDRAM

I don't know what this stuff means, but it was under the information about Airport so I'll include it:

 Software Versions:
  Menu Extra:    6.0 (600.22)
  configd plug-in:    6.0 (600.27)
  System Profiler:    6.0 (600.9)
  Network Preference:    6.0 (600.22)
  AirPort Utility:    5.4.2 (542.23)
  IO80211 Family:    3.0 (300.20)
  Interfaces:
en1:
  Card Type:    AirPort Extreme  (0x14E4, 0x8C)
  Firmware Version:    Broadcom BCM43xx 1.0 (5.10.91.19)
  Locale:    FCC
  Country Code:    US
  Supported PHY Modes:    802.11 a/b/g/n
  Supported Channels:    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 124, 128, 132, 136, 140, 149, 153, 157, 161, 165
  Wake On Wireless:    Supported
  Status:    Connected

---

### Post by linuxopjemac on 2010-08-21
[http://mac.linux.be/phpBB3/viewtopic.php?f=3&t=23](http://mac.linux.be/phpBB3/viewtopic.php?f=3&t=23)

---

### Post by JuliaKhanam on 2010-08-21
If it doesn't have wireless built in, you will have to buy an airport  card and install it.  If built in, there is networking settings in the  accessories that you can set like on a windows machine.  Just make sure  you apply them.

---

### Post by linuxopjemac on 2010-08-21
JuliaKhanam: thanks for your helpful contributions

---

### Post by laurenbanjo on 2010-08-21
> **JuliaKhanam said:**
> If it doesn't have wireless built in, you will have to buy an airport  card and install it.  If built in, there is networking settings in the  accessories that you can set like on a windows machine.  Just make sure  you apply them.
Built in? 
You mean, am I using an external card or a USB drive or something to connect to wireless?
No, the wifi is already "inside" the iMac. I don't even use the wired connection because I can't get it to this room.

---

### Post by furok23 on 2010-08-22
do you simply want to connect to your currently available wireless network? or do u want to create a network with your mac?

either way, you need to install the proprietary drivers that are found when you perform the driver find function

system>administration>hardware drivers

from there, the needed drivers should be found in the menu (specifically the wifi one you need)

just install them and restart

---


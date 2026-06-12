---
title: "wireless connection"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by limac on 2007-10-14
hi,

I'm using a netgear router. My laptop is on wireless connection. And I am currently dual-booting with vista and ubuntu 7.04. When i recently installed ubuntu it ran on wireless perfectly. Then after a couple of days we checked up on vista and vista wasn't on wireless at that time when we checked up on it.  Then after playing around a while with vista's wireless networking and I then enabled the wireless connection for vista. I for the first time went on line on vista after downloading ubuntu 7.04. And then later when I went on ubuntu again it could not connect to any wireless networks from then. Normally when I clicked on the monitor on the top right side of the screen for wireless it usually shows all the wireless connections in range and now it only says wired network ,which is disabled and manual configuration, which only has wired connection in it and modem connection, it doesn't show any wireless connections in range, not even ours. So how can I get over with this problem. 

Thnx :popcorn:

---

### Post by julian67 on 2007-10-16
Many laptops have buttons to switch wireless on and off. This can be hardware switch (a physical button or switch/slider) on the laptop or a software switch (perhaps a key combination fn+F4 for example). Also the wireless applications themselves can switch the radio on/off. Chances are that you need to check that the radio is actually switched on both via the physical switch and any key combo. 

if you run the command in Ubuntu ```
iwconfig
``` and see something like "radio kill switch on" then you know this is the case.

---

### Post by limac on 2007-10-16
if I use that command it says :

Lo        no wireless extensions.

eth0      no wireless extensions.

So what shoul I do?

---

### Post by julian67 on 2007-10-16
> **limac said:**
> if I use that command it says :

Lo        no wireless extensions.

eth0      no wireless extensions.

So what shoul I do?

could be the physical switch is off

otherwise it looks like the driver for your wireless card isn't loaded. suggest you check the howtos and so on in these forums for loading your wireless card's driver.

---

### Post by Pumalite on 2007-10-16
Wireless:

[http://www.linux.com/feature/56946](http://www.linux.com/feature/56946)

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946)

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion](https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion)

[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

---


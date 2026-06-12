---
title: "Trouble with TP-Link USB wireless adapter"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by ajmo on 2007-07-15
I just installed xubuntu alternative 7.04 on a celeron 433MHz with 64MB RAM (which I've since upped to 192MB) that used to run W98 (I did a clean install).

Its my first Linux experience, and its fun, except for getting my TP-Link TL-WN321G wireless USB adapter to work. The box said it supported Linux, but there were no drivers.
[http://www.linuxquestions.org/hcl/showproduct.php?product=3778&cat=all](http://www.linuxquestions.org/hcl/showproduct.php?product=3778&cat=all) says that it works.
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) doesn't list it, but it is under construction.

I downloaded the RT73 driver from serialmonkey and I seem to have installed it, but when I [FONT="Fixedsys"]$ sudo lshw -C network[/FONT], it doesn't mention a driver (following [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide))

[FONT="Fixedsys"]$ sudo iwconfig[/FONT] shows my rausb0 (but not much info) and Network Settings show the wireless connection with my ESSID (dhcp addressing and I've disabled security).

I can ping the localhost and the IP of the device, but not my router (Netgear DG843G).

I've followed several guides, but don't have much to show for it.

Any suggestions? Let me know what terminal output you require...

---

### Post by ajmo on 2007-07-15
Also the usb adapter doesn't light up.

Also, does using a four-port usb hub with extension cable have a deleterious effect on usb devices?

---

### Post by ajmo on 2007-07-15
I've moved this to Networking and Wireless [http://ubuntuforums.org/showthread.php?p=3025848](http://ubuntuforums.org/showthread.php?p=3025848)

---


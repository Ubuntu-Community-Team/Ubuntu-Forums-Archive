---
title: "Wireless help, please!"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by s.minor.13 on 2007-04-30
I have a D-link DWL-520 PCI card. Under the networking settings it shows up as wlan0. I try to configure it with the network ESSID and password, but with these correct settings I cannot connect to the internet. Any instruction on how to properly configure my wireless card would be greatly appreciated (or, if it's easier, a recommendationfor a common wireless card that works out of the box)

Ubuntu Edgy

---

### Post by neouser99 on 2007-04-30
you are probably going to have to use the ndiswrapper with that card, as a quick search seems to indicate. unless someone else can help you otherwise, i would head down the path of getting that to work. [here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29") is a great place to get started.

-neo

---

### Post by jfinkels on 2007-04-30
> **s.minor.13 said:**
> I have a D-link DWL-520 PCI card. Under the networking settings it shows up as wlan0. I try to configure it with the network ESSID and password, but with these correct settings I cannot connect to the internet. Any instruction on how to properly configure my wireless card would be greatly appreciated (or, if it's easier, a recommendationfor a common wireless card that works out of the box)

Ubuntu Edgy
Can you connect to your wireless router? Most of the time, it's address is something like 192.168.1.1, type that in the address bar of Firefox. If you can, then your connection is working, and we need to try something else. It may have something to do with port forwarding? I don't know...

You may first want to check if your wireless card is known to be supported. Take a look here ( [http://doc.gwos.org/index.php/D-LinkWireless](http://doc.gwos.org/index.php/D-LinkWireless) ) and ( [http://doc.gwos.org/index.php/LinuxWirelessDrivers](http://doc.gwos.org/index.php/LinuxWirelessDrivers) ). There should be some information on these pages about installing necessary drivers.

---


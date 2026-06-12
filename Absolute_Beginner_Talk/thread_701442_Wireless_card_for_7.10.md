---
title: "Wireless card for 7.10"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by armitage shanks on 2008-02-19
Hello, could someone let me know if there is a pci or usb wireless network card that works with 7.10 out of the box please. I have a friend using 7.10 who wishes to connect a HP desktop to a wireless router for internet access. Any straigtforward suggestions would be greatly appreciated.
Thanks in advance.

---

### Post by julian67 on 2008-02-19
The Safecom SWMULZ-5400 USB wireless adapter works perfectly in Ubuntu, the driver and firmware are part of the standard Ubuntu install. You plug it in, it works.

> Support WMMTM (Wi-Fi Multimedia) function.
Operating distance of up to 300 meters in free space.
2.412GHz ~ 2.484GHz unlicensed ISM frequency band.
Support USB 2.0 interface.
64/128/256-bit WEP / WPA / WPA2/WPA-PSK / WPA2-PSK and TKIP Encryption.
Support for Microsoft Windows 98SE, Me, 2000, XP, Linux and MAC.
Easy setup and configuration.

---

### Post by dstew on 2008-02-19
You have to look around a bit. For Gutsy, there are some cards listed in the [Documentation]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported"). Some cards work in Feisty but not Gutsy, and vice-versa. If a card is listed as using ndiswrapper, you will need to do a bit of work to get it going, but once it is set up it will work as well as it would with a "native" driver.

There are often more than one driver for a card. Usually, there is an open-source driver that will make the card functional, but not be able to use more advanced features. Sometimes a card maker will provide a linux-native driver (also called a restricted driver, not because it is restricted in what it can do, but because its user agreement restricts you from copying the driver and giving it away, or reverse-engineering it). With Gutsy, there is a Restricted Drivers Manager that will allow you to easily install these drivers. They cannot be provided with the base Ubuntu system, because of the software licensing required. But, once Ubuntu is installed, you are free to install them yourself.

---


---
title: "Getting WiFi to work on Joli OS 1.2"
date: 2012-02-08
forum: Any Other OS
---

### Post by Lennart5 on 2012-02-08
Heya all,

This morning I installed Joli OS on my Samsung N145 Plus Netbook, in a dual-boot with Windows 7. 
When I have my LAN-cable plugged in, everything works perfect.
However, I can't seem to be able to get WiFi to work. 
When I unplug the LAN-cable, it just shows me the 'no LAN-connection' symbol, a symbol for wireless networks doesn't even show up. 
When I take a look into the BIOS, I notice that my internal WLAN-adapter is always on, so I guess that's not the problem. 
Does anyone have experience with this?

---

### Post by sudodus on 2012-02-08
Some wifi chips and cards work out of the box in linux. The drivers are built-in in the linux kernel. If not, it might be possible to run via ndiswrapper and use the Windows driver, but it may not work reliably. If your wifi hardware is new, chances are better if you use a new version of linux. You can also try another distro, for example Ubuntu.

But first of all, you can check on the internet if your wifi chip or card is reported to work with linux, see for example

[[COLOR="Red"]_https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported_[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

---

### Post by Linuxman1900 on 2013-03-08
Try downloading the latest kernel from Ubuntu's package website. (Using Ethernet of course.) and go from there. If you get stuck spatry has a video on upgrading the kernel on Ubuntu based systems like joli os.

---


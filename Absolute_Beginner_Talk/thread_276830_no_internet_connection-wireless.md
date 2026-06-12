---
title: "no internet connection-wireless"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by jerrallan on 2006-10-13
This is the second attempt to get wireless going on my "other" computer.
The wireless device is a LinksysWUSB54g.  It works fine on Windows, and PCLinuxOS.

I installed the driver using ndiswrapper and the driver and hardware shows that is installed.  Under System>Networking> it shows wlan0.  I have the ESSID and WEP key set up.  The linksys device's link light blinks frequently showing it is seeking.  

But no internet connection!

What could the problem be?  I am wondering if there is a native firewall that is installed when I installed from the live cd?

This is my last attempt with Ubuntu 6.06 on that computer.

Working fine on the family computer connected to the router/modem.

Thank you
Jerry

---

### Post by petri on 2006-10-13
Wifi seems to not to be Ubuntus strong card(?)

Yes, Linux firewall is called iptables which are located in to the kernel. To use these iptables you can go CLI or install with Synaptic GUIs like Firestarter och Guarddog, maybe there are more but I don't know them.

About the Linksys you can take a look at his site 
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
There is a couple of versions like yours and they work with some tuning.

Hope this was some help.

---


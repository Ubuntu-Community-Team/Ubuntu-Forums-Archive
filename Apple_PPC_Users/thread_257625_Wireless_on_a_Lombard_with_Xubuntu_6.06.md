---
title: "Wireless on a Lombard with Xubuntu 6.06"
date: 2006-09-14
forum: Apple PPC Users
---

### Post by rorykingms on 2006-09-14
Cannot seem to get the wireless working on the ol' Lombard. The old Orinoco PCMCIA card that worked with an opensource driver under OS X seems completely dead: not recognized at all, and no power light on the card. (Using lshw, the PCMCIA slot lists "configuration: driver=yenta_carbus" which I take to mean that a driver is loaded for the PCMCIA slot.)

A Netgear PCMCIA card MA401 lights up, but also is not recognized.

A Linksys WUSB12 USB adapter lights up (including the Link light), and is sorta' recognized: using the command lshw, I get:

*-network:0 DISABLED[INDENT]description: Ethernet interface
physical id: 2
logical name: wlan0
capabilities: ethernet physical
configuration: broadcast=yes driver=p80211_prism2_usb driverversion=0.2.2 link=no multicast=yes[/INDENT]

But the Network GUI does not show the Linksys or the others as available. Any ideas? I have gone through the [Wireless Troubleshooting Guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check"), but admittedly it is a bit over my head. Not having wireless on a laptop is something of a deal breaker for me, so any advice would be greatly appreciated.

---


---
title: "Wireless internet?"
date: 2005-07-15
forum: Absolute Beginner Talk
---

### Post by Warren on 2005-07-15
Does anyone know how to get wireless internet connected in Ubuntu?

I have an HP pavilion ze4400 laptop, 54 Mbps Wireless LAN JAHT card (PCMCIA, I think), and a netgear WGR614 v3 router.

If your explanation requires terminal commands, please explain what the commands do.  I've only used linux for about a month and don't know a lot of the commands yet.

---

### Post by stevenyu on 2005-07-15
Firstly you will need to find out what chipset is used in your wifi unit

lspci

once you done that, have a search on the net for wifi driver supporting that chipset in linux, if you can't find it, have a look at ndiswrapper, which is a software allow you to use windows based wireless nic driver in linux.  You can find the detail installation guide on the ndiswrapper website.

---

### Post by Warren on 2005-07-15
What exactly does the lspci command do and what do I do if I can find the driver?

---

### Post by stevenyu on 2005-07-15
lspci - displays detailed information about all PCI busses and devices in the system, replacing the original /proc/pci interface.

if you are using a USB doogle, you have to look at in usb device stats under /proc

---

### Post by Warren on 2005-07-16
Thanks, but I mentioned my problem to someone else, and he redirected me to the wiki.

[https://wiki.ubuntu.com/Rt2500WirelessCardsHowTo](https://wiki.ubuntu.com/Rt2500WirelessCardsHowTo)

Hopefully if someone else has the same problem, they'll find this sooner.

I have it set up and all, but do you know how I make it connect on startup instead of waiting until I go into the networking options?

---

### Post by varunus on 2005-07-16
That same howto has a "daily use" section where they say that you can save an ssid into the gnome networking interface, and even if that's not the SSID you want to use, the card will come up on startup.  I'm not sure exactly what that means, but I do know you can add some lines to your /etc/network/interfaces to bring up your card:

#Add to the end of the file:
iface ra0 inet dhcp
wireless-essid belkin54g

This should make it come up on startup, though you may have to change SSID's.

I'd recommend taking a look at GTKWifi, which can do most things from the panel (like windows does... :) ): [http://ubuntuforums.org/showthread.php?t=49148](http://ubuntuforums.org/showthread.php?t=49148)

---

### Post by Warren on 2005-07-17
[QUOTE=varunus]That same howto has a "daily use" section where they say that you can save an ssid into the gnome networking interface, and even if that's not the SSID you want to use, the card will come up on startup.  I'm not sure exactly what that means, but I do know you can add some lines to your /etc/network/interfaces to bring up your card:

#Add to the end of the file:
iface ra0 inet dhcp
wireless-essid belkin54g

This should make it come up on startup, though you may have to change SSID's.

I'd recommend taking a look at GTKWifi, which can do most things from the panel (like windows does... :) ): [http://ubuntuforums.org/showthread.php?t=49148](http://ubuntuforums.org/showthread.php?t=49148)[/QUOTE]

Hahahahaha!  I'm such an idiot!  I just went as far as "That's it!  The driver's installed!"

I'll try what's on that howto, and if that doesn't work, I'll check out that link.

---


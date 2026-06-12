---
title: "Wireless Problems with Ubuntu 7.1"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by augie428 on 2008-02-24
I am testing out Ubuntu 7.10 by running it off of the CD-ROM but cannot get my wireless network operating. 

I have a Motorola SB5100 Surfboard Cable Modem used with a Netgear RangeMax Wireless Router - WPN824. I am using Comcast Cable as my service and also am using WPA-PSK “WPA-Personal” (TKIP) to secure my network.

I'm not sure if it is an ASDL modem but I thought I read that you need firmware to upgrade this modem type to work with Ubuntu. 

Any advice would be greatly appreciated. Thanks.

Greg:confused:

---

### Post by bobbybobington on 2008-02-24
Thats strange I think that modem should be able to work with linux just fine. Try plugging it into the Ethernet port on your computer and if it doesn't work try plugging it into your usb port. Your ethernet card might be the culprit, but I think that would be a pretty rare problem since linux is used for servers so much. But if you can isolate the problem to your ethernet card, you might as well replace it as they are widely supported and super cheap. Oh, and I'm assuming that your computer is a desktop (tower) pc?

---

### Post by Cha1n5aW on 2008-02-24
I have almost the exact same setup as you.  I had to get a firmware update for my router to get it to work properly with my surfboard.  try bobbybobbington's suggestion.  I had to shut down everything (and leave it off for at least 2 minutes), power on my cablemodem (allow lights to steady), then power on the netgear router, then power on the pc, connected via ethernet to the router, from there I had to go into [http://192.168.0.1/basic.htm]("http://192.168.0.1/basic.htm") with a web browser and manually set up the routers connection.  I found for some reason my netgear router refused to automatically believe my modem & cable conn was dhcp (auto everything) with the setup wizard.  Those netgear routers require latest firmware to work properly & reliably with those surfboard docsis modems.  Once you have a wired connection with the router working, and everything is online, then I would start by setting up wireless on router and connecting to that network.  If you have trouble connecting your wifi with gnome's network manager, you may want to try this thread..
[http://ubuntuforums.org/showthread.php?t=684495]("http://ubuntuforums.org/showthread.php?t=684495")
I have to set up my wifi devices manually, for some reason gnome's nm-applet doesn't seem to work well with encrypted wireless.

I hope this all helps..
- Shawn

---


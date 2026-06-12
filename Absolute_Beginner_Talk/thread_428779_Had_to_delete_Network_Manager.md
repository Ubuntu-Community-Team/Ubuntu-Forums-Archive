---
title: "Had to delete Network Manager"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by gerrymoth on 2007-04-30
I have been running Ubuntu fine for the last few weeks until today when network manager just refused to connect to the wireless network, so I removed it with every intention to install it again, but I've connected manual using System/Network and it seems to connect quicker.

What are alternatives to Network Manager? Is Wifi Radar a similar application?

I use at least 3 different wifi connections, 2 are WEP and 1 is WPA.

---

### Post by starcraft.man on 2007-04-30
Just a note to begin before I say anything else but I strongly recommend you stop using WEP. WEP has been badly BROKEN, and by that I mean that there are now automatic tools (that even a complete noob could use) and proof of concept programs that will crack ANY wep encryption in under 2 minutes, most of the time under 1. Unless its vital, you really should move to WPA or use a VPN on your WEP connection. Disabling SSID and Enabling Mac adress filtering really don't offer any protection either. Just putting it out there, I wouldn't want your network/computer to be hacked.

As for network manager, I haven't had or heard of many problems. Maybe there was simply a problem with the install, perhaps it would work better this time. Haven't used wifi radar so can't commit on that. I don't think if network-manager is working that it should cause any delay at all at least in my experience.

---

### Post by gerrymoth on 2007-04-30
Thanks for the quick reply.

The WPA connection I use is my home router, the 2 WEP connections are when I'm away working and connect to the hotels wifi connection.

---

### Post by starcraft.man on 2007-04-30
> **gerrymoth said:**
> Thanks for the quick reply.

The WPA connection I use is my home router, the 2 WEP connections are when I'm away working and connect to the hotels wifi connection.

Oh boy... a WEP line at a hotel, man thats really not secure. I know of cases where hackers and other people just go to a hotel and plug into the network (usually it is one big network all interconnected) and they can easily spy on everything you do by monitoring all packets going in and out. You really should invest or set up a VPN solution for when you are on the go. I mean, I read a serious security article where one journalist just set up her labtop to read all packets on the hotels network (was all connected together) and after two hours she came back and had adresses, credit card numbers a whole assortment of info. It is that easy and people do that. >.>

Oh and I did a bit of research, you might wanna look at these alternatives.

[Managers.]("http://linuxappfinder.com/internetandnetworking/configuration")

[Wireless.]("http://linuxappfinder.com/internetandnetworking/wireless")

There should be a program available that works for you.

---

### Post by gerrymoth on 2007-05-01
I did a fresh install of Ubuntu last night and Network Manager can see all available network, but refuses to connect to any, just comes back for me to put the password in again.

Installed Wifi Radar and can connect no problem.

How do I setup  a VPN?

---

### Post by HyperY2K on 2007-05-01
How can I configure Network Manager to use a static IP for a WLAN?

---


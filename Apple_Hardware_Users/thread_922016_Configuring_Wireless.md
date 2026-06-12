---
title: "Configuring Wireless"
date: 2008-09-16
forum: Apple Hardware Users
---

### Post by ericks13 on 2008-09-16
I recently moved back to my college and we have a new wireless network set up in the residential buildings.  I managed to set up wireless on my Leopard and XP partitions, but I'm having difficulty doing so with Ubuntu (i.e. I'm clueless as to what I'm supposed to do).  Normally you would type in "ifconfig" in a terminal and send the output to Network Services and they'd configure it for you, but my computer is already registered as a Mac OS X machine.  The guy from Network Services told me: "To connect to RowanWPA, you need to configure your wireless for EPA Enterprise, key automatically provided, PEAP, TKIP and MSCHAPv2. Use your Rowan username and password and leave Domain blank if it's offered." Any clue how I'm supposed to do this?  I checked in Network Preferences for a wireless option, but all I found was, "enable roaming mode".  Help would be greatly appreciated.  Thanks.

---

### Post by cyberdork33 on 2008-09-17
You are going to have to use network-manager (or some other client) that supports PEAP first of all. This is "Enterprise-grade" wireless security so a lot of home user type tools will not have those options. You could also checkout wicd as I think it supports this too.

Either way, since this is really not a problem related to the fact that you have a Mac, you might check in the Wireless & Networking forum for more detailed instruction.

---


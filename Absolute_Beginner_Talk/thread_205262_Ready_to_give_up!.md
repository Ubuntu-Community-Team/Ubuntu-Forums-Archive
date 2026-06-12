---
title: "Ready to give up!"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by drifternel on 2006-06-28
Try as I might cannot get dapper to install properly.
Ive tried to upgrade from within breezy, Ive tried the live cd install as well as the alternate cd. Same problems.
The usb and sound issues I could live with (and use the forum to work out a fix) but it wont recognise my ethernet (or usb) connection to a cable modem which makes it a total hassle to track down advice.

Two things before I give up!
Is there a foolproof way of getting an internet connection?
Is it worth me waiting for the next version of ubuntu and try then?

Knoppix and PclinuxOS (and win xp)work ok on my system so its an ubuntu thing it seems.
Thanks
](*,)

---

### Post by Apple 101 on 2006-06-28
How does your cable modem assign IP addresses?  Statically or by DHCP service?  Check Windows or any other operating system if you are not sure.  If it is a static addressing system, write the settings down, and input them into Ubuntu.

---

### Post by taurus on 2006-06-28
If Knoppix and PCLinuxOS work with your machine but not Ubuntu, then you should install either one of them.  Even though Ubuntu is good, it doesn't always work for everybody so whichever Linux distro works for you, use it.  There is nothing wrong with it as long as you don't use that Windows crap!  ;)

---

### Post by drifternel on 2006-06-28
Thanks apple
I'm at work so can respond but computer in question is at home unfortunately.
er..mm. no idea to be honest.
How do I find out?
Its a cable modem from NTL (in the uk).
It has an ethernet card (RJ 45 wired) connection ie not wireless
Breezy connected fine when it was a usb connection but not now its an ethernet card. Dapper disables my systems usb so other than just staying with breezy on usb (and not upgrading to dapper) Im stuck!

If you can tell me the info I need to collect I post it onto the forum latter.
Many thanks

---

### Post by Apple 101 on 2006-06-28
Just load Windows XP for these steps.
1. Start --> My Network Places --> My Network Connections (or any other route you want to take).
2. Right-click your LAN connection (most likely called 'Local Area Connection') --> Status --> Support.
3. The information will tell you whether the IP is DHCP assigned or manually assigned.  If manually assigned, the information is also provided.

---

### Post by richbarna on 2006-06-28
This site covers your modem for Mac and Windows, but gives some uesful information :-
[http://homepage.ntlworld.com/robin.d.h.walker/cmtips/]("http://homepage.ntlworld.com/robin.d.h.walker/cmtips/")

I also found this about ntl :-

> NTL also do high speed access with cable modem but their customer service was said to be poor due to cut backs. They have now merged with Telewest.

I had some problems moving cable modem from machine to machine, until it was explained that I had release lease on first machine ( run -> winipcfg on win98) , turn off cable modem and wait up to a few hours before setting up on new NIC card. Blueyonder has now dropped requirement to register MAC address of card with ISP.

A cable modem can be used on different machines so long as 1) the mac address of each machine's NIC card has been registered with ISP (if required) and 2) when moving the modem between machines the IP address is released from the first machine before being renewed on the second. You may find it necessary also to power down the modem for a period of time if it does not learn the new NIC card address (and thus acquire a new IP address) - this time could be anywhere from a few minutes to a couple of hours.

for interest check out your cable modem config at: [http://192.168.100.1](http://192.168.100.1) ( but take care here really you don't need to mess with settings here)

And here is a good ethernet guide :-

[http://en.tldp.org/HOWTO/Ethernet-HOWTO.html]("http://en.tldp.org/HOWTO/Ethernet-HOWTO.html")

---

### Post by drifternel on 2006-06-28
Thanks guys for the info
excellent forums.
by the way didnt mean
'Knoppix and PclinuxOS (and win xp)work ok on my system so its an ubuntu thing it seems'
as a critisism of ubuntu! - just meant that I know its not my modem/ethernet card etc.
Doesnt read too good tho - sorry!

---

### Post by richbarna on 2006-06-28
[QUOTE=drifternel]Thanks guys for the info
excellent forums.
by the way didnt mean
'Knoppix and PclinuxOS (and win xp)work ok on my system so its an ubuntu thing it seems'
as a critisism of ubuntu! - just meant that I know its not my modem/ethernet card etc.
Doesnt read too good tho - sorry![/QUOTE]

No problem, Many people here dual-boot with Windows, and I personally have about thirty other Linux distros that I play with.
These things happen with different OS's.

Post back if you still need more help :)

---


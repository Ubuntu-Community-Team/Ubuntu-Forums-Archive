---
title: "Can't Get Online, part3"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by metsfan47 on 2007-08-25
Hello all,

I want to thank anyone for their help, but I still can't get online.  I purchased a new NIC but still can't, so that wasn't the problem.  I guess I have to install the libc development package to install my network drivers, but unfortunately I don't have a way of getting that PC online.  Someone recomended an old dial-up modem and using some free dial up service (ie, peoplepc)  Unfortunately I don't have a landline phone, however I will be visiting my parents in a few weeks who do, maybe I could take it with me and try then.  In the meantime, does anyone have any other ideas?  

It says I'm connected to a wired connection, but my IP, Subnet, etc are all 0.0.0.0

Please, any advice would be appreciated, I'm getting desperate!

-Aaron

---

### Post by Spr0k3t on 2007-08-25
I don't know what the other suggestions included.  Perhaps it would be good to link to the other two parts of your request for help in the original post.

My suggestion, try a live disc... not just Ubuntu, but other distros as well.  Also, details on the card you purchased would help as well (lspci).

---

### Post by ravenwere on 2007-08-25
Hi Aaron,

Don't act too hastily. There is nothing to indicate (someone may want to correct me) that there is any problem with your NIC either the earlier onboard chip or the one you purchased. If network manager indicates that you have a wired connection then I cant see you have a driver problem.

I am tending to think there is a cabling or modem configuration problem. Be careful scaring off your internet providers helpdesk but telling them you use linux. What you want to know is how they configure their network.

IP addresses are assigned usually automatically by DHCP with your modem acting as the DHCP server.

Have you rebooted your cable modem yet. I have to reboot my ADSL modem to restore the DHCP service two or three times a year. Before you reboot the modem power down the PC and leave that off while you reboot the cable modem. I would also suggest you disconnect the power to the cable modem in the reboot process. Once the cable modem is rebooted give it another 30 seconds then power up the PC. And finally type a website address in the browser to kickstart the interface (if needed).

You may also want to get your internet provider to tell you what IP address they default their modems to. eg my provider gives a default 10.0.0.138 This will possibly not be the address your provider uses though.

Right click on your wired connection icon select manual configuration and after your password is entered the first table should show your eth0 available network interface.
this should read something like:

eth0 + IP address + Protocol DHCP + State enabled + Comment Ethernet Network Device

Check DHCP is active. Check the state is enabled.

I use KDE so your Gnome network manager may be slightly different.

Under the routes tab you want a default gateway setting that points to your cable modem IP address. In my case this is 10.0.0.138. Likewise for the DNS tab.

I will check your previous posts to see if there is any other clue.

---

### Post by gb5757870 on 2007-08-26
Hi, I seem to have the same problem as metsfan47. I have followed all suggestions too but no joy. The odd thing is that it was fine until recently. Now, using a live CD and in fact re-installing still no connection but I can get a connection on windows as I dual-boot.

metsfan47, have you had any luck?

---

### Post by NotonyourNelly on 2007-08-26
Same here, Windows XP has network but not Ubuntu 7.04. Again recent problem in last 5 days.
Tried fixed IP address but no joy - seems from router LEDs that network card/cable isn't seen at all!

---

### Post by por100pre1 on 2007-08-26
Hey guys, while using xp, have you unticked the  "Allow this device to bring the computer out of standby" option for your network cards? :-k Try to tick it.

---

### Post by NotonyourNelly on 2007-08-26
> **por100pre1 said:**
> Hey guys, while using xp, have you unticked the  "Allow this device to bring the computer out of standby" option for your network cards? :-k Try to tick it.

Not tried this tip so far, but will try it in a second - I have to reboot into Ubuntu with no internet...so will set up other machine and use them side by side.

BTW I close down everything PC, router etc when they are not being used plus the connection on the router is fine using the same PC and router in Windows....I wonder if a recent update has caused this?

Is there any way to reset all network connection to clear any changes I might have made?

thanks
N

---

### Post by metsfan47 on 2007-08-28
I don't know if this will help anyone else, but I think I figured something out.

I have one modem to hook to the internet via Comcast and I've been alternately hooking up the PC I built with Ubuntu 7.04 and an old machine running Windows XP.  The XP machine always got online fine, but Ubuntu never would.  I have no idea why, but I hooked up the Ubuntu machine, unplugged my modem for several minutes to get a new IP address, rebooted Ubuntu, and POOF, I'm online!!

This literally JUST happened, so I really have no idea if this will work in the long run or what.  I hope it does.  Does anyone have any idea WHY this worked?  (out of curosity?)

-Aaron

---

### Post by ravenwere on 2007-08-28
See the following:
[http://homepage.ntlworld.com/robin.d.h.walker/cmtips/dhcp.html](http://homepage.ntlworld.com/robin.d.h.walker/cmtips/dhcp.html)

Quote:
 The DHCP server identifies you by the unique MAC address of your PC's network interface card connected to the cable modem, and it maintains a record of which IP addresses it has issued to which MAC addresses.

In other words each network card has a unique MAC address. If your cable modem originally linked the XP computer NIC MAC address to the IP address in its tables whenever you plug in the Ubuntu PC (which has a different MAC address) it would want to assign a different IP address assuming it had a range of IP addresses to allocate.If it doesn't then sorry no internet connection. The simple solution is to reboot the cable modem which would then assign the IP address to the MAC address of the Ubuntu PC.(poof) you now have internet.

---


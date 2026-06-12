---
title: "Static IP Address"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by drowner on 2006-04-18
Could someone walk me through the steps to make my ip address static?

Will this change affect XP? ie, is the change made in Ubuntu or in the router?

ADSL 2+ Zyxel 600 router, :)

---

### Post by ds[de] on 2006-04-18
If your provider equipped you with a dynamic IP (which is common) then there's nothing you can do about it, except using a service like dyndns.org, which will assign a name like drowner.dyndns.org to your IP address and update it every time you re-login (i.e. your IP changes).

If you are however talking about your local IP address, and you don't want your LAN to be using DHCP, then you'll have to change that in your router's settings.

Regards,
ds[de]


PS: I'm not sure if dyndns.org offers a tool for linux (which you'll need so your "hostname" is updated to your dynamic IP), but there may be others that do so.

PPS: I just checked, and they do offer two clients for linux/unix, which can be found here:
[http://www.dyndns.com/support/clients/unix.html](http://www.dyndns.com/support/clients/unix.html)

Good luck.

---

### Post by 5-HT on 2006-04-18
As ds[de] mentioned, this would need to be reflected in the router's configuration (usually a web-interface). 

Most commonly, you could opt for the router to send out specific IPs filtered by MAC address.
If you went this way, you can leave Ubuntu set for DHCP, and windows will be affected as well (as the change is being done at the router level).

You could also probably configure Ubuntu for a static IP (the one the router will be giving out), but it is not necessary.
If you wanted to configure Ubuntu for a static address, there are two options:

i)  In GNOME: system > administration > networking
I don't know about KDE, but something similar should be somewhere in the menus


ii) Edit /etc/network/interfaces 
For syntax see: man interfaces

Hope that helps.

---

### Post by drowner on 2006-04-18
Wow im confused :D

i was looking at PortForward, and it had a noob guide to doing it in XP.... basically, telling windows to use THIS dns, not obtain it automatically

[http://www.portforward.com/networking/winxp-tcpip.jpg](http://www.portforward.com/networking/winxp-tcpip.jpg)

Where can i change these settings in Ubuntu? sys>Admin>networking?

---

### Post by 5-HT on 2006-04-19
[quote=drowner]Where can i change these settings in Ubuntu? sys>Admin>networking?[/quote]

Yup.

---

### Post by dickohead on 2006-04-19
Go to System - Administration - Networking and change your eth0 interface from Dynamic to Static and assign yourself the IP address of 192.168.1.101 with a subnet mask of 255.255.255.0, which might be your private IP range. See what kind of IP your router is giving you, ie: 192.168.1.100, or 10.0.0.100 and then make your IP address something OUTSIDE of the range that your router will issue you via DHCP, or set the range to something like 192.168.1.100-192.168.1.254 then you can assign anything from .1 to .99 for static use, you'll also need to specify the default gateway, which will be the address if your router, probably 192.168.1.1 or 10.0.0.1, or similar!

---

### Post by CameronCalver on 2006-05-19
how do you find out your routers ip

---

### Post by jorn on 2006-05-19
If you still have got the manual it probably is mentioned there.
Or open your browser and type maybe 192.168.1.1 or 10.0.0.1
What is the name of your router?

---

### Post by CameronCalver on 2006-05-19
its a zyxel prestiege 600 and when i type 192.168.1.1 it just says waiting but when i type in 192.168.1.0 itsays error so it must be 192.168.1.1 so if it is in that can you help me fill these out
Ip address i want my main comp to be 192.168.0.100 and secondary to be 192.168.0.101
Subnet Mask
Gateway Address

---

### Post by jorn on 2006-05-19
Main pc:
IP address          192.168.1.100
Subnet mask       255.255.255.0
Gateway address 192.168.1.1

Sec pc:
IP address          192.168.1.101
Subnet mask       255.255.255.0
Gateway address 192.168.1.1
See if that works or have you already done it?

---

### Post by Iowan on 2006-05-19
CameronCalver:
Does [THIS]("http://www.portforward.com/english/routers/port_forwarding/ZyXEL/Prestige600/default.htm") help any?

---

### Post by CameronCalver on 2006-05-19
jorn it worked thanks everyone for helping me

---


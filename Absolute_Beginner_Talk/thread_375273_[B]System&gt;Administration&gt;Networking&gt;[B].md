---
title: "[B]System&gt;Administration&gt;Networking&gt;???[/B]"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by perfidious_alban on 2007-03-03
I'm sitting here **again** with a totally clean installation of 6.06 on my other machine, an old IBM T21 laptop with PCMCIA card (a D-Link G630 this time which I'm assured will work with the correct drivers). 

Unfortunately the laptop does **not** have an ethernet connection so hard wiring it to get things 'up and running' then switching to wireless is not an option open to me.

I've been here (several times) before  and it all usually goes pear shaped when I get to the point of connecting to my wireless network using, as I have always done with Win networks, fixed IP addresses.

ie I'm past the : Installed ndis drivers: <name of driver>  driver present, hardware present bit, I've got rid of IPv6 (and blacklisted it) and I'm all set to connect.

So **before** I start this time, can someone confirm that I'm putting the correct entries in the correct fields in Network settings and haven't missed anything or got something totally wrong ?

What goes (if anything) in 'Location' ?

Default gateway device is : wlan0, which looks to be OK.

On the various tabs.

_Connection_
Network Name = usr9106 - USR9106 Wireless router
Key type = Hexadecimal
WEP = <blank>	 
Configuration = Static IP Address
IP Address = 192.168.xx.dd - T21 Laptop with Ubuntu install
Subnet mask =  255.255.255.0
Gateway address	192.168.xx.aa - USR9106 Wireless router

_General_
Hostname = tango-t21 - T21 Laptop with Ubuntu install 
Domain Name = 192.168.xx.dd - T21 Laptop with Ubuntu install

_DNS_
DNS Servers	192.168.xx.aa - USR9106 Wireless router
Search Domains	<blank>

_Hosts_
192.168.xx.aa	usr9106
192.168.xx.dd	tango-t21
127.0.0.1	localhost tango-t21
All entries relating to Ipv6 have been removed

I know that after all that I need to edit several files such as '/etc/network/interfaces' and the '/etc/modules' file but I'll cross that bridge when I get to it.

Any help appreciated.

---

### Post by zvacet on 2007-03-03
```
sudo pppoeconf
```

---

### Post by perfidious_alban on 2007-03-03
Thanks for replying.

I get a not connected message and it tells me to 'check network and modem cables'

on a wireless LAN ???????????

---

### Post by benblout on 2007-03-15
From a terminal, could you type 
iwconfig
and 
ifconfig
and post the results?

-Ben

---


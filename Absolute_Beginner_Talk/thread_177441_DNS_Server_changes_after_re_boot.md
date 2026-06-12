---
title: "DNS Server changes after re boot"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by ahlandberg on 2006-05-16
I have a router which runs DHCP.

In my 'Network Settings' I entered DNS Server: 192.168.0.1

I can now connect to the internet and all works fine.

After I re boot the computer, the DNS Server address has changed to 192.168.1.1

I can now ping any address but cannot connect to the internet via Firefox.

Please help!

Cheers, Anders

---

### Post by kencoe on 2006-05-16
You may have already tried this, but did you try to ping [www.yahoo.com](www.yahoo.com) to see the response?

---

### Post by shanepardue on 2006-10-17
my dns disappears after reboot every time. once i'm booted, i have to change the dns server and it works. let me know if you found a solution. thanks!

---

### Post by starsky on 2006-10-17
> **shanepardue said:**
> my dns disappears after reboot every time. once i'm booted, i have to change the dns server and it works. let me know if you found a solution. thanks!

I am pretty sure it's the resolvconf (man resolvconf). If you have it installed. Disable resolvconf and dnsmasq if you are on single user network.

```

sudo /etc/init.d/resolvconf stop && sudo /etc/init.d/dnsmasq stop

```

insert your ISP's Primary and secondary DNS address in /etc/resolv.conf. 

Then wait for about 4-5 secs and then do
```

sudo dhclient3 <your_ethernet_device>

```

Hope that helps.

---

### Post by Iowan on 2006-10-17
Your router probably has the 192.168.1.1 address as it's DNS 
Inside your **/etc/dhcp3/dhclient.conf** file are lines similar to:
```
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers,
        netbios-name-servers, netbios-scope;
```
Removing the **domain-name-servers** and embedding your choice in the **prepend** line (remove the "#") should (hopefully) prevent the router from overriding your settings.
  There are several other threads with similar problems - some have more detailed solutions (including editing **/etc/dhcp3/dhclient-enter-hooks.d**) 
 **SEARCH** for **dns reboot**.
[http://www.ubuntuforums.org/showthread.php?t=188551&highlight=dns+reboot]("http://www.ubuntuforums.org/showthread.php?t=188551&highlight=dns+reboot")
Here's an especially involved one.

---

### Post by shanepardue on 2006-10-17
i was hoping this would work, it seemed promising, but sure enough after reboot, i'm back on a blank dns. here's the output i got after i typed the last command (sudo dhclient eth0)

```
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:17:31:0c:99:eb
Sending on   LPF/eth0/00:17:31:0c:99:eb
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.101 -- renewal in 78705 seconds.

```

and Iowan, thanks for the attempt also..i'll definitely research this..i'm kinda bummed this is an issue. this is quite an annoyance!

just a note..my domain name doesn't stick either after reboot.

---

### Post by shanepardue on 2006-10-17
here's the fix!! thanks for the link iowan!!

[http://www.ubuntuforums.org/showpost.php?p=1565472&postcount=33](http://www.ubuntuforums.org/showpost.php?p=1565472&postcount=33)

---


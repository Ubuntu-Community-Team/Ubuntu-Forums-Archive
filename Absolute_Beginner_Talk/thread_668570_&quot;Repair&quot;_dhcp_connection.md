---
title: "&quot;Repair&quot; dhcp connection"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by Scrier on 2008-01-15
Hi, 

I have a swedish cablenet isp called comhem distributing their service through DHCP. On this Ubuntu server / router / whatnot machine I am sharing it with the built in gigabit interface and I take the cable isp on an dlink usb network card. 

The problem I get is that the connection dies after around 24 hours or more and I have to reboot this ubuntu machine to get it to work again. ifdown / ifup doesn't work and I don't know any other way to recieve a new ip in ubuntu like ipconfig / release, ipconfig /renew or right click repair in windows. I wonder if there is any other way to do this without restarting the machine.

// Andreas

---

### Post by Cypher on 2008-01-15
How about
```

sudo /etc/init.d/network restart

```
This will cause the DHCP-Client daemon to restart and it should re-do the whole DHCP process..

---

### Post by fatality_uk on 2008-01-15
> **Cypher said:**
> How about
```

sudo /etc/init.d/network restart

```
This will cause the DHCP-Client daemon to restart and it should re-do the whole DHCP process..

In addition, [COLOR="Red"]**crontab**[/COLOR] it :)
If it's the ISP that's forcing your connection to go down after a specified time period, you can use this to bring it back up.
See here for details. [Link]("http://ubuntuforums.org/showthread.php?t=102626")

---

### Post by rbc on 2008-01-15
I am not having this problem, but wanted the knowledge in case it ever happened......I do not have a file called "network" in /etc/init.d. I have a file called "networking". Same thing?

---

### Post by Scrier on 2008-01-19
Well it took a while but this niight it died and this is what i got when I tried to restart the network:
> scrier@Backend:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth1.pid with pid 31262
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:80:c8:39:78:c8
Sending on   LPF/eth1/00:80:c8:39:78:c8
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 10.125.1.11 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
SIOCSIFFLAGS: Cannot send after transport endpoint shutdown
SIOCSIFFLAGS: Cannot send after transport endpoint shutdown
There is already a pid file /var/run/dhclient.eth1.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFFLAGS: Cannot send after transport endpoint shutdown
SIOCSIFFLAGS: Cannot send after transport endpoint shutdown
Listening on LPF/eth1/00:80:c8:39:78:c8
Sending on   LPF/eth1/00:80:c8:39:78:c8
Sending on   Socket/fallback
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
RTNETLINK answers: Network is down
run-parts: /etc/network/if-up.d/avahi-autoipd exited with return code 2
                                                                         [ OK ]


Maybe it is too late now and I need to run the command earlier?

---


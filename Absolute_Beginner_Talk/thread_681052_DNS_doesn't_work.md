---
title: "DNS doesn't work"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by Imsdal on 2008-01-28
I can't get DNS to work from a standard Gutsy install. It has a wreless network card that works, and ping works to extrenal ip addresses, so it's just the name lookup that doesn't work.

The router (NETGEAR WGT624) is configured to get DNS address from my ISP. My Vista machine connects just fine, so that seems to work.

In Network settings, the DNS server is 198.172.0.1 (the router address) - is that correct or will it falsely believe that the router is the actual DNS server? Removing the DNS entry completely didn't work either, unsurprisingly.

The network uses DHCP, and it gets the correct local ip address from the router.

What now?

---

### Post by Iowan on 2008-01-28
Check  [this thread]("http://ubuntuforums.org/showthread.php?t=678794").  In brief, you're probably gonna need to edit /etc/dhcp3/client.conf file.  I suspect the router is perceived as DNS server.  You could check the Vista machine settings for "working" setting.   More details available on request.

---

### Post by erfahren on 2008-01-28
> **Iowan said:**
> Check  [this thread]("http://ubuntuforums.org/showthread.php?t=678794").  In brief, you're probably gonna need to edit /etc/dhcp3/client.conf file.  I suspect the router is perceived as DNS server.  You could check the Vista machine settings for "working" setting.   More details available on request.
I was going to suggest the same:
[http://ubuntuforums.org/showthread.php?t=511486](http://ubuntuforums.org/showthread.php?t=511486)
[http://news.softpedia.com/news/DNS-Hacks-for-Faster-Web-Browsing-55699.shtml](http://news.softpedia.com/news/DNS-Hacks-for-Faster-Web-Browsing-55699.shtml)

---

### Post by Imsdal on 2008-01-28
I looked at the threads suggested, and followed the instructions. The files now look like the examples with entries pointing to OpenDNS, and the GUI agrees. Same results, though. Can ping by ip, can't ping by name. What can I try next?

Also, using OpenDNS instead of my ISP's seems to be quite a bit of a workaround. The only problem wth my ISP's DNS servers is that my machine can't (won't) reach them, not that they are broken in any way.

---

### Post by bumanie on 2008-01-28
I suspect you are a victim of the ipv6 problem that has plagued some others in gutsy. Suggest you blaclist ipv6 and see if that makes a difference.
> gksudo gedit /etc/modprobe.d/blacklist
at the end of the gedit list type
blacklist ipv6. 
Save and reboot.
Hopefully this will get you connected.

---

### Post by Imsdal on 2008-01-29
I tried blcklisting ipv6 as well. Same results as before, unfortunately.

Is there anything else to try?

---

### Post by erfahren on 2008-01-29
I came across this article - you might want to look at it
[http://www.ventanazul.com/webzine/articles/cannot-access-websites-ubuntu-gutsy-gibbon](http://www.ventanazul.com/webzine/articles/cannot-access-websites-ubuntu-gutsy-gibbon)

EDIT - I apologize - I reread your first post. It's probably unrelated - sorry

---

### Post by Iowan on 2008-01-29
Did you try prepending your ISP's DNS servers' addresses?
Is Gutsy's DNS still the router address?

---

### Post by Imsdal on 2008-01-29
> **Iowan said:**
> Did you try prepending your ISP's DNS servers' addresses?

I'm not at home now, so I can't experiment, but I don't even know the address of the DNS servers of my ISP. My router is just configured to get everything automatically from the ISP. This works in Vista, and it did work in Feisty. But I'll see if I can find the address out and add that.

> Is Gutsy's DNS still the router address?

I tried both:
<OpenDNS address 1>
<OpenDNS address 2>
198.172.0.1

and just:
<OpenDNS address 1>
<OpenDNS address 2>

No difference, as far as I could tell.

---

### Post by Imsdal on 2008-01-29
OK, now I had the time to try this. Changig DNS servers to those provided by my ISP gave the exact same results as before.

However, restarting the network with sudo /etc/init.d/networking restart gave the following output. I can't interpret it, buu it does look suspect to me.
```

 * Reconfiguring network interfaces...       [80G There is already a pid file /var/run/dhclient.ath0.pid with pid 6750
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:0f:b5:81:1a:bf
Sending on   LPF/ath0/00:0f:b5:81:1a:bf
Sending on   Socket/fallback
DHCPRELEASE on ath0 to 198.172.0.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 6831
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:a0:cc:64:6d:87
Sending on   LPF/eth0/00:a0:cc:64:6d:87
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 198.172.0.1 port 67
There is already a pid file /var/run/dhclient.ath0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:0f:b5:81:1a:bf
Sending on   LPF/ath0/00:0f:b5:81:1a:bf
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
ip length 314 disagrees with bytes received 534.
accepting packet with data after udp payload.
DHCPOFFER from 198.172.0.1
DHCPREQUEST on ath0 to 255.255.255.255 port 67
ip length 314 disagrees with bytes received 534.
accepting packet with data after udp payload.
DHCPACK from 198.172.0.1
bound to 198.172.0.6 -- renewal in 945839657 seconds.
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:a0:cc:64:6d:87
Sending on   LPF/eth0/00:a0:cc:64:6d:87
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

[74G[ OK ]

```

Any clues  from this?

---


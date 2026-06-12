---
title: "&quot;ipconfig&quot; on linux?"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by J-Gaming on 2006-06-06
I was just wondering, how to make these things on linux?
like on windows you do:

ipconfig /flushdns - ?
ipconfig /release - dhclient -r
ipconfig /renew - dhclient -1 (?)

---

### Post by slakkie on 2006-06-06
For /release and /renew I would point to the dhclient (man dhclient).
And for the flushdns.. I have no clue. I found a page which describes it, however, I did not see the process running which they mention in the article:

[http://www.tech-faq.com/flush-dns.shtml](http://www.tech-faq.com/flush-dns.shtml)

---

### Post by ctgray on 2006-06-06
ipconfig /release = sudo ifdown <network interface e.g. eth0>
ipconfig /renew = sudo ifdown <network interface e.g. eth0> && sudo ifup <network interface e.g. eth0>

I'm sure that's not the most correct way but it's how i do it.

---

### Post by J-Gaming on 2006-06-06
[QUOTE=ctgray]ipconfig /release = sudo ifdown <network interface e.g. eth0>
ipconfig /renew = sudo ifdown <network interface e.g. eth0> && sudo ifup <network interface e.g. eth0>

I'm sure that's not the most correct way but it's how i do it.[/QUOTE]
This is what I get:

> Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:10:dc:cf:03:b6
Sending on   LPF/eth0/00:10:dc:cf:03:b6
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:10:dc:cf:03:b6
Sending on   LPF/eth0/00:10:dc:cf:03:b6
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 192.168.0.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.171 -- **[COLOR="Red"]renewal in 279919 seconds.[/COLOR]**


---

### Post by steve.horsley on 2006-06-06
That's working then. Good.

A better way is:
**sudo dhclient -r eth0**
**sudo dhclient eth0**

---

### Post by J-Gaming on 2006-06-06
[QUOTE=steve.horsley]That's working then. Good.

A better way is:
**sudo dhclient -r eth0**
**sudo dhclient eth0**[/QUOTE]

After I've done that I need to restart computer? modem? router?
EDIT: and I still need to know how to flush DNS?

Edit: Ok, I got IP changed, but I needed to re-connect from router - is it possible to make it change IP from terminal only?

---

### Post by elemental666 on 2006-06-06
you shouldn't have to reboot, bringing the interface up and down will suffice for chanigng your ip, if your ip is being cached its most likely not on your system but the routers, switches, servers you travel through...

The only way I know to clear DNS Resolver Cache on linux is if there is a dns daemon of somesort running, ie. nscd or somesuch...

Individual applications may cache dns resolution to some degree (think history in a web browser).  

however, /etc/host.conf can be configured to go through BIND before looking through host files... 

my original /etc/host.conf
```
cat /etc/host.conf
order hosts,bind
multi on

```

change ther order line to...
```
order bind,hosts
```

but unless the site your trying to purge is in your hosts file then that won't help...I don't think...

are you running a daemon like ncsd?

edit: I just found a script, /etc/init.d/dns-clean , that appears to clear up the resolver cache.  It does so before ppp is brought up during a system boot.  Looking through the script it calls /etc/ppp/ip-down.d/0dns-down.  I've copied a few lines of note:

```
# 0dns-down takes down what 0dns-up sets up.
...
# Are we being called by dns-clean?  If so fix up /etc/resolv.conf
# and clean out /var/cache/pppconfig.
...
# Tell nscd about what we've done.

/usr/sbin/nscd -i hosts || exit 0

```

I don't have nscd running by default, so I don't think there is a cache to clean.  Are you having a specific problem or you just trying to figure it out?


PS. Thanks, I learned alot tinkering with this thread...

---


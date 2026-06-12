---
title: "Network stopped working after restart"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by rubbsdecvik on 2007-02-19
So, I'm not sure what is happening, but I have recently reinstalled Edgy.  I had everything working well.

Then yesterday I turned my computer on, and I couldn't use the internet.  I tried to get to my router, but it won't even connect to that.

I tried to change to a static IP in the routers range, disabling and re-enabling the network using System->Administration->networking.

I checked my router, and it seems to work.  I think it is even trying to give the computer an address (it is set for DHCP), but I don't think my Edgy machine is getting it.

here is my interfaces file.  

```
/etc/network$ cat interfaces
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth0
iface eth0 inet dhcp

```

Can anyone give me some other ideas? 

Thanks a lot!

---

### Post by annda on 2007-02-19
are you using wired or wireless internet?

what is the output of ifconfig?

---

### Post by rubbsdecvik on 2007-02-19
Sorry, it would be a wired connection.  

Here is the ifconfig output 

```
eth0      Link encap:Ethernet  HWaddr 00:11:09:CE:8D:E5  
          inet6 addr: fe80::211:9ff:fece:8de5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:275 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:120 (120.0 b)  TX bytes:80167 (78.2 KiB)
          Interrupt:193 Base address:0xef00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1738 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1738 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:131504 (128.4 KiB)  TX bytes:131504 (128.4 KiB)

```

Thanks

---

### Post by annda on 2007-02-19
i suppose you will still get no IP from the router after manually resetting the connection by

```
sudo ifdown eth0
sudo ifup eth0
```

but there is no harm in trying (helped me once).

i hope someone here has better ideas.

---

### Post by Rippey on 2007-02-19
try "sudo dhclient eth0"
that should get you an ipadress from the dhcp server

---

### Post by rubbsdecvik on 2007-02-19
you were correct... it didn't help... but in case someone else is reading here is the output I got.


```
: sudo ifdown eth0

There is already a pid file /var/run/dhclient.eth0.pid with pid 8464
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:11:09:ce:8d:e5
Sending on   LPF/eth0/00:11:09:ce:8d:e5
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.

:/etc/network$ sudo ifup eth0

There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:11:09:ce:8d:e5
Sending on   LPF/eth0/00:11:09:ce:8d:e5
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

I got a similar thing by doing ```
sudo dhclient eth0
```

I wonder if it's something weird with my router?

I'm open to anything really.

Thanks.

---

### Post by rubbsdecvik on 2007-02-19
bump

---

### Post by rubbsdecvik on 2007-02-19
bump again.

I would appreciate any input anyone can give me

---

### Post by rubbsdecvik on 2007-02-19
nevermind... i think it's with my router... a live CD doesn't work with it either.

Thanks anyway!

---

### Post by pgilmon on 2007-02-19
Have you set the networking configuration to DHCP again? You said that you configured a static IP...

---

### Post by annda on 2007-02-19
on second thought: can't you even access your router at 192.168.0.1 ? not even ping it? if so, maybe it's something else than dhcp that's not working right...

---

### Post by rubbsdecvik on 2007-02-19
That's right... I couldn't even ping... whenever I would do that it would say "network not available." 

But I don't think my router is working right anyway, because I tried using a LiveCD and it still wouldn't get an IP address.

I guess it's probably my cheap router.

Thanks anyway.

---


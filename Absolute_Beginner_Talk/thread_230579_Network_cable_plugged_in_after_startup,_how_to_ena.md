---
title: "Network cable plugged in after startup, how to enable networking"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by Sambalbai on 2006-08-06
Hi,

newbie question here: I started up my laptop, and when I got to browsing the internet I found out I had forgotten to plug in my network cable. I used the Windows way to fix this (i.e. reboot), but there has got to be an easier way. I think I should send some restart signal to some network driver or network service, but I don't know how to do so. Does anybody know what command I ought to use for this?

Thanks,
              Sambalbai.

---

### Post by 23meg on 2006-08-06
```
sudo /etc/init.d/networking restart
```should do it.

---

### Post by steve.horsley on 2006-08-06
I'm not sure you need to do anythong other than plug the cable in and wait 5 seconds. That's all I ever do.

---

### Post by Sambalbai on 2006-08-06
Thanks for the input, unfortunately it didn't work. It seems like it gets tangled up with my wireless hardware (which I don't use, haven't got an access point yet)

What happens when I restart networking is:

 ```
* Reconfiguring network interfaces...                                          Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:17:31:fa:43:c2
Sending on   LPF/eth1/00:17:31:fa:43:c2
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.1 port 67
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:17:31:e4:b3:ae
Sending on   LPF/eth0/00:17:31:e4:b3:ae
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Listening on LPF/eth0/00:17:31:e4:b3:ae
Sending on   LPF/eth0/00:17:31:e4:b3:ae
Sending on   Socket/fallback
receive_packet failed on eth0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
send_packet: Network is down

``` 
Also, when I do an ifconfig before and afterwards I notice that my eth1 is gone (my normal interface). Before restarting the network, my configuration reads:

```
eth1      Link encap:Ethernet  HWaddr 00:17:31:FA:43:C2
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:1710 (1.6 KiB)
          Interrupt:233 Base address:0xc800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:172 (172.0 b)  TX bytes:172 (172.0 b)

``` 
As you can see, eth0 isn't present normally, which is fine.

Judging from the output, it seems like it finds my DHCP server on 192.168.1.1, but then goes on to overwrite things by using the non-active eth0.

Any ideas?

regards,
             Sambalbai

---

### Post by Sambalbai on 2006-08-08
Got it working now. Getting ndiswrapper to work for my wireless and enabling eth0 solved the problem. I still think it's strange it didn't work before, though......

---

### Post by xpod on 2006-08-08
If you get broadband through a set top box like i do with ntl you sometimes just need to turn the box on and off.
I get a similar problem when im switching the connection between pc`s

---

### Post by Sambalbai on 2006-08-09
No, it's connected straight to my router (Draytek vigor 2200E). So that's not why it won't gets its parameters automagically. But I know how to do it manually now, so it's fine for me.

---


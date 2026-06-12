---
title: "[SOLVED] Try to ping my host: Network unreachable"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by MachaB on 2007-11-22
Hi

I've tried to link a Mac to my Dell running Feisty (server edition) with a crossover Ethernet cable. I've assigned IP address 127.0.1.2 to the Mac. When I ping this address from the Dell, it works. But it's more complicated the other way round.

First my localhost's default address was 127.0.0.1. So I ifconfiged eth0 and lo to force address 127.0.1.1 on both. I also added
```
auto eth0
iface eth0 inet static
address 127.0.1.1
netmask 255.255.255.0
gateway 127.0.1.127 
```
to /etc/network/interfaces

(Damn don't know if the netmask and gateway are OK)

After rebooting, lo inet address is still 127.0.0.1, while eth0 address is 127.0.1.1. (Should I edit interfaces the same way for lo as for eth0?). I still can't ping my Dell from my Mac; Terminal says: 

```
PING 127.0.1.1 (127.0.1.1): 56 data bytes
ping: sendto: Network is unreachable
```

Strangely, if I do route -n, it says
```
Destination     Gateway     Genmask           Flags      Metric       Ref Use      Iface
127.0.1.0         0.0.0.0       255.255.255.0   U           0                0       0         eth0
```

the destination is not 127.0.1.1 but 127.0.1.0, is it normal?

Anyway, if I ping 127.0.1.0 from the Mac, same result:
      
```
PING 127.0.1.0 (127.0.1.0): 56 data bytes
ping: sendto: Network is unreachable
```


Morevoer, at startup, apache keeps on saying
```
Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for server name
```

Is that normal?

(Maybe it would go better if I used DHCP instead of forcing IP addresses I'll probably have to change one day anyway. But to use DCHP, I'll probably need to get my wireless dongle working and for now I'm blocked by the absence of Linux headers, which apparently keep ndiswrapper from installing -any ideas welcome if you happen to have hints, but I'll make another post about that anyway).

Many thanks in advance!

---

### Post by perfecttao on 2007-11-23
Hi,

I think the problem you have probably stems from the address range you are trying to use.

The address block 127.x.x.x is typically reserved for loopback tests.  For example, regardless of the IP you have, pinging 127.0.0.1 would ensure that the interface is alive (ie. drivers working).

I would attempt to specify an address range of say 192.168.0.0/24 on both machines, so for example give the Dell 

IP:  192.168.0.2
Mask: 255.255.255.0
GW: 192.168.0.254 or 192.168.0.1 (this would be the address of your internet gateway or route out for both machines - if you're using ADSL then this would be your router....)

And then give the Mac 

IP: 192.168.0.3
Mask: 255.255.255.0
GW: 192.168.0.254 (or whatever the correct Gateway is...)

Generally DHCP is a good idea....you need a device that supports being a DHCP server.....like your feisty box ;)  Then you need to specify the address range that it will issue.  The majority of ADSL routers support being DHCP servers too :)

A good tutorial on IP address classes is available here 

[http://www.ralphb.net/IPSubnet/ipaddr.html](http://www.ralphb.net/IPSubnet/ipaddr.html)

Hope this helps

---

### Post by MachaB on 2007-11-25
Hi Perfecttao

Thanks for the piece of advice. I've tried the range of addresses you gave and it works perfectly well! Now I'll be able to post my troubles more efficiently (easier to copy/paste from the Mac's Terminal than to key in what appears on my Dell's screen...). Next step is to make the wireless dongle work. Wish me good luck...8-[

---

### Post by perfecttao on 2007-11-26
Glad to help....

:)

---


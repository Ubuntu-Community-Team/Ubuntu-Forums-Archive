---
title: "How-to ethernet over firewire"
date: 2011-05-24
forum: Apple Hardware Users
---

### Post by Azyx on 2011-05-24
Hi.
On a PPC iMac g3 and iLamp g4. I wonder how I activate IP over Firewire on 10.04LTS and 11.04.

[https://help.ubuntu.com/community/EthernetOverFirewire](https://help.ubuntu.com/community/EthernetOverFirewire)

Find this help, but how do I find drivers? ohci1394 and eth1394?

When I run modeprobe I get this. 

```
sudo modprobe eth1394
[sudo] password for Azyx: 
FATAL: Module eth1394 not found.
```I dont find Networking under:  System-> Administration->?
Is this an old guide?

I have also #-marked some drivers in  /etc/modprobe.d/blacklist-firewire.conf and blacklist.conf but driver is not finded when modprobe eth1394 :(

/Cheers

---

### Post by Azyx on 2011-05-31
bump

---

### Post by hihanhoesj on 2011-07-15
Hi Azyx,

I dont know if you managed to get this fixed. If you have not I got mine working between my 10.10 and 11.04 by using

```

modprobe firewire-net
ip address add dev firewire0 <ip address>
ifconfig firewire0 up

```

on both machines

Hope that helps you
Regards
_h

---

### Post by UseLinuxNotWindows on 2011-12-26
Don't forget to add your netmask (e.g. for 192.168.10.x)

```

modprobe firewire-net
ip address add dev firewire0 192.168.10.2/255.255.255.0
ifconfig firewire0 up

```I find this very useful for transferring files from my Apple Mac to my trusty Lenovo laptop (running Ubuntu 11.10) :grin:

---


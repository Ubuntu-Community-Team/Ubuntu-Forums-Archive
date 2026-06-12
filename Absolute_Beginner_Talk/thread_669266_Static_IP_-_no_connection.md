---
title: "Static IP - no connection"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by ben22 on 2008-01-16
Hello,

I have assigned a static IP to my Ubuntu 7.10 machine.

I did the following:


open the /etc/network/interfaces file.

**sudo gedit /etc/network/interfaces**


I saw

[B]auto lo
iface lo inet loopback[/B]


I changed to:

[B]auto eth0
iface eth0 inet static
address 192.168.0.136
netmask 255.255.255.0
network 192.168.0.1
broadcast 192.168.0.255
gateway 192.168.0.1
[/B]


Then  changed DNS:

sudo gedit /etc/resolv.conf

[B]
nameserver DNS IP
namserver DNS IP2[/B]


Restart the networking:
**sudo /etc/init.d/networking restart**

[B][I][CENTER]
After performing these changes and not rebooting, but logging out and in again - there was no internet connection.
Thus I restarted the computer - the boot halted at "Starting NFS common utilities"[/CENTER][/I][/B]


The system showed before for ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:13:8F:29:C7:A8  
          inet addr:192.168.0.37  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:8fff:fe29:c7a8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:494738 errors:0 dropped:0 overruns:0 frame:0
          TX packets:407430 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:411660900 (392.5 MB)  TX bytes:33802446 (32.2 MB)
          Interrupt:23 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:776 (776.0 b)  TX bytes:776 (776.0 b)


What can I do?

Cheers,
Ben

---

### Post by Cypher on 2008-01-16
Show us the output of
```

route
ping 192.168.0.1

```

---


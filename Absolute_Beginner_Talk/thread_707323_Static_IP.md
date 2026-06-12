---
title: "Static IP"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by Jloser on 2008-02-25
Whenever I restart my router, the static IP address I set for my server gets replaced with a DHCP address (assigned by the router).  How do I make it so that my computer always has a static IP?

/etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.250
        netmask 255.255.255.0
        network 192.168.1.0
        gateway 192.168.1.1
```
#ifconfig (before /etc/init.d/networking restart
```
eth0      Link encap:Ethernet  HWaddr 00:12:3F:78:FF:10
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:fe78:ff10/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26182981 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8160232 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1138180692 (1.0 GB)  TX bytes:531159895 (506.5 MB)
          Base address:0xcce0 Memory:ef7e0000-ef800000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4870 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4870 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1375889 (1.3 MB)  TX bytes:1375889 (1.3 MB)
```
#ifconfig (after /etc/init.d/networking restart)
```
eth0      Link encap:Ethernet  HWaddr 00:12:3F:78:FF:10
          inet addr:192.168.1.250  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:fe78:ff10/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26183560 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8161139 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1138227006 (1.0 GB)  TX bytes:531434006 (506.8 MB)
          Base address:0xcce0 Memory:ef7e0000-ef800000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4871 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4871 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1375977 (1.3 MB)  TX bytes:1375977 (1.3 MB)
```

---

### Post by justleen on 2008-02-25
that is the correct way to give eth0 a static IP..

in your output it gets 192.168.1.250 after the restart? thats what you want right?

---

### Post by glennric on 2008-02-25
You have to first set your router to always assign your computer the same (static) ip address.

---

### Post by Jloser on 2008-02-25
Yes it is working now, but if the power goes out or the router restarts it will not be working.

Is there a way to do it if I don't have access to the router?

---

### Post by seventhc on 2008-02-25
Why wouldn't you have access to the router? It should be right there...if the router is set to dhcp then that's what it will do. Your router is the thing handing out IP's so it has to be set in the router as well.
If you don't know the login info try
admin
password

---

### Post by justleen on 2008-02-25
im not sure wether i understand you right..

The config you have, will give your machine a static IP. The IP stays the same wether you reboot or not (a reboot/power down should not affect your config files..)

If your router is configured as a DHCP server, you should check the config of the router for any options concerning static ip adresses. if this is your only machine, consider turning DHCP off on your router.
Check if your router is trying to assign an ip to this machine (based on MAC, perhaps?)

---


---
title: "Internet Woes! eth0 active"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by hollym on 2006-09-07
Have been trying on and off for a couple of days but still no joy with internet. eth0 is active and there is some activity in the system Monitor screen. I was asked a couple of times to find out the contents of $route and $ifconfig, so here they are. Yesterday someone commented that I had no gateway defined and no IP address for that gateway or something. Anyway, here is the text dump of the files. Any ideas? cheers in advance ...

$route 
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref
(no information - is this the problem?)

$ifconfig
Link encap:Ethernet HWaddr 00:0C:6E:11:1B:3B
inet6 addr: fe80::20c:6eff:fe11:1b3b/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:1633 errors:0 dropped:0 overruns:0 frame:0
TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:97980 (95.6 KiB) TX bytes:4230 (4.1 KiB)
Interrupt:201 Base address:0x9800lo

Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:135 errors:0 dropped:0 overruns:0 frame:0
TX packets:135 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:10196 (9.9 KiB) TX bytes:10196 (9.9 KiB)

---

### Post by David Corrales on 2006-09-07
The problem is that eth0 doesn't have a valid IP address. Try **sudo dhclient** and see if you get any dhcp offers.

---

### Post by DSn0wMan on 2006-09-07
What is your setup? i.e. modem -> router -> PC

Are you using DHCP?

It might help more to see your /etc/network/interfaces file.

---

### Post by hollym on 2006-09-07
setup is that i plug my internet directly into a wall socket (i.e. my building is hardwired) and they have a central server box in the basement. No modems, no router, just a sraight plug into the wall.
I am using DHCP, though it seems as though it is not configured properly. I have run the sudo invoke-rc.d networking restart command a few times and constantly get a DHCP no offers received response. havent tried the sudo dhcpclient command but I'm guessing the result will probably be the same.

/etc/network/interfaces file

not the full file but the part that relates to eth0 just says

auto eth0
iface eth0 inet dhcp

If the problem is with DHCP, what is the next step ... cheers

---

### Post by hollym on 2006-09-07
/etc/network/interfaces file

not the full file but the part that relates to eth0 just says

auto eth0
iface eth0 inet dhcp

---

### Post by hollym on 2006-09-07
anyone? ...

---

### Post by DSn0wMan on 2006-09-07
Have you tried this howto:

[http://ubuntuguide.org/wiki/Dapper#How_to_configure_network_connections](http://ubuntuguide.org/wiki/Dapper#How_to_configure_network_connections)

There are plenty of other good network related howto's on that page.

edit: You may try swapping out your network (RJ45) cable for a different one.  Many difficult to diagnose problems happen at the physical layer (cables connecters NIC's etc..)

This is what an active properly configured interface looks like with the if config command

eth1      Link encap:Ethernet  HWaddr 00:11:5B:23:E5:DD
          inet addr:192.168.1.149  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:5bff:fe23:e5dd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19888823 errors:0 dropped:6 overruns:0 frame:0
          TX packets:19156793 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1887541679 (1.7 GiB)  TX bytes:1649150652 (1.5 GiB)
          Interrupt:201 Base address:0xcc00

notice that I have an IP, and the link is UP.

---


---
title: "network problem"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by point on 2006-04-05
I installed Ubuntu 5.10 on the second SATA drive in my system (the first one was disabled). After installation, everything was ok (network was up and running etc.) After enabling the first SATA drive, I had to change "sda" entries to "sdb" (in menu.lst and fstab) to make the system boot correctly and a new problem emerged - my network won't work anymore (modules for my RealTek RTL8139 are loaded).... :-k

---

### Post by mlind on 2006-04-05
if by network you mean internet connection, try to aquire it from DHCP using command
*sudo dhclient eth0*

---

### Post by point on 2006-04-05
[QUOTE=mlind]if by network you mean internet connection[/QUOTE]

no, my network adapter behaves as it is disabled, the appropriate LED on my switch with this network adapter connected is turned off

---

### Post by mlind on 2006-04-05
[QUOTE=point]no, my network adapter behaves as it is disabled, the appropriate LED on my switch with this network adapter connected is turned off[/QUOTE]

how does /etc/network/interfaces look like?

---

### Post by point on 2006-04-05
[QUOTE=mlind]how does /etc/network/interfaces look like?[/QUOTE]

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0.

mapping hotplug
script grep
map eth0

iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
netowrk 192.168.1.0
broadcast 192.168.1.255
dns.nameservers 192.168.1.2

auto eth0

---

### Post by jamesr on 2006-04-05
Post outputs of ```
sudo ifconfig -a
```

---

### Post by point on 2006-04-05
[QUOTE=jamesr]Post outputs of ```
sudo ifconfig -a
```[/QUOTE]

eth0 Link encap: Ethernet HWaddr.........
inet addr: 192.168.1.2 Bcast:192.168.1.255 Mask: 255.255.255.0
UP BROADCAST RUNNING MULTICAST MTU: 1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collission:0 txqueuelen: 1000
RX bytes:0 (0.0b) TX bytes:0 (0.0b)
Interrupt: 16 Base address: 0xa000

lo ...........................

---

### Post by jamesr on 2006-04-05
It is finding the card and it has a address but in your /etc/network/interfaces file> auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0.

mapping hotplug
script grep
map eth0

iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
netowrk 192.168.1.0
broadcast 192.168.1.255
dns.nameservers 192.168.1.2

auto eth0you are setting the nameserver to your own PC which is not the way it should be. I would comment out or delete that line and use the file /etc/resolv.conf. Also the nameservers should be the addresses of the ISP nameservers. ALso post the resolv.conf file

---

### Post by point on 2006-04-05
[QUOTE=jamesr]ALso post the resolv.conf file[/QUOTE]

route add default gw 192.168.1.1
nameserver 192.168.1.1

---

### Post by point on 2006-04-05
[QUOTE=jamesr]I would comment out or delete that line and use the file /etc/resolv.conf. Also the nameservers should be the addresses of the ISP nameservers. ALso post the resolv.conf file[/QUOTE]

I commented the line, but network still doesn't work :-?

---

### Post by Iowan on 2006-04-05
Do you have another machine/router/etc... at 192.168.1.1 that's supposed to be connecting to your ISP (and presumably has the address of your ISP nameserver?

---

### Post by point on 2006-04-05
[QUOTE=Iowan]Do you have another machine/router/etc... at 192.168.1.1 that's supposed to be connecting to your ISP (and presumably has the address of your ISP nameserver?[/QUOTE]

Yes, router is at 192.168.1.1, but my connection to router nor to other parts of the network doesn't work. My problem at the moment is not the Internet, the problem is network adapter under Linux which stopped working.... and it works in Windows.

---


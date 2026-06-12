---
title: "Ubuntu/OSX on wireless network"
date: 2011-01-31
forum: Apple Hardware Users
---

### Post by POWMS on 2011-01-31
I am trying to network my Ubuntu notebook with my Macbook. Ubuntu can 'see' the Macbook, but not the other way round. Have I missed a setting on either machine for them to play nice together?
Thanks.

---

### Post by 1clue on 2011-01-31
Somebody's network isn't set up right, or you have a firewall set up.

I use Linux with my MacBook Pro all the time.

Post the output of **ifconfig** and **netstat -rn** from both boxes.

---

### Post by POWMS on 2011-01-31
Thanks 1.
I will do that tonight when I get home.

---

### Post by POWMS on 2011-01-31
```
craig$ ifconfig
lo0: flags=8049<UP,LOOPBACK,RUNNING,MULTICAST> mtu 16384
	inet6 ::1 prefixlen 128 
	inet6 fe80::1%lo0 prefixlen 64 scopeid 0x1 
	inet 127.0.0.1 netmask 0xff000000 
gif0: flags=8010<POINTOPOINT,MULTICAST> mtu 1280
stf0: flags=0<> mtu 1280
en0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
	ether 00:25:4b:a5:31:80 
	media: autoselect
	status: inactive
en1: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
	ether 00:25:4b:8e:c6:50 
	inet6 fe80::225:4bff:fe8e:c650%en1 prefixlen 64 scopeid 0x5 
	inet 192.168.1.2 netmask 0xffffff00 broadcast 192.168.1.255
	media: autoselect
	status: active
fw0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 4078
	lladdr 00:25:4b:ff:fe:a5:31:80 
	media: autoselect <full-duplex>
	status: inactive
en2: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
	ether 00:25:00:c7:03:f6 
	media: autoselect
	status: inactive

```
```
Routing tables

Internet:
Destination        Gateway            Flags        Refs      Use   Netif Expire
default            192.168.1.1        UGSc          124        0     en1
127                127.0.0.1          UCS             0        0     lo0
127.0.0.1          127.0.0.1          UH              1      394     lo0
169.254            link#5             UCS             0        0     en1
192.168.1          link#5             UCS             3        0     en1
192.168.1.1        c0:3f:e:59:54:3e   UHLWI         130      675     en1   1004
192.168.1.2        127.0.0.1          UHS             0        0     lo0
192.168.1.3        1c:65:9d:9:9d:93   UHLWI           0       29     en1   1034
192.168.1.255      link#5             UHLWbI          4      198     en1

Internet6:
Destination                             Gateway                         Flags         Netif Expire
::1                                     ::1                             UH              lo0
fe80::%lo0/64                           fe80::1%lo0                     Uc              lo0
fe80::1%lo0                             link#1                          UHL             lo0
fe80::%en1/64                           link#5                          UC              en1
fe80::225:4bff:fe8e:c650%en1            0:25:4b:8e:c6:50                UHL             lo0
ff01::/32                               ::1                             Um              lo0
ff02::/32                               ::1                             UmC             lo0
ff02::/32                               link#5                          UmC             en1

```

---

### Post by POWMS on 2011-01-31
This one from Ubuntu.
```
craig@craig-Presario-CQ62-Notebook-PC:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 60:eb:69:40:20:c7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:54 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3976 (3.9 KB)  TX bytes:3976 (3.9 KB)

wlan0     Link encap:Ethernet  HWaddr 1c:65:9d:09:9d:93  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1e65:9dff:fe09:9d93/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:228 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16005 (16.0 KB)  TX bytes:34241 (34.2 KB)
          Interrupt:16 Memory:f8410000-f8410100 

```
```
craig@craig-Presario-CQ62-Notebook-PC:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0

```

---

### Post by 1clue on 2011-01-31
I don't see anything wrong with your network.  Apple has funky output with ifconfig, but mine does the same thing.

Since your mac is the one that can't see the linux box, the linux box is probably blocking packets.

Do you have a firewall installed on your linux box?  If you have it shut down tight, it can appear as though your system doesn't even exist to outside computers.

Unfortunately I'm not up on current firewalls, and I'm not running Ubuntu on anything I currently have access to.  I've been using an appliance for network security, and each host is configured to be reasonably secure as well.  But I imagine with Ubuntu that there's a firewall or security control panel that you can configure.

---

### Post by POWMS on 2011-02-01
Thanks 1. I suspect the same thing as you.
I'll have a check tonight. Though it is a standard, fresh install of Ubuntu, no additional firewall settings. Maybe the default is high, I'll check.

---


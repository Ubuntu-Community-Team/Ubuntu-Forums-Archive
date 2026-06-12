---
title: "Cannot connect to the internet using a staic ip"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by mtn_man on 2007-10-18
At the risk of beating this subject to death ( I have read a lot of related articles regarding internet connections) but still not luck getting connected...

I am running Dapper with no GUI at this point and am trying to connect to the internet from my school. I have a static IP and have been able to connect to the internet with a Windows box when I configure my internet connection manually - so I know that the info (IP, router, etc..) I have is correct and the connection itself works.

I have looked at my** /etc/network/interfaces** file and it reads:

...

auto lo
iface lo inet loopback

auto eth0
iface etho inet static

   address 129.82.xxx.xxx
   netmask 255.255.xxx.x
   network 129.82.xxx.x
   broadcast 129.82.xxx.xxx
   gateway 129.82.xxx.x

   dns-nameservers 129.82.xxx.xx 129.82.xxx.xx

My **resolv.conf** file looks like:

search colostate.edu
nameserver 129.82.xxx.xx
nameserver 129.82.xxx.xx

I have tried to ping the router and it fails w/ 100% packet loss, when I try to run apt-get update i get:

50% [connecting to us.archive.ubuntu.com]
Temporary failure resolving us.archive.ubuntu.com

etc...

When I run **lspci**, I see:

0000:00:02.0 Ethernet controller: Intel Corp. 82557/8/9 [Ethernet Pro 100] (rev 08)
0000:00:0a.0 Ethernet controller: Intel Corp. 82557/8/9 [Ethernet Pro 100] (rev 08)

How do I tell if the eth0 option in the /etc/network/interfaces file matches one of the options listed above?? Or how do I know that I am attempting to connect using the right ethernet card option?

Any help would be greatly appreciated.

Thanks,

mtn_man

---

### Post by introp on 2007-10-18
If you know you've got the right IP, it's using a gateway or routing table problem.  Could you post the output of "route -n" and "ifconfig"?

---

### Post by mtn_man on 2007-10-18
route -n

Dest                         gateway                 genmask                flags   metric   ref    use  iface
129.82.xxx.x           0.0.0.0               255.255.xxx.0           U         0         0       0     eth0
0.0.0.0                   129.82.xxx.x       0.0.0.0                      UG       0          0      0     eth0

working on the write up of ifcong...coming next...

---

### Post by compiledkernel on 2007-10-18
sudo cat /var/log/messages > ~/messages.txt
sudo cat /var/log/dmesg > ~/dmesg.txt 

Im pretty sure one of those will tell you if something really unhappy is going on , post here whatever you find.

---

### Post by mtn_man on 2007-10-18
ifconfig:

eth0    Link encap:Ethernet HWaddr  00:02:55:AD:1F:16
           inet addr:129.82.xxx.xxx Bcast:129.82.xxx.xxx  Mask:255.255.xxx.x
           UP BROADCAST MULTICAST MTU:1500 Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0'
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

lo   Link encap:Local Loopback
     inet addr:127.0.0.1  Mask:255.255.xxx.x
    inet 6 addr: ::1/128 Scope:Host
           UP LOOPBACK RUNNING MTU:16436 Metric:1
          RX packets:290 errors:0 dropped:0 overruns:0 frame:0
          TX packets:290 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:29916 (29.2 KiB) TX bytes:29916 (29.2 KiB)

---

### Post by mtn_man on 2007-10-18
messages.txt:

[43798032.350000] ADDRCONF(NETDEV_UP): eth0: link is not ready

---

### Post by mtn_man on 2007-10-18
dmesg.txt:

[42949406.740000] e100: eth0: e100_probe: addr 0xfeb7f000, irq 193, MAC addr 00:02:55:AD:1F:16

---


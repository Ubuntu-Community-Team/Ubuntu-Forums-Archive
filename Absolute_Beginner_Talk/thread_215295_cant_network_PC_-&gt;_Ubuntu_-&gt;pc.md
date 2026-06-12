---
title: "cant network PC -&gt; Ubuntu -&gt;pc"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by Phatie Mcgee on 2006-07-13
sooo I've gone stupid since I know I have done this before and I remember it being easy!

I have Ubuntu getting its Internet connection from a router (eth0,192.168.0.104).. Ubuntu is then trying to share that connection to a PC (eth1)

but something is not working right,
eth1 is set to static 192.168.1.69
my PC is set to use a static IP: 192.168.1.69 Subnet: 255.255.255.0 gateway: 192.168.0.104

and what I am trying to do is setup Ubuntu to be a firewall for my PC so I don't have to have a software firewall running on it.. I also want to put a AV scanner on it..

DNS is setup on the PC using my ISP's DNS servers

Now it seems to me that perhaps the gateway is wrong since its on a separate ip scheme but I though that's how it had to work?

if someone can point me to a howto of sharing a Internet connection through Ubuntu.. I'd be grateful!

I've tried firestarter.. but I still cant get the computers to even see each other.. in windows it says the nic is unplugged! :(

I just cant figure this out ](*,)

---

### Post by dmizer on 2006-07-13
well first of all, do you have a router between ubuntu and your pc?  if not, you'll need a crossover cable.

otherwise, if windows is showing network cable is unpluged, you'll need to figure out why there doesn't appear to be a physical connection.  bad cable? bad pc nic drivers? loose connection?

is the local ethernet card on your ubuntu box even functioning?  what's the output of ifconfig?

---

### Post by gborzi on 2006-07-13
I have an howto for debian, but it's written in italian. However the main points are:
1) enable ip forwarding, i.e. as root type
> echo 1 > /proc/sys/net/ipv4/ip_forward
2) give the command
> sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE 
To have the correct configuration of the router at every reboot, do the following:
1) uncomment the > net/ipv4/ip_forward=1 line in /etc/sysctl.conf.
2) save the ip rules
> sudo iptables-save > iptables-saved 
put them somewhere in your hard disk (e.g. cp iptables-saved /etc) and put the command
> cat /etc/iptables-saved | iptables-restore
in some init script, e.g. /etc/rc.local .

---

### Post by Phatie Mcgee on 2006-07-14
> **gborzi said:**
> I have an howto for debian, but it's written in italian. However the main points are:
1) enable ip forwarding, i.e. as root type

2) give the command

To have the correct configuration of the router at every reboot, do the following:
1) uncomment the  line in /etc/sysctl.conf.
2) save the ip rules

put them somewhere in your hard disk (e.g. cp iptables-saved /etc) and put the command

in some init script, e.g. /etc/rc.local .

well.. one of my problems is that I didn't have a crossover cable.. shame on me :P  But I put in those commands and I still cant see Ubuntu from XP, however I can ping XP from Ubuntu.. (but I'm guessing thats because the nic is in the Ubuntu box) but I cant ping Ubuntu from XP.. 

Both computers workgroups are MSHOME

Ubuntu network config:
eth0      Link encap:Ethernet  HWaddr 00:00:E8:89:7C:E1
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::200:e8ff:fe89:7ce1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8782 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4520 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7964906 (7.5 MiB)  TX bytes:506793 (494.9 KiB)
          Interrupt:177 Base address:0x4f00

eth1      Link encap:Ethernet  HWaddr 00:0F:3D:7D:25:36
          inet addr:192.168.1.69  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:3dff:fe7d:2536/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:177 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:18176 (17.7 KiB)  TX bytes:22593 (22.0 KiB)
          Interrupt:185 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:773 errors:0 dropped:0 overruns:0 frame:0
          TX packets:773 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:47770 (46.6 KiB)  TX bytes:47770 (46.6 KiB)

Route:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

XP network config:

Connection-Specfic IP suffix:
IP address: 192.168.1.69
Subnet mask: 255.255.255.0
Default Gateway: 192.169.0.102

in XP under LAN connection, activity, it shows it sending packets but not reciving any

What other information can I give you to help me figure this out??

Thanks for the help so far!

---

### Post by dmizer on 2006-07-14
what is the result of ipconfig in the windows xp machine?

---

### Post by Phatie Mcgee on 2006-07-15
> **dmizer said:**
> what is the result of ipconfig in the windows xp machine?

XP network config:

Connection-Specfic IP suffix:
IP address: 192.168.1.69
Subnet mask: 255.255.255.0
Default Gateway: 192.169.0.102

the XP and Ubuntu computers are connected via a crossover cable

thanks for the help so far guys.

---

### Post by gborzi on 2006-07-15
The ubuntu PC and the Windows XP PC have the same IP address, 192.169.1.69. It can't work in this way. The IP addresses must differ in the last number (with the 255.255.255.0 netmask), e.g. 192.168.1.69 for ubuntu 192.168.1.6_8_ for XP.

EDIT: Sorry, I hadn't noticed it before, but the gateway for Windows XP is wrong too, it must be your ubuntu PC, i.e. 192.168.1.69 in the example above.

---


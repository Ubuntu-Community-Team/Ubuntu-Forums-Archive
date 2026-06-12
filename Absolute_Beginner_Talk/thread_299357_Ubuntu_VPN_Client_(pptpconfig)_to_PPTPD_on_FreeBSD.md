---
title: "Ubuntu VPN Client (pptpconfig) to PPTPD on FreeBSD not working"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by robhipp on 2006-11-14
I have successfully installed pptpconfig on my Ubuntu machine (6.06 LTS). After messing around with pptpconfig, I am finally able to connect to my FreeBSD machine via VPN  (pptpd). 

On my Ubuntu box, I can ifconfig and am getting an ip address from the remote  VPN on FreeBSD, however, I cannot ping out... I get no reply to any computer on the network. If I VPN in with any windows machine, it works fine. 

I'm not sure about IP tables or anything like that, any help is much appreciated. 

My local network here at home is behind 192.168.1.x

At the office, it's 192.168.0.x

Like I said, it works fine when I connect via Windows VPN client. 

I set up 192.168.0.0/16 as a route in the pptpconfig and did notice when I try to ping a remote lan address, it sends out bytes but does not receive. 

Any help is greatly appreciated. Thanks!

---

### Post by robhipp on 2006-11-14
Here is my connection log on Ubuntu:

Using interface ppp0
pptpconfig: monitoring interface ppp0
Connect: ppp0 <--> /dev/pts/0
CHAP authentication succeeded
MPPE 128-bit stateless compression enabled
Cannot determine ethernet address for proxy ARP
local  IP address 192.168.0.80
remote IP address 192.168.0.100
pptpconfig: pppd process exit status 0 (started)
ip route replace 71.114.234.208 via 192.168.1.1 dev rausb0  src 192.168.1.2
ip route add '192.168.0.0/16' dev 'ppp0'
pptpconfig: routes added to remote networks
pptpconfig: connected

---

### Post by Carlos Santiago on 2006-11-14
hi. it is not clear what you want.
what interface do you want for default gateway?
or by other words, do u want that all your traffic goes out throught your VPN? or only the traffic to a specific network.
Carlos

---

### Post by robhipp on 2006-11-14
Thanks for the reply. I have several computers behind my lan at work I need to access. There are several IPs I need to access on the FreeBSD end. I'm not sure what gateway to use. All I need is to access those other IP addresses though. Like I said, I can't even ping the FreeBSD VPN server once I connect. If I can do that, then I could access everything else I need.

---

### Post by Carlos Santiago on 2006-11-14
place here the result of 'ifconfig', before and after you connect to the VPN

---

### Post by robhipp on 2006-11-14
Before:

eth0      Link encap:Ethernet  HWaddr 00:16:17:1B:86:FF
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:225 Base address:0xe200

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

rausb0    Link encap:Ethernet  HWaddr 00:12:17:73:0C:68
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:17ff:fe73:c68/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4891 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5053 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:65220521 (62.1 MiB)  TX bytes:870166 (849.7 KiB)


AFTER:

eth0      Link encap:Ethernet  HWaddr 00:16:17:1B:86:FF
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:225 Base address:0xe200

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:192.168.0.87  P-t-P:192.168.0.100  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1496  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:88 (88.0 b)  TX bytes:82 (82.0 b)

rausb0    Link encap:Ethernet  HWaddr 00:12:17:73:0C:68
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:17ff:fe73:c68/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5530 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5468 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:66207161 (63.1 MiB)  TX bytes:916350 (894.8 KiB)


PLEASE NOTE, I'm using rausb0 for my connection to the internet.

---

### Post by robhipp on 2006-11-14
By the way, here's the information I'm getting from ppp.log on the freebsd machine:

Nov 14 22:10:41 baby ppp[12908]: LCP: deflink: SendProtocolRej(2) state = OpenedNov 14 22:10:42 baby ppp[12908]: Phase: Unknown protocol 0xba34 (unrecognised protocol)

This has to be causing the error because when I'm connected, it goes like crazy.  It's funny though, I can connect and get an ip address.


Anybody who can help is greatly appreciated. Thanks.

---

### Post by Carlos Santiago on 2006-11-17
Sorry, I was out of forum for some time.
Can you ping 192.168.0.100?

This could be a routing problem. Plz place your routing table.

---


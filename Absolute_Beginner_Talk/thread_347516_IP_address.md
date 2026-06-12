---
title: "IP address"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by anaconda on 2007-01-27
How can I get my own ip address ?

I know ifconfig should give it to me, but there are several addresses there. which is my ?

or is there any easier way to get it?

---

### Post by taurus on 2007-01-27
What's the output of ifconfig then?

---

### Post by anaconda on 2007-01-27
```
eth0      Link encap:Ethernet  HWaddr 00:13:8F:1D:93:E8
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:8fff:fe1d:93e8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19709 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11813 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:23102036 (22.0 MiB)  TX bytes:1308348 (1.2 MiB)
          Interrupt:217 Base address:0xc800

eth2      Link encap:Ethernet  HWaddr 00:A0:D2:A5:87:16
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:193 Base address:0xac00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:45 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3444 (3.3 KiB)  TX bytes:3444 (3.3 KiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01
          inet addr:192.168.36.1  Bcast:192.168.36.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08
          inet addr:172.16.177.1  Bcast:172.16.177.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

---

### Post by JamieC on 2007-01-27
192.168.1.102 is most likely your (internal) IP address...

---

### Post by anaconda on 2007-01-27
Ok!
Thanks.
What is internal IP address. I suppose it is the one I would like to use in my home samba network.. ?
Which is what i need it for.

---

### Post by taurus on 2007-01-27
Looks like your ethernet connects to a router, 192.168.1.102.  And the vmnet1 & vmnet8 are from VMWare.

---

### Post by Pobega on 2007-01-27
Yeah, 192.168.1.102 is your local IP. You can connect to it with other computers through LAN, but external connections won't work with it. To find your external IP try [http://whatismyip.com/](http://whatismyip.com/), but your internal IP *should* be what you need for Samba.

---


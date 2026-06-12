---
title: "Kubuntu 7.04 – Konqueror not working"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by chager on 2007-08-21
Kubuntu 7.04 – Konqueror not working

I’ve configured my modem with Wvdial.  When I dial out the modem runs, but when I use Konqueror nothing happens?  I get and error that page is not found.  I checked with the system monitor to make sure that the modem is running.  Do you have to tell Konqueror that you are using a modem?

I used nano to configure Wvdial.

Thanks

---

### Post by wormser on 2007-08-21
Have you tried pinging by ip and domain name?  Do you have an ip address?  

```
ifconfig
```

```
ping 4.2.2.2
```

```
ping yahoo.com
```

---

### Post by chager on 2007-08-22
wormser

Here is the info:

Code: ifconfig

Result:
eth0      Link encap:Ethernet  HWaddr 00:D0:09:D2:A6:27
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Base address:0xd000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:592 (592.0 b)  TX bytes:592 (592.0 b)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:68.210.229.57  P-t-P:209.215.218.14  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:1042 (1.0 KiB)  TX bytes:1695 (1.6 KiB)



Code: ping 4.2.2.2

Result:

PING 4.2.2.2 (4.2.2.2) 56(84) bytes of data.
64 bytes from 4.2.2.2: icmp_seq=1 ttl=52 time=179 ms

It repeats the ping.

Code: ping yahoo.com

Result:

PING yahoo.com (66.94.234.13) 56(84) bytes of data.
64 bytes from w2.rc.vip.scd.yahoo.com (66.94.234.13): icmp_seq=1 ttl=51 time=258 ms

It repeats the ping.

Any clue?

---

### Post by chager on 2007-08-22
I tried to kill the KDE Network Manager.

Killall networkstatustestservice – it failed



Konqueror does not recognize that I’m using a dialup modem.

---


---
title: "No Connection to the internet"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by Droobie on 2007-04-16
I have just installed Ubuntu feisty fawn beta,
& I have no Internet connection for firefox,email or Synaptic,
I have installed on a dell p4 1.5ghz 512mb ram connected to an tp link TL-SF100SD 4 port network switch & Netcomm NB5 adsl2+ dsl modem, I have a Static IP of 58.6.33.113.
I have Network connectivity [so I assume that the tp-link switch is functioning OK1]
Can someone Please Help, Linux is not a very good OS if you can't connect to the internet !!
this is my first attempt at using Linux,Please be gentle with me.](*,)

---

### Post by bwhite82 on 2007-04-16
Post the output of:

> ifconfig -v -a

---

### Post by Droobie on 2007-04-16
Here's the post for the results of ifconfig -a -v;

andrew@CompaqP3:~$ ifconfig -a -v
eth0      Link encap:Ethernet  HWaddr 00:02:A5:1B:28:47
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:a5ff:fe1b:2847/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1295 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1455 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:678228 (662.3 KiB)  TX bytes:176040 (171.9 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

is this of any help in solving my problem?](*,)

---

### Post by bwhite82 on 2007-04-16
Hmmmm, shows that you are up and running. Are you behind a proxy or perhaps you need to set an IP instead of having one automatically assigned to you?

---


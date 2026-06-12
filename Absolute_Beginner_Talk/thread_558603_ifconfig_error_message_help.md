---
title: "ifconfig error message help"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by WIREHEAD on 2007-09-24
I am trying to make sense of this , details below .

ifconfig gives this output :


eth1      Link encap:Ethernet  HWaddr 00:10:B5:B1:65:DD                ( the smiley face in this line is a ":" and a "D" on my screen :D )
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::210:b5ff:feb1:65dd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36729 errors:295 dropped:682 overruns:295 frame:0
          TX packets:26080 errors:0 dropped:0 overruns:8 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:36029761 (34.3 MiB)  TX bytes:10392814 (9.9 MiB)
          Interrupt:12 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:920 (920.0 b)  TX bytes:920 (920.0 b)

This is a recent problem , internet acess still works , but is slower than usual .

I have ruled out the following :
ISP , Modem , Router , cables , NIC card . ( other computers on network are unaffected , swapping cables and NIC's between machines does not help )

The machine in question has been running Dapper for a couple of months now without any problems of this nature.

Any ideas ?

Thanks in advance !

WIREHEAD

---

### Post by justleen on 2007-09-24
erm...what is the error??
or do you mean the errors packets them self??

---

### Post by WIREHEAD on 2007-09-24
Justleen,

RX packets:36729 errors:295 dropped:682 overruns:295 frame:0
TX packets:26080 errors:0 dropped:0 overruns:8 carrier:0

Errors , dropped ,and overruns are what I'm thinking is a problem .

Sorry for not making that clear to begin with .

This is the current ifconfig error line ( just booted and ran several speed tests )

RX packets:29976 errors:488 dropped:1152 overruns:488 frame:0
TX packets:23044 errors:0 dropped:0 overruns:6 carrier:0

WIREHEAD

---


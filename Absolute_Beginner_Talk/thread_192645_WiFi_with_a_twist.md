---
title: "WiFi with a twist"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by monkeycool on 2006-06-09
Hi everyone,

I just installed Ubuntu 6.06 desktop on my laptop (dell inspiron 9100) as a dual boot with xp pro.  After the install, I booted back to xp, which mysteriously  found new hardware :confused: and asked me to restart, which I did.  I have no idea what hardware it thinks it found, but now my wifi connection wont work in xp.  Firefox  gives me an "interrupted" error. ](*,) 

Any help would be greatly appreciated!
Cheers!

---

### Post by sherlock-holmes on 2006-06-09
[QUOTE=monkeycool]Hi everyone,

I just installed Ubuntu 6.06 desktop on my laptop (dell inspiron 9100) as a dual boot with xp pro.  After the install, I booted back to xp, which mysteriously  found new hardware :confused: and asked me to restart, which I did.  I have no idea what hardware it thinks it found, but now my wifi connection wont work in xp.  Firefox  gives me an "interrupted" error. ](*,) 

Any help would be greatly appreciated!
Cheers![/QUOTE]

strange!

whats the output of 
```
ifconfig
```

and 

```
gedit /etc/network/interface
```

in linux...?

---

### Post by Dragonfire on 2006-06-09
your problem may be that your wireless card drivers have corrupted.

It would be easiest to do a driver check through the device manager utility, and if they appear to be corrupted, perform a driver rollback. This will reset the drivers to the last working driver set. After which, XP will probably update the drivers, resolving the problem.

---

### Post by monkeycool on 2006-06-09
@ sherlock-holmes

ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:0F:1F:0E:AF:7C
          inet addr:24.26.25.185  Bcast:255.255.255.255  Mask:255.255.252.0
          inet6 addr: fe80::20f:1fff:fe0e:af7c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2244 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2432 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:908208 (886.9 KiB)  TX bytes:249706 (243.8 KiB)
          Interrupt:193

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

gedit /etc/network/interface didn't do anything except open what looks like an empty document.

@ Dragonfire

I checked the device manager and couldn't find anything, however I'll try to do a driver rollback.

My problem is that the wifi problem is at work.  I'm posting this at home on an ethernet connection, and no wifi until I get back to work tomorrow. Although I could drive to the parkinglot and try to connect again.. 

Tell me what to do and I'll do it ;)  Anything to avoid eight hours at work tomorrow with no internet. :(

---


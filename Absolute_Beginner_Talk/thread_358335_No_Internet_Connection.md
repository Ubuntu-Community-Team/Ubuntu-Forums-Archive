---
title: "No Internet Connection"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by Fesarius on 2007-02-10
Help !!!
I'm a newbie. I tried ubuntu on an old computer, and everything worked great !
Now, I invested in a "new" PC. AMD64, Biostar mobo, Realtek 8201CL PHY onboard LAN.
I've installed Kbuntu for the AMD 64. Looks great but no Internet or sound (Both a function of the onboard Realtek stuff). I've checked other threads, but alas, no one seems to have a problem of my exact nature.

Need to establish internet connection, sound a distant second. 
Can anyone out there help !

Here's some screen output from terminal (please note, this is retyped, not cut-n-paste):
ifconfig:

lo  Link encap:Local Loopback
     inet addr:127.0.0.1  Mask:255.0.0.0
     UP LOOPBACK RUNNING  MTU:16436 Metric: 1
     RX packets:0 errors:0 dropped:0 overruns: 0 frame:0
     TX packets:0 errors:0 dropped:0 overruns: 0 carrier:0
     collisions:0 txqueuelen:0
     RX bytes: 0 (0.0 b)  TX bytes:0 (0.0 b)

Help !!!!

---

### Post by Mba7eth on 2007-02-10
Will clearly your lan port is down . Anyway if you are connected thru etharnet here is a solution : 
```
$sudo ifup eth0
$sudo dhclient eth0
$ping -c 4 google.com

```
if you are using wireless just search in the forum. there is planet cases and solutions you can find. Also goes for dialup .

---

### Post by Fesarius on 2007-02-10
Thanks for that one !, but no go...
I basically get this in response to you post:

There is already a pid file /var/run/dhclient.eth0.pid with pid 5798864
....
SIOCSIFADDR: No Such Device
eth0: ERROR while getting interface flags: No such device
Bind Socket to interface: No such device
Failed to bring up eth0
....

I'm not using wireless. It's a an RJ45 eithernet plug straight in. I'm posting this thread on the same network via a WinXP PC, so the connectivity, in that sense, is good.

 Could this be a driver and/or kernel issue ??

 I am grateful for your assistance !!!

---

### Post by Mba7eth on 2007-02-10
```
$ifconfig -a
```
please !

---

### Post by Fesarius on 2007-02-11
ifconfig-a :

lo              Link encap:Local Loopback
                 inet addr:127.0.0.1   Mask:255.0.0.0
                UP LOOPBACK RUNNING   MTU:16436  Metric: 1
                RX packets:152 errors:0 dropped:0 overruns:0 frame:0
                TX packets:152 errors:0 dropped:0 overruns:0 carrier:0
                collisions:0 txqueuelen:0
                RX bytes:12128 (11.8 KiB)   TX bytes:12128 (11.8 KiB)

Hope that helps !

---

### Post by Fesarius on 2007-02-24
Popped In an old 3Com nic and presto
Also popped in an old sound card and that's up too.
Thanks For the help.
Looks Like Kernel might need and update for Biostar mobo's with RealTek chipsets though.

---


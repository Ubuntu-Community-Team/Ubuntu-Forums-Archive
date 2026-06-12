---
title: "Kubuntu doesnt detect internet automatically"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by smartygoldenfish on 2008-04-18
when i start Kubuntu, the Knetwork manager shows i am well connected to the net, however internet doesnt run!

Then i type these:
> 
sudo dhclient eth0

whose reply is:
[I]Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1b:b9:82:b0:26
Sending on   LPF/eth0/00:1b:b9:82:b0:26
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.4 -- renewal in 125827 seconds.
[/I]

then i have to type this
> sudo dpkg --configure -a
Then my internet starts

Why is this so, i have to do this everytime i boot up!
and Knetworkmanager shows me CONNECTED everytime...even when i switch off my modem completely.

---

### Post by Crafty Kisses on 2008-04-18
Post the following output:
```
ifconfig
```

---

### Post by smartygoldenfish on 2008-04-18
*THATS THE OUTPUT...AFTER INTERNET HAS BEEN MANUALLY SWITCHED ON BY ME BY TYPING THOSE 2 COMMANDS....*
```


eth0      Link encap:Ethernet  HWaddr 00:1B:B9:82:B0:26
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:b9ff:fe82:b026/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1651 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1821 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1035332 (1011.0 KB)  TX bytes:240066 (234.4 KB)
          Interrupt:16 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

---

### Post by Troca on 2008-04-18
no need to capslock/scream to ppl trying to help. Anyway i posted a simular poste earlyer that you can read answers from that might help you 

[http://ubuntuforums.org/showthread.php?t=755726](http://ubuntuforums.org/showthread.php?t=755726)

---

### Post by smartygoldenfish on 2008-04-21
well the above post is nearly useless to a newbie like me!
can i get some straight forward answers to this question!
also, when i click on Manual Network Configuration..it shows NO ACTIVE DEVICE..not even eth0
Also, i remembered i messed up all these settings when internet stopped working suddenly one day to manual configuration...how do i revert it back?
any answers?

---


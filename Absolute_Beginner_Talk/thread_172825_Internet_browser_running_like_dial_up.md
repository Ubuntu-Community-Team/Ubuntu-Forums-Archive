---
title: "Internet browser running like dial up"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by peterj on 2006-05-09
HI,
I am very new to linux, Everthing installed fine, dual boot etc.
Tried 3 different browsers and they all have the same result..its like im on dial up (with wireless broadband) Its really frustrating and putting me off the entire system. 
I checked and windows internet explorer is still running fine.
Thanks in advance!](*,)

---

### Post by Al3xanR0 on 2006-05-09
We will need information that is a little bit mr tangible to be able to offer helpful assistance. Post the out put of the following

```
ifconfig
```

the mtu setting on wlan0 may need to be adjusted, there may be other possibilities. What are your system specs? The more info you are able to provide the bette.

---

### Post by peterj on 2006-05-09
ath0      Link encap:Ethernet  HWaddr 00:11:F5:74:ED:94
          inet addr:192.168.1.1  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::211:f5ff:fe74:ed94/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18463 errors:85625 dropped:0 overruns:0 frame:85625
          TX packets:12798 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:15907467 (15.1 MiB)  TX bytes:1168943 (1.1 MiB)
          Interrupt:193 Memory:dca40000-dca50000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:920 (920.0 b)  TX bytes:920 (920.0 b)



Thanks a mill for having patience in a newbie..appreciate it.

---

### Post by Kurt` on 2006-05-09
go to about:config in firefox

set network.dns.disableIPv6 to "true" and restart firefox

---

### Post by Googler on 2006-05-09
the feeling of slow browsing is due to IPv6 services that run with ubuntu
i had the same problem till i read a topic in this forum about disabling the ipv6 to speed up browsing it was amazing and it works 
here is the topic link:
[http://ubuntuforums.org/showthread.php?t=87798&highlight=ipv6]("http://ubuntuforums.org/showthread.php?t=87798&highlight=ipv6")

try to do the steps and reboot you will notice the difference

good luck

---

### Post by peterj on 2006-05-09
problem  solved by disabling ipv6 in firefox...
Thanks a million folks.. I'm not yet capable of doing the code one (im literally a complete newbie)
Its funny they dont have a default setting or cure for everyone because it looks like a lot of people have this problem and revert back to windows..makes an incredible difference thanks
peter

---


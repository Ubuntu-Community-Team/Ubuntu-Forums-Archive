---
title: "network troubles are driving me crazy"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by joesmith1234 on 2008-02-01
I am able to do networking and connecting to the web and download torrents and etc...

but only for a while.

After downloading for a while, or transferring files from another computer, the network services on the ubuntu machine just stop.  Nothing else happens.

I figured it was the card, so I borrowed a card from a friend, and he had the same card in his linux box with no troubles at all...  same behaviour...

Im kind of at a wits end here... Ive been fighting this problem for weeks.

Does ANYONE have ANY suggestions on where to go next?
Has this behaviour been seen before?

---

### Post by joesmith1234 on 2008-02-01
So, here is this...
```

nibbles@nibbles-desktop:~$ ifconfig -a -v
eth1      Link encap:Ethernet  HWaddr 00:50:04:37:2E:91
          inet addr:192.168.1.36  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:4ff:fe37:2e91/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:254 errors:0 dropped:0 overruns:0 frame:0
          TX packets:238 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:34463 (33.6 KB)  TX bytes:41436 (40.4 KB)
          Interrupt:20

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

Anyone know what else I can print out that may help?

---

### Post by joesmith1234 on 2008-02-01
nobody has suggestions?

---


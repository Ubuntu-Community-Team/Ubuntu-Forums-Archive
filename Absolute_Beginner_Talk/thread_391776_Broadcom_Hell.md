---
title: "Broadcom Hell"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by WolfCarinea on 2007-03-23
alright, 
 I have a Compaq Presario R3000Z, with a Broadcom 4306 802.11b/g WLAN internal card, I've used Ndiswrapper to install both bcmwl5.inf and bcmwl5a.inf, Ndiswrapper says the device is present. IT STILL WON'T WORK!!! what the hell do i do?


Also, three days ago, my wired ethernet connection literally just stopped working, the Network Manager tries to use it to connect to the internet and gets nothing, it's set as a DCHI (or whatever that abrieviation is). I have been able to use it mulitple times, even switching back and forth between Windows and Linux, the connection still works just fine in Windows, just like the wireless.... it's acting the very same way, detected, activated, attempts to connect, and no results. ???? fix anyone?

---

### Post by dhtseany on 2007-03-23
Please go to a terminal prompt and type:

```
$ ifconfig 
```

and post the output here.

Sean

---

### Post by WolfCarinea on 2007-03-23
eth0  Link encap:Ethernet HWaddr 00:0F:B0:6C:DF:88
        UP BROADCAST MULTICAST MTU: 1500 Metric:1
        RX packets:0 errors:0 dropped:0 overruns:0 frame:0
        TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:1000
        RX bytes:0 (0.0b) TX bytes:0 (0.0b)
        Interrupt:185 Base address:0x2000

lo Link encap:Local Loopback
   inet addr: 127.0.01 Mask 255.0.0.0
   inet6 addr: ::1/128 Scope:Host
   UP LOOPBACK RUNNING MTU:16436 Metric:1
   RX packets:255 errors:0 dropped:0 overruns:0 frame:0
   TX packets:255 errors:0 dropped:0 overruns:0 frame:0
   RX bytes:11272 (11.0KiB) TX bytes:11272 (11.0KiB)

---

### Post by WolfCarinea on 2007-03-23
that smilie is suppose to be : 0 without the space

---

### Post by dhtseany on 2007-03-25
Ok first make sure all of your interfaces are configured; System -> Administration -> Networking.

Put in your password.

If you see red boxes over eth0, eth1, etc... then you have to click Properties and check "enable this connection". Also, if eth0 is the interface that we're working with here, make sure that you select eth0 as the default gateway on the net-properties page.

After you do all that, click OK to exit out of that page and then go to the terminal and type:

```
$ /etc/init.d/networking restart
```
Then
```
$ ifconfig
```

And paste the results.

Sean

---


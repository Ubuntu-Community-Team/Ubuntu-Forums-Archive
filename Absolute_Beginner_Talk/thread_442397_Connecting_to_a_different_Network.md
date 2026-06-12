---
title: "Connecting to a different Network"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by led_scorched on 2007-05-13
I'm home on break from college.  I have a Toshiba Satellite Laptop running Dapper... at home it; connected to my WiFi no problem... but i cant for the life of me get it to connect to the ethernet here... it will bring up Google... and thats it.  Any ideas to fix it?

---

### Post by oilchangeguy on 2007-05-13
open the network manager (the two screened icon near the clock) and from the drop down menu select eth0. then you should be able to use the ethernet connection.

---

### Post by led_scorched on 2007-05-13
did that first thing... still got nothing.

...i can google search, but i'm not having luck with anything else...like yahoo.com, Gaim, etc

---

### Post by oilchangeguy on 2007-05-13
go to system, admin, networking. what's listed? also have you reset (turned off the cable modem) since you hooked this computer to it? if not unplug it for about a minute, turn it back on and try it.

---

### Post by led_scorched on 2007-05-13
eth0 activated.
modem not configured.

default gateway device - eth0


...tried youre steps.  nada.

---

### Post by jfinkels on 2007-05-13
> **led_scorched said:**
> eth0 activated.
modem not configured.

default gateway device - eth0

Make sure you have wireless connection unchecked and wired connection checked.

What is the output of the following command:
```

ifconfig -a

```

---

### Post by oilchangeguy on 2007-05-13
please re-read my previous post (i added to it).

---

### Post by led_scorched on 2007-05-13
eth0
Link encap:Ethernet  HWaddr *my mac address*
inet addr:192.168.1.102 Bcast:192.168.1.255 Mask:255.255.2550
inet6 addr: fe80::208 (blah blah) Scope:Link
UP BRAODCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:406 errors:0 dropped:0 overruns:0 frame:0
TX packets:490 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueelen:0
RX bytes:372 (372.0b)  Tx bytes:372 (372.0 b)

---

### Post by led_scorched on 2007-05-13
Oil - i tried the additional steps...but it didnt change anything. :(

---

### Post by annda on 2007-05-13
this might be overkill, but i managed to get more use of my father's laptop/router combination by blacklisting IPv6 .

[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

i started with disabling the protocol in FF:

about:config in the address line, filter ipv6, double-click to set the disable option to true.

restarting the connection is also a good idea:

```
sudo ifdown eth0
sudo ifup eth0
```

---

### Post by led_scorched on 2007-05-13
annda...FF is working now... but Gaim is still FUBAR

---

### Post by jfinkels on 2007-05-13
> **led_scorched said:**
> annda...FF is working now... but Gaim is still FUBAR

Do you get any error messages when you start gaim from the terminal?```
gaim
```

---

### Post by led_scorched on 2007-05-13
no error message... just tries to connect forever and gives up after a few minutes.

---

### Post by led_scorched on 2007-05-13
i got Kopete to work... but Gaim is still hanging when it tries to connect

---


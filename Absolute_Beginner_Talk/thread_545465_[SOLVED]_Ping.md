---
title: "[SOLVED] Ping"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by Yizi on 2007-09-07
How can i **Ping** from Ubuntu?
Is it possible at all :-s


*In windows your go run and the cmd, the you can type Ping [www.yourdomain.com](www.yourdomain.com)*

---

### Post by dca on 2007-09-07
open a terminal and do it the same way as you would in MSWinXP.  ping -c 3 xxx.xxx.xxx.xxx

---

### Post by yabbadabbadont on 2007-09-07
```
/home/daffy $ ping -c 1 www.yahoo.com
PING www.yahoo-ht3.akadns.net (69.147.114.210) 56(84) bytes of data.
64 bytes from f1.www.vip.re3.yahoo.com (69.147.114.210): icmp_seq=1 ttl=56 time=49.2 ms

--- www.yahoo-ht3.akadns.net ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 49.281/49.281/49.281/0.000 ms

```
:D

Edit: Too Slow.  :lol:

---

### Post by Yizi on 2007-09-07
pretty cool, is there any other codes you can use to get information about the website or the host? :D

---

### Post by dca on 2007-09-07
What do you mean?  You can use netcraft.com to find out what OS a particular website is running...

---

### Post by Yizi on 2007-09-07
> **dca said:**
> What do you mean?  You can use netcraft.com to find out what OS a particular website is running...

Yes, that's what i wanted is there anyway to do it in Ubuntu, because that's the web based version :-s

---

### Post by dca on 2007-09-07
You can try going into system -> administration -> network tools and click on the lookup tab...  Put an IP in there....

---

### Post by dwhitney67 on 2007-09-07
There is a command called 'whois' and another called 'traceroute'.  At a minimum, they work like this:

[FONT="Courier New"]
$ whois <IP address or URL>
$ traceroute <IP address or URL>[/FONT]

Read the man-page for each for additional info and for details on options that can be supplied to each command.

---

### Post by Yizi on 2007-09-07
> **dwhitney67 said:**
> There is a command called 'whois' and another called 'traceroute'.  At a minimum, they work like this:

[FONT="Courier New"]
$ whois <IP address or URL>
$ traceroute <IP address or URL>[/FONT]

Read the man-page for each for additional info and for details on options that can be supplied to each command.

I like this one looks OK, Thanks everyone, problem solved! :KS

---

### Post by yabbadabbadont on 2007-09-07
traceroute isn't installed by default.  Just an FYI.

---

### Post by Yizi on 2007-09-07
> **yabbadabbadont said:**
> traceroute isn't installed by default.  Just an FYI.

What does that mean :confused:

---


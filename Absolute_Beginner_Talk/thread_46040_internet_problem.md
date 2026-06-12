---
title: "internet problem"
date: 2005-07-02
forum: Absolute Beginner Talk
---

### Post by JICTY on 2005-07-02
My computer appears to be connected to the internet, but every time I type in a web site  it says the site cant be found. I have looked all over the message boards and I cant find anything to help me.

---

### Post by rachii on 2005-07-02
are you on wireless or not?  if you go to "System - Administration - Networking" is your ethernest connection Active?  is it configured?    and why does it "appear" to be connected, i dont understand?

---

### Post by JICTY on 2005-07-02
When I go into networking my ethernet is active and all the info seems to be filled in correctly. that is why i said it apears to be connected

---

### Post by cwaldbieser on 2005-07-03
Try opening a terminal and type

```
$ ping -c 3 www.google.com
```

(feel free to substitute in a different site name).  If everything is working OK, you should get something like:

```
PING www.l.google.com (64.233.161.104) 56(84) bytes of data.
64 bytes from 64.233.161.104: icmp_seq=1 ttl=244 time=22.9 ms
64 bytes from 64.233.161.104: icmp_seq=2 ttl=244 time=22.6 ms
64 bytes from 64.233.161.104: icmp_seq=3 ttl=244 time=22.0 ms

--- www.l.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 22.037/22.547/22.939/0.415 ms
```

If you get "ping: unknown host www.google.com", then maybe your DNS is just not set up correctly.  Try:
```

$ ping -c 3 64.233.161.104
```
and see if that works.  If so, then your computer is just not translating the site names into their addresses.

---

### Post by JICTY on 2005-07-05
when I try that it says "network is unreachable"

---

### Post by cwaldbieser on 2005-07-05
When you try which one(s)?  The first, the second, or both?

---

### Post by JICTY on 2005-07-05
both, the first says its unknown.

---

### Post by Bl0wn2b1ts on 2005-07-06
Hi,

Open a terminal and type ifconfig and post the results here

Thanks

Bl0wn2b1ts

---


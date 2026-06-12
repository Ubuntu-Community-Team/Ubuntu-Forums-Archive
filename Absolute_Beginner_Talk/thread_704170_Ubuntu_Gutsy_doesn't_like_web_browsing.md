---
title: "Ubuntu Gutsy doesn't like web browsing"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by NeonSamurai on 2008-02-22
Hi,

Long time lurker and first time poster. Basically I've been using Xubuntu for about 7 months now and I'm a convert, so much so that I decided to take the plunge and buy a large tome on Ubuntu and make my main PC dual boot. Up until now I've been installing Xubuntu on old machines at work so I can play around with them and thus far it's done the job very nicely indeed.

**The problem:**

I've installed Ubuntu on my main PC (6600GFX, Pentium D 815, 1GB Ram, XFi) and after a few initial hitches with the install it's up and running, but the internet connection is as flakey as hell. I can ping google, youtube and yahoo, but I can rarely open them in Firefox. I say rarely since it does occasionally work, but 95% of the time I get no response and the page times out. I've installed all the updates from the repositories with apt-get and the download speed was pretty good,

Sat beside my main machine on the same router is an Xubuntu laptop, which can connect to the internet without any problems. Basically my network consists of two routers: One attached to the internet and the other piggy-backed off of it. When booted in XP my main PC can find the internet and browse fluidly, but when it's logged in under Ubuntu the internet grinds. I can http onto each router no problem, but going anywhere else and the problems start.

Any ideas or suggestions would be much appreciated.

Thanks


Mark

---

### Post by justleen on 2008-02-22
check your 
```
ifconfig -a 
```
wether duplex setting are correct (compare them to windows, ipconfig /all)

and are your routes setup correctly in 
```
netstat -nr 
```

can you do a (as in, can it resolv?)
```
 nslookup www.google.com 
```



just some thouhgts

---

### Post by NeonSamurai on 2008-02-22
Many thanks Justleen. I can't do that now as I'm at work (running Gutsy on a Dell laptop), but I will give it a go tonight on my main PC. Here's what I get running ifconfig -a on the laptop for my main network adapter:

> eth0      Link encap:Ethernet  HWaddr 00:0D:56:B7:F1:0A  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:feb7:f10a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14978 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10065 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13943175 (13.2 MB)  TX bytes:1284825 (1.2 MB)
          Interrupt:11 


Where should I be looking in the above readout to check out the duplex settings?

Cheers


Mark

---

### Post by bollix47 on 2008-02-22
Just a thought, but sometimes IPV6 can cause similar problems.

Have you tried [disabling IPV6]("http://ubuntuforums.org/showpost.php?p=932249&postcount=3")?

---

### Post by SunnyRabbiera on 2008-02-22
> **bollix47 said:**
> Just a thought, but sometimes IPV6 can cause similar problems.

Have you tried [disabling IPV6]("http://ubuntuforums.org/showpost.php?p=932249&postcount=3")?

Yeh I was going to suggest this, though so far I have had no issues with IPV6 myself

---

### Post by NeonSamurai on 2008-02-22
Thanks Bollix47, that's something else to try and it does sound as if the guy had similar problems to myself. If the connection simply didn't work, at least I'd have a fairly good idea what might be wrong, but as it is there's so much it could be. :confused:

---

### Post by HereInOz on 2008-02-22
Some routers don't handle IPv6 as well as they should. I would certainly disable IPv6 as a trial in this instance.

---

### Post by SunnyRabbiera on 2008-02-22
> **HereInOz said:**
> Some routers don't handle IPv6 as well as they should. I would certainly disable IPv6 as a trial in this instance.

Yup, but it makes me glad I have a linksys router :D

---

### Post by justleen on 2008-02-22
sorry, i reread my post, and thats confusing :)

You cant see the duplex settings there, you can view those with "mii-tool" or with the GUI tool under Sys >Admin > network tools..

i've experienced some problems in the past with auto negotion and switches/routers who would correctly send there duplex/speed

---

### Post by NeonSamurai on 2008-02-22
Much obliged for the advice folks. It's given me plenty to work with. I'll check out the duplex settings and get rid of IPv6 and see if that does the trick, otherwise I'll probably be back here tomorrow ;)

---

### Post by NeonSamurai on 2008-02-22
FYI I ditched IPv6 and the machine can now access the internet reliably (it's what I'm using now). Thanks your all your advice people! \\:D/

---


---
title: "Network"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by drndrw on 2007-10-29
Hi. I've recently been downloading some files to my computer (100ish mb) but whenever I do, my router stops working. This is only on my Linux box. Why? Thanks.

---

### Post by genbuntu on 2007-10-29
Well you will have to probe in more.. 
1) Is it only from a particular site or with a particular program (like torrent etc) ?
2) I'm not sure but it could be a firewall setting issue also.

---

### Post by drndrw on 2007-11-02
Well, it's mainly packages. I was able to download the entire AA Server package (about 2.2 gbA) with no problems whatsoever. But maybe a few packages and my whole network's down. Do I need to open a special port fore this? It is only on my Linux box might I add.

---

### Post by drndrw on 2007-11-04
Bump. oOrry. I actually notyiced this is kind of with everything.

---

### Post by genbuntu on 2007-11-04
hmm... :confused: not able to  think more on this. Maybe someone else has better advice to offer.

---

### Post by drndrw on 2007-11-17
Okay. Well if anyone knows, please help :P!

---

### Post by gigaferz on 2007-11-17
have you tried  turning everthing off and reseting the router?, also check the modem and router do not have the  same  address..

---

### Post by JayTee on 2007-11-17
run ifconfig -a -v from a terminal window and paste it in a new post in this thread or as an attachment. 
also if you are not experiencing problems with any other computers, only linux then if you have a Windows system that is not experiencing this problem then open a command prompt and type IPCONFIG /ALL  , copy and paste the results and add that to what you post.

You mentioned AA, I don't know what that program is. Could you be more specific.

---

### Post by drndrw on 2007-11-19
```
ath0      Link encap:Ethernet  HWaddr 00:0F:A3:1B:72:3E  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:a3ff:fe1b:723e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7666 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5479 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5000357 (4.7 MB)  TX bytes:640952 (625.9 KB)

eth0      Link encap:Ethernet  HWaddr 00:1B:B9:64:86:13  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12768 (12.4 KB)  TX bytes:12768 (12.4 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-0F-A3-1B-72-3E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:271443 errors:0 dropped:0 overruns:0 frame:461
          TX packets:8501 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:28408789 (27.0 MB)  TX bytes:893986 (873.0 KB)
          Interrupt:19 

```

I do not experience this problem on Windows. AA is a game (America's Army). I don't think it is related to this issue.

---

### Post by drndrw on 2007-11-19
Bump again. This is turning into a big problem.

---


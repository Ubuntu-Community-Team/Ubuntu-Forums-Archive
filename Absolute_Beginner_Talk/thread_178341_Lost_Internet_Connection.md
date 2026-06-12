---
title: "Lost Internet Connection"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by billvb on 2006-05-17
Hi,

This morning I went to turn on my Ubuntu machine, and could not connect to the interenet.  Please note that every computer in my house is connected through the same router, and all of these can connect just fine.   Last night, before I turned it off, it worked fine... What could the problem be?

Thanks in advance!
-Bill

---

### Post by mjm115 on 2006-05-17
Could be your network connection on the Ubuntu machine.  When you go to a terminal and type in 'ifconfig', what do you get?

---

### Post by Iowan on 2006-05-17
What kind of router? Linksys?
[http://ubuntuforums.org/showthread.php?p=1024395]("http://ubuntuforums.org/showthread.php?p=1024395")

---

### Post by billvb on 2006-05-17
Well, its interesting. ](*,) 

When i unplug the network cable, a little error graphic appears in the notification area.  When i plug it back in, it goes away and the network connection icon lights up, but when I open up mozilla it says so and so cant be found.  When i type in ifconfig:

eth0  Link encap:Ethernet HWaddr (lots of hex)
inet6 addr: more hex Scope:Link
 UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
 RX packets: 17 errors:0 dropped:0 overruns: 0 frame:0
 TX packets: 45 errors:0 dropped:0 overruns:0 carrier:0
 collisions:0 txqueuelen:1000
 RX bytes:3487 (3.4 KiB) TX bytes:14058 (13.7 KiB)

---

### Post by Iowan on 2006-05-17
[QUOTE=billvb]inet6 addr: more hex Scope:Link[/QUOTE]
I won't guarantee this is the problem, but ipv6 has caused issues for others - there are a few threads about how to disable ipv6 around here.

---


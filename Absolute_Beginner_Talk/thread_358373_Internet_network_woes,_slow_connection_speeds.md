---
title: "Internet network woes, slow connection speeds"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by AFritzy on 2007-02-10
Hey all,

   I am brand new to Linux/Ubuntu lifestyle.  I've been trying to figure out why my connection to the Internet is being slowed down.  When I was using Windows XP, the load speeds were way faster then on the Ubuntu OS.  I've been looking around other post and can't seem to find anyone with the same problem as me. I am on a hard line network with Windows users, the routers are all Linksys, and the network is connected to a cable line.  I don't know if maybe there are firewalls on Ubuntu that is causing the backup or what. If anyone needs more info let me know, thank you bunches.

Fritzy

---

### Post by nickoli_02 on 2007-02-10
That is kind of weird. Sorry I can't help but try posting the problem in the networking forum. You may get a better response.

---

### Post by KAL9000 on 2007-02-10
I havent noticed a slow speed once its connected and Downloading something but i do get alotof 404's and timeouts under Ubuntu and pages are slow to start downloading. its like the 1st 10-20 seconds are just nothing then i get the full speed.

i am also conected via Ethernet to a ADSL modem/router and I am the only user so I know the bandwidth was there.

---

### Post by r4ik on 2007-02-10
Try,

[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)

Good luck !

---

### Post by jpeddicord on 2007-02-10
If you don't use IPv6, you can probably disable it without problems. IPv6 support has been know to slow down connections at times.

Here is a quick guide on it:
[http://ubuntuforums.org/showthread.php?t=87798](http://ubuntuforums.org/showthread.php?t=87798)

EDIT: r4ik beat me to it!

Jacob

---

### Post by skyhopper88 on 2007-02-10
Your duplex may be set to half instead of full. Try entering

> sudo ethtool - s eth0 autoneg off duplex full

That fix it?

---

### Post by KAL9000 on 2007-02-10
It looks like (although I wont get chance to try it untill tommorow) the IPV6 is the problem, its not slow, once it starts its as fast as usual, its just waiting for it to start. almost looks like extreme  package loss, if you give the F5 abit of abuse it will start abit quicker.

---

### Post by r4ik on 2007-02-10
Also try about:config in the adressbar and set the "pipe" maxrequest to 8

---

### Post by AFritzy on 2007-02-12
Thanks for all the help, i will definitely try what everyone has recommended.

Fritzy

---

### Post by keith11 on 2007-02-12
> **skyhopper88 said:**
> Your duplex may be set to half instead of full. Try entering



That fix it?

I have a similar problem and when I type "sudo ethtool -s eth1 autoneg off duplex full" as I am on wireless, i get the following error message:

Cannot get current device settings: Operation not supported
  not setting duplex
  not setting autoneg

How to solve this? Thanks.

---


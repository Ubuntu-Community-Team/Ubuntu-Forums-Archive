---
title: "tracking m/b usage in ubuntu"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by dpgraves on 2007-04-28
Want to be able to track usage on ubuntu have three machines running ubuntu all connected to switch which then connects to belkin router adsl2+.

What i am trying to do is measure m/b downloaded (tcp,udp,smtp) ideally from router itself 

few suggestions people have said to use mrtg but this only from what i have found measure speed of router connections. (which i currently have working.) not m/b downloaded.

another person suggested smoothwall or ipcop but that means another machine wife will not let that at moment.

is there a way of measuring usage on each computers or directly from router. 

two machines are running feisty (one server on desktop ) third machine is running dapper 64 

Ideally what to be able split into timed eg offpeak between 12am and 8am different to 8am to 12am and wish list exclude any downloads from certain websites eg ( repos from isp which are not counted in downloads limit)

Help on this please

---

### Post by nixclusive on 2007-04-28
..urm.. you can use the connbytes match in iptables/netfilter but that would mean a really steep learning curve. Or hey just enter: ```
sudo ifconfig 
``` and check out the RX bytes in the relevant interface. That shows the amount of data recieved through that interface. But alas, that conter is reset whenever the interface goes down.

Using iptables to count the number of bytes transferred is a real spartan approach though it has its own benifits, however, there may be other software options available.

---

### Post by 0vv1 on 2007-04-28
I don't have much experience here but a quick glance around would lead me to believe your best bets are smoothwall and/or finding a router that has that built in.

---

### Post by rolfen on 2007-06-30
Check out vnstat , it does exactly that and it's easy to use.

---


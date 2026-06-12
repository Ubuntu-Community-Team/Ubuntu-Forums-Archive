---
title: "HELP building router - cannot share internet"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by uberteknik on 2006-08-22
Hi all, i am attempting to build my first linux router and having a few issues, 

I did a fresh install of 5.10 desktop with 2 nics.
1 nic has static ip 192.168.1.1, the other has made a ppoe connection
I typed "nano firewall" at the terminal, and entered the below
[http://webcontrol.jumbahost.com/firewall.txt]("http://webcontrol.jumbahost.com/firewall.txt")
saved it, then did iptables-save | more and it seemed to register all ok.

I went to a client xp machine and find its not getting any internet? I renewed the ip etc and still nothing..

I rung a friend who told me i need to run
 **echo "1" > /proc/sys/net/ipv4/ip_forward**

I tried this and get a permission denied error? Even after adding sudo infront of it??

Where am i going wrong?

Also please dont mention firestarter, i dont want to use it.

---


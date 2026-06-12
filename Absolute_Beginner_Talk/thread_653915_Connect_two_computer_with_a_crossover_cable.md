---
title: "Connect two computer with a crossover cable?"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by jms1989 on 2007-12-30
Ok guys, I have a problem ever since I started using a crossover cable to connect my computer with another.

When my computer is running windows, all I have to do is share my wireless internet connection and the two can talk. The guest computer is able to connect to the internet.

When I'm on Ubuntu, it's a different story. I have not been able to get ubuntu to share it's internet connection for the guest computer to have access to the internet.

I need a simple and easy method to connect the two and frankly, I do not want to have to deal with the linux shell to get things going.

Please help me. :(

---

### Post by ^rooker on 2007-12-30
Hm...
It's actually so easy in the shell (using iptables) that I myself have never even looked for a GUI, but maybe this could work:
[http://news.softpedia.com/news/Share-Internet-Connection-and-Set-up-Port-Forward-with-Guidedog-50091.shtml]("http://news.softpedia.com/news/Share-Internet-Connection-and-Set-up-Port-Forward-with-Guidedog-50091.shtml")

Sometimes we shell-users just forget that "simple things" are close to "no-go's" for beginners. Sorry. :(

If "Guidedog" should not work for you, you should really try the shell - it's a breeze!

Here's how to do it the "shell" way
1) Become root: 
**sudo -i**
2) Install "iptables" (using synaptic, adept) - or run 
**apt-get install iptables**
3) Enable IP forwarding:
**echo "1" > /proc/sys/net/ipv4/ip_forward**
4) Tell iptables to masquerade and forward packets that go to your "internet interface" (e.g. ppp0, eth0 or eth1, etc...):
**iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE**
5) Assign some internal IP address to your LAN card (e.g. eth1):
**ifconfig eth0 inet 192.168.5.1 up**
6) Give the to-be-forwarded computer an IP address within the same range. e.g.: 192.168.5.2

That's it.

---

### Post by jms1989 on 2007-12-30
I tried the Guidedog way and it simple didn't work for me.

My computer is connected to the router using eth1 and the guest computer is connected to my eth0 interface. What do I have to change in your shell instructions?

---

### Post by ^rooker on 2007-12-30
**iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE**

That's it.   :)
(The above command masquerades every packet that goes out through eth1 (your router))

PS: I'm curious: If you have a router, why don't you just connect the second PC directly?

---


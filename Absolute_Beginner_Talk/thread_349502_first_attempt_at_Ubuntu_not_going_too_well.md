---
title: "first attempt at Ubuntu not going too well"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by nog on 2007-01-30
Hi,

I fairly sure I've mucked up somewhere, but anyway here goes...

I've got an old HP DL6000 onto which I installed Dapper server edition.  I've got 2 nics that seem to work fine.  One's configured to talk to my internal subnets (192.168.21.x) and the other nic is in my internet accessible subnet (192.168.27.x).  My core router knows to route  anything sent to it on this subnet out thru the firewall.  I've got 1 other linux machine (RH?) and several sun solaris8 servers in this subnet and they all can access the outside world but not my ubuntu server.

Where do I start looking for what's causing this?  The routing looks okay to me, I can ping the router, I can access the other servers in that subnet and the other subnets.  I can't ping, traceroute or tracepath.  Ftp refuses to connect to anything, unless it's in the subnet.

I'm just having a bit of a brain meltdown so any help is appreciated

ta

---

### Post by hal10000 on 2007-01-30
try ping 194.25.2.129 (this is the ip-address of the german telekom dns-server, of course you can try any other ip-address in the internet you know).
If you get an answer when pinging to an address instead of a name you might have an dns problem.
Just look into the file /etc/resolv.conf and see if there's a line like this:
```

nameserver 192.168.1.1                 (or whatever the address of your name server is)

```

---

### Post by nog on 2007-01-31
:guitar: 

sorted it.  It helps if you've got a route thru the firewall.  I was positive I had, what a prat!

thanks for you're help anyway.

---


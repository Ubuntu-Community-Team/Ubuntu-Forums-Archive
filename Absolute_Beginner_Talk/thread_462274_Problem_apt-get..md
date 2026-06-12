---
title: "Problem apt-get."
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by OmnificienT on 2007-06-02
My pc won't connect to the server. I can't download anything this way.
```

Err http://nl.archive.ubuntu.com dapper/main Packages
  Cannot initiate the connection to nl.archive.ubuntu.com:80 (2001:7b8:3:37::21: 1). - connect (101 Network is unreachable) [IP: 2001:7b8:3:37::21:1 80]

```

Does anyone know how to make it work? Either the Dutch server is down, then I'd need to connect to a different server, or it is my hardware. I'm using a WLAN repeater as wireless adapter, and connecting to a wireless ADSL modem.

---

### Post by lsalminen on 2007-06-02
Can you connect to the internet normally?

---

### Post by H.E. Pennypacker on 2007-06-02
It is likely that the server is down.  You will know for sure that the server was down at one point if it works at a later time.  Try again later.

---

### Post by useResa on 2007-06-02
AFAIK the server is still available.
BTW: You can check it by just going to the address [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com)
It gives you a possibility to go to Packages. This will give you a directory.
First choose "dists" and next "Dapper" and finally "main".
This seems to work just fine.

Have you got any other problems connecting to the internet?

---

### Post by OmnificienT on 2007-06-02
Thanks everyone for the replies! 

I think the server was probably down for maintenance, but I was beginning to worry since I hadn't been able to connect since yesterday. I think it is a bit strange, because if you look at [this]("http://noc.bit.nl/newgraph.php?caption=nl.archive.ubuntu.com&hostname=rbfs1.galilei.network.bit.nl&target=gi9-7")
link, it hasn't been offline at all.

My internet connection is a bit slow indeed yes, but I'm not sure whether or not that is my adapter, or caused by a software problem.

Edit: 
I did this in firefox:
about:config
find: ipv6
and then I changed: 
network.dns.IPv6 (value) False into True

It just did work, maybe I should disable it again.

---

### Post by OmnificienT on 2007-06-02
Well, it's not working anymore, and I can't connect to the server with firefox either, so it appears to be able to connect to the server at some times, but not at others. This is a very strange problem.

---


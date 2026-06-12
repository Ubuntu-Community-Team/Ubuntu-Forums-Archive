---
title: "help with webserver"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by gnama on 2007-01-01
I just set up my webserver, and how do I make it public? How can others view it? I have all my pages up.

---

### Post by coastdweller on 2007-01-01
Do you have a static ip? Dynamic IP?

---

### Post by LoclynGrey on 2007-01-01
[http://www.dslwebserver.com/main/fr_index.html?/main/connection.html](http://www.dslwebserver.com/main/fr_index.html?/main/connection.html)

---

### Post by coastdweller on 2007-01-01
What is unfortunate about that document is I couldnt easily see it going into DDNS which is normally the first thing people do.

Its free, its easy

Check your router OP for a DDNS client (It should be in most linksys for example,.. and netgear) and go get yourself a free hostname from [www.dyndns.com](www.dyndns.com)

You can then add the dynamic hostname and your user and pass you created at dyndns to your router. Now when your connection gets a new IP it will translate it to your free hostname.

What I do is then overlay one of my domains running on one of my datacenter servers to not have to remember the free one I get.

---

### Post by seijuro on 2007-01-01
if the router doesn't have dyndns don't worry there are a couple clients you can install on the server machine via synaptic(pkg-name: ddclient) . Also you will need to set up port forwarding on your router. If your router has it I highly recommend enabling IP reservation for your server computer as well so that at least on the lan side it will always use the same IP.

---


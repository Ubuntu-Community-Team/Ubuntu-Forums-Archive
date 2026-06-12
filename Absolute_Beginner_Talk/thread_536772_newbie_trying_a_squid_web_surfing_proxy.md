---
title: "newbie trying a squid web surfing proxy"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by tai4ji2x on 2007-08-28
trying to leap the great firewall of china...

leaving for study abroad in a couple days, so not much time...  :(

not very linux saavy anymore (played around with linux many years ago, but now i'm basically a newbie again).  installed ubuntu 7.04 desktop edition on my old IBM thinkpad.

how do i set up things like the following, but with a server whose IP isn't static?

[http://www.securityfocus.com/infocus/1508](http://www.securityfocus.com/infocus/1508)

[http://nickselby.com/articles/technology/index.htm?a=1810](http://nickselby.com/articles/technology/index.htm?a=1810)

thx

---

### Post by Malibu Illusion on 2007-08-28
If you want to browse unrestricted and have access to a box outside of China, just set that box up with SSH access and use a client like PuTtY on a Windows machine or command line on a *NIX machine to forward a port down an open tunnel and then proceed to use that as a SOCKS proxy.

```
ssh -l user -D22200 whatever.no-ip.org
```

SOCKS proxy: localhost, port: 22200 redirects down the tunnel thus granting you unrestricted, and encrypted, internet access.

You can check [here](http://www.no-ip.com) for Dynamic DNS assignment.

---

### Post by Marat Galiev on 2007-08-28
Hi guys!I need some guides to configure squid+ubuntu 7.04.
Somebody can help me?

---

### Post by tai4ji2x on 2007-08-28
thanks malibu.  just curious - what happens if no-ip.com itself gets blocked by the great firewall? :confused:

> **Malibu Illusion said:**
> 
You can check [here](http://www.no-ip.com) for Dynamic DNS assignment.

---

### Post by tai4ji2x on 2007-08-28
anyone?  just wondering what happens if the dynamic dns service also gets blocked?

---

### Post by tai4ji2x on 2007-08-28
i mean, from what i seem to be reading online, indeed if the dynamic DNS servers are blocked, it looks like my attempt to SSH would be blocked too... yes/no?

---


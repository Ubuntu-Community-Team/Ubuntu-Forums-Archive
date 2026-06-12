---
title: "howto let apt-get install go through local squid?"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by lennie2 on 2007-04-29
I have just managed to setup a Squid proxy and from my windows Pc I can see the proxy works if I do a tail on the access log, hewever how do I get the Ubuntu server to redirect it's own traffic through the squid as well ? My main idea is to cache the apt-get packages if it is needed by another ubuntu pc, will this work ?

---

### Post by piti118 on 2007-04-29
[http://ubuntuforums.org/showthread.php?t=96802](http://ubuntuforums.org/showthread.php?t=96802) <-- this might be what you need

But, you might want to look in to a program called apt-proxy. :)

---

### Post by lennie2 on 2007-04-30
Feedback to the Forum, apt-proxy works like a charm, easy to setup and I can now request all my udates from the internet through my Squid into the local repository for the other Ubuntu Pc's

Many thanks piti118

---


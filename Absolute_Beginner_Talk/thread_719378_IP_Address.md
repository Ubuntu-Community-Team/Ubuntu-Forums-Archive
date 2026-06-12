---
title: "IP Address"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by lifeinoleg on 2008-03-09
Here's a random question: How do I find out what my IP address is?

fyi: I'm running GG (7.10), fully updated.

---

### Post by banewman on 2008-03-09
If you type in a terminal - 
ifconfig
- you will get to see the ip address for your nic.
:)

---

### Post by RSLxH on 2008-03-09
> **lifeinoleg said:**
> Here's a random question: How do I find out what my IP address is?

fyi: I'm running GG (7.10), fully updated.

I suppose you mean your external ip:
[http://whatsmyip.org/](http://whatsmyip.org/)

---

### Post by russell.h on 2008-03-09
```
wget http://whatismyip.org; cat index.html
```
Will print your external IP on the last line of the output.

If you are interested in your local IP (if you are behind a router using NAT) use
```
ifconfig
```

---

### Post by lifeinoleg on 2008-03-09
Thanks everyone, that was fast!

Gotta love this forum.

---


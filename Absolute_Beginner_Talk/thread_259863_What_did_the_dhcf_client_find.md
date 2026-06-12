---
title: "What did the dhcf client find"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by rccharles on 2006-09-18
I would like to know what the dhcf client found out.  The ifconfig command will return some of the parameters. 

But how do I find out about the dns address or the gateway address?  


Robert

---

### Post by cwaldbieser on 2006-09-18
> **rccharles said:**
> I would like to know what the dhcf client found out.  The ifconfig command will return some of the parameters. 

But how do I find out about the dns address or the gateway address?  


Robert

Try "route" to find out your gateway(s).
I think maybe /etc/resolv.conf has your nameservers in it.

---


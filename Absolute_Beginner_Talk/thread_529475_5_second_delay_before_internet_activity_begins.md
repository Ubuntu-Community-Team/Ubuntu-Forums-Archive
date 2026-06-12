---
title: "5 second delay before internet activity begins"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by mithun1217 on 2007-08-19
Hi!  I'm new to Ubuntu and I'm really excited about exploring Linux.  I'm having only one problem as of now.  Each time I type a URL into the address bar of my browser (Firefox), there is a 5 second delay before all the "Connecting to......" and "Transferring data from...." stuff happens.  Once it starts data transfer, though, everything is pretty smooth.  This happens in both Edgy and Feisty.  How do I eliminate this 5 second delay?

---

### Post by por100pre1 on 2007-08-19
I suspect this could be an issue with the domain name server of your internet provider. Try adding 208.67.222.222 and 208.67.220.220 to the DNS servers of your network configuration. Let us know if it works. :-k

---

### Post by mithun1217 on 2007-08-19
Hi!  Thanks for responding!  I never had this problem in Windows, so I think the DNS servers are not the cause.

---

### Post by por100pre1 on 2007-08-19
I was thinking on the DNS because i had a similar issue and I fixed it adding the DNS servers manually. No problems in Windows neither. :-k

---

### Post by lambros on 2007-08-19
It might be an IPv6 issue.  I had a similar problem when I changed my ISP and my router.  This link has more info:
[http://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](http://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

Lambros

---


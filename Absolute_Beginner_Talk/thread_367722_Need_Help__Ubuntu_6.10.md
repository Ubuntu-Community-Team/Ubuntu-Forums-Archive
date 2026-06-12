---
title: "Need Help / Ubuntu 6.10"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by gmutt on 2007-02-22
.

---

### Post by igknighted on 2007-02-22
What happens if you open a terminal and type:
```
ping -c 5 www.gentoo.org
```

---

### Post by mahy on 2007-02-22
I guess you meant Firefox web browser ;)

Try some other programs, and if nothing works, tell us about your network connection.

---

### Post by gmutt on 2007-02-22
.

---

### Post by mahy on 2007-02-22
> **gmutt said:**
> Ping was done through live CD session as I can't access Internet otherwise, don't know if that matters.

It does. Please try the ping in your installed version of Ubuntu, to make sure. Let us know.

---

### Post by gmutt on 2007-02-22
.

---

### Post by gmutt on 2007-02-22
.

---

### Post by gmutt on 2007-02-22
.

---

### Post by mahy on 2007-02-22
No i haven't. :-P The post from your ping clearly reveals that your machine DOES have internet access. The problem is solely within firefox. Open about:config in firefox and put number '6' to the filter. Then doubleclick the line containing IPv6 (it should turn **bold** as a result).

---

### Post by gmutt on 2007-02-22
.

---

### Post by gmutt on 2007-02-22
.

---

### Post by gmutt on 2007-02-22
.

---

### Post by Maestro23 on 2007-02-22
> **gmutt said:**
> Ok, have no clue what you just said:

Open about:config in firefox and put number '6' to the filter. Then doubleclick the line containing IPv6 (it should turn bold as a result).


Could not find any such folder - novice at work here

Maybe a screen shot of what Firefox does will help.


/media/hdb1/Screenshot.png


Don't know if this will work but ... Never know unless I try

In the address window, type: **about:config**

Scroll down until you find **network.dns.disableIPv6**

Double click it, it should then say: **TRUE.**

Restart Firefox.

---

### Post by mahy on 2007-02-22
Exactly. Type "about:config", just like any other URL. It should become clear then :)

---

### Post by HereInOz on 2007-02-22
Sounds like a DNS problem.  Try setting a static IP address in System > Aministration > Networking, and then set your DNS servers to the IP addresses given you by your ISP.

This is a common issue with some router/modems and Ubuntu, and it often solves the problem of "Firefox not working"

---

### Post by gmutt on 2007-02-22
.

---

### Post by austinw on 2007-02-22
Try typing "about:config" without quotes into the address bar in firefox, then follow his instructions.

---


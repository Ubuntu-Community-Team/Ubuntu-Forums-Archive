---
title: "help me finding a software"
date: 2015-07-05
forum: Any Other OS
---

### Post by -@23%^yu* on 2015-07-05
Is there a software where I can log websites that each user on the  network has visited? Something like DMA radius Connection Tracking  System(CTS). I can log both web sites visited and also the port numbers.

---

### Post by TheFu on 2015-07-06
Only the edge router has this data, so you need to get the data from it.  SNMP is the normal way. Setting up a remote rsyslog from the router is normal.

Of course, if you have a proxy server, which is mandatory on the network, those logs will have that data too. If a transparent proxy is used, then userids won't be known, but you can setup the proxy to require user authentication, which can be logged. squid is the normal proxy for Unix systems.

---

### Post by Bucky Ball on 2015-07-06
As you give no indication of what operating system you are using a bit impossible to answer your question. Are you the network admin and have control over this local area network? Which OS are you using?

---

### Post by -@23%^yu* on 2015-07-06
> **Bucky Ball said:**
> As you give no indication of what operating system you are using a bit impossible to answer your question. Are you the network admin and have control over this local area network? Which OS are you using?
i'm using ubuntu 12.04 lts. yes i'm network admin.

---

### Post by SeijiSensei on 2015-07-06
If all you need to do is identify which IP addresses made which requests, then a transparent Squid proxy would be all you need.  If users roam around and use various devices, you'd need to require authentication in Squid as well.

---

### Post by -@23%^yu* on 2015-07-09
> **SeijiSensei said:**
> If all you need to do is identify which IP addresses made which requests, then a transparent Squid proxy would be all you need.  If users roam around and use various devices, you'd need to require authentication in Squid as well. After searching on the web for some time i found that ntopng is the program that suits my needs. Thank you.

---

### Post by TheFu on 2015-07-09
> **abdieltatpati said:**
> After searching on the web for some time i found that ntopng is the program that suits my needs. Thank you.

Thanks for posting what you've decided. That tool looks VERY COOL, indeed. If you could post a follow up in a week, that would be great, but I completely understand if that isn't possible.

---


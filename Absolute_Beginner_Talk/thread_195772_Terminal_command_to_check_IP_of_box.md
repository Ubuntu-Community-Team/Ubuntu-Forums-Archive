---
title: "Terminal command to check IP of box?"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by u.b.u.n.t.u on 2006-06-13
Hi,

I want to check the IP address of one of my LAN computers. Is there a terminal command for that?

Thanks.

---

### Post by halfvolle melk on 2006-06-13
ifconfig / iwconfig
ip addr show
ip route

edit: check man ip for lots of nifty options.

---

### Post by u.b.u.n.t.u on 2006-06-13
Thank you, halfvolle melk

```
ip route
``` does the job. I'll check out the manual too.

---


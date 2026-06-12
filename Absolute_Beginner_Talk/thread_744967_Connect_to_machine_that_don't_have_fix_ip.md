---
title: "Connect to machine that don't have fix ip?"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by peterlauri on 2008-04-04
Hi,

How can I some how connect to another machine that doesn't have a fix ip? Microsoft have some "remote assistance" things, anything similar in Ubuntu?

Basically I will leave my girlfriend alone with her Ubuntu for a while, and I need to be able to at least connect via SSH to her. But we don't have fix IP, and the computer is behind another router as well.

/Peter

---

### Post by bluefrog on 2008-04-04
you could use dyndns service (or any other dynamic IP service) with ddclient on your ubuntu machine. You can configure ddclient to fetch your public IP from your router and send it to dyndns.

James Dupin

---

### Post by peterlauri on 2008-04-04
Hi,

dyndns.com works. And the ddclient is updating info correctly, now another problem:

I cannot ssh to the machine, it gives "connection refused", how can this be fixed?

/Peter

---


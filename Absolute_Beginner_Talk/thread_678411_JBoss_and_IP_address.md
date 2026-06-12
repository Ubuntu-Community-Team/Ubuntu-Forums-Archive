---
title: "JBoss and IP address"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by toolips on 2008-01-25
I installed JBoss 4.2.2 on a machine with an IP address of 192.168.1.200.  (Running 6.06)

To see the JBoss admin page I  can get there by going to [http://localhost:8080](http://localhost:8080) or [http://127.0.0.1](http://127.0.0.1) ... but not by [http://192.168.1.200:8080](http://192.168.1.200:8080).  Why?  Since I can't display the page with that URL I can't get another machine on my network to display it either.

How can I fix this?

---

### Post by PeterJS on 2008-01-25
It's not broken, it's supposed to be that way. Most packages that offer a web configuration interfaces, have them default to only have the server listen on the lo interface. This is so that random machines on the local network segment can't access the configuration page. If you want to access the page remotely your best (and safest) bet is to install sshd on the machine and use putty to tunnel in to the machine to access the webconfig page remotely.

---

### Post by mortsahl on 2008-01-26
Thanks ... for futher reference ... the real answer turns out to be that, as of JBoss 4.2.0, the server is locked to localhost.  To access it via it's IP address you must start it with "./run.sh -b 0.0.0.0"

---


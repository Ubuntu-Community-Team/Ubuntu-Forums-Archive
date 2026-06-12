---
title: "Change MTU And Keep The Change"
date: 2008-12-04
forum: BSD
---

### Post by Vince4Amy on 2008-12-04
How can I change the MTU on DesktopBSD And make it keep the change?

On Linux I would put:

ifconfig eth0 mtu 1492 in /etc/rc.local

On DesktopBSD where would I put the command so it runs on boot?

---

### Post by LateNiteTV on 2008-12-04
make it a .sh script and put it in /etc/rc.d

---


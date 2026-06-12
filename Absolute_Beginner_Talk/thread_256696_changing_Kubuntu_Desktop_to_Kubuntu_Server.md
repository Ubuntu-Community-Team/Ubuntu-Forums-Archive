---
title: "changing Kubuntu Desktop to Kubuntu Server?"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by tobmeister on 2006-09-13
Hey Gang,

How would one change a sytem from the desktop invironment to the server environment?

Would we just go to snaptic and add what ever server we want to use, and then just simply implement it?

Thanks

Tobmeister

---

### Post by whizbaby on 2006-09-13
*Server* usually means
(1)having the services you need installed 
(2)every not substantially needed program is a potential security risk (so no x-server and no GUI programs).

So for a secure server you would need to disable the x-server (either uninstall or better move the */etc/X11/xorg.conf* to e.g. */etc/X11/xorg.conf.saved* so the x-server won't start but you can get it back quickly if you want) and decide what services you want to provide.

---

### Post by Klaidas on 2006-09-13
I myself would either:
a) Install ubuntu server iso with LAMP
b) Read [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) and add server applications to the existing desktop.

---


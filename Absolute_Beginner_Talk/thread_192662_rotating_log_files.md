---
title: "rotating log files"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by x96riley3 on 2006-06-09
I wrote a little script that rotates my /var/log/auth.log when it get's to a certain size. I move the file to a new name and then I do a touch auth.log again.  However, nothing writes anymore to my auth.log until I reboot the server.  I'm guessing I need to restart a process but I don't know which one.  Any help would be apperciated.

Thanks,
-X

---

### Post by nanotube on 2006-06-09
[QUOTE=x96riley3]I wrote a little script that rotates my /var/log/auth.log when it get's to a certain size. I move the file to a new name and then I do a touch auth.log again.  However, nothing writes anymore to my auth.log until I reboot the server.  I'm guessing I need to restart a process but I don't know which one.  Any help would be apperciated.

Thanks,
-X[/QUOTE]
ehrm, the ubuntu syslog setup already automatically rotates logs, so there is no need to make your own script to do that. just so you know...

as to nothing writing to it... are you sure that when you touch a new auth.log, it has the right permissions? just a guess on my part, but doesn't hurt to check.

---


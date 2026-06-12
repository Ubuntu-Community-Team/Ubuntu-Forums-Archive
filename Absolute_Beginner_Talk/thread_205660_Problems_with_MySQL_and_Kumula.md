---
title: "Problems with MySQL and Kumula"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by spyke01 on 2006-06-28
Im trying to install kumula, a business suite for linux and KDE. Im using gnome, but have been able to get some KDE apps to work in the past, anyways i installed mysql and kumula's dependencies, set the root password, and ran the queries. When i run its connection script, it says it cant connect as root on localhost:3306

i checked/etc/mysql/my.cnf and it shows its binded to port 3306 on 127.0.0.1, i also ran sudo /etc/init.d/mysql restart and it successfully restarts, still no go. from there i ran netstat -tap and i have this:
tcp        0      0 localhost:mysql         *:*                     LISTEN     -


anyone have any ideas?

---


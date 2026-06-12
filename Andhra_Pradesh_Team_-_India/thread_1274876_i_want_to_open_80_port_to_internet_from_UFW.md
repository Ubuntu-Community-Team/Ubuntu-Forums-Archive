---
title: "i want to open 80 port to internet from UFW"
date: 2009-09-25
forum: Andhra Pradesh Team - India
---

### Post by csejo123@yahoo.com on 2009-09-25
dear all
i am using mtnl triband ppp0 connection i want open  80
port form external
i have tried  everything but it going thru

please help

 ufw status
Status: active

To                         Action  From
--                         ------  ----
22                         ALLOW   Anywhere
8080                       ALLOW   Anywhere
3128                       ALLOW   Anywhere
Anywhere                   ALLOW   192.168.0.0
Anywhere                   ALLOW   59.181.0.0
Anywhere                   ALLOW   59.181.129.36
Anywhere                   ALLOW   10.100.100.1
Anywhere                   ALLOW   192.168.1.194
Anywhere                   ALLOW   0.0.0.0
Anywhere                   ALLOW   10.100.100.4
Anywhere                   ALLOW   10.100.100.0
Anywhere                   ALLOW   192.168.1.0
10.100.100.1               ALLOW   192.168.1.194
80/tcp                     ALLOW   59.181.129.36
25                         DENY    Anywhere
110                        DENY    Anywhere
80                         ALLOW   Anywhere
443                        ALLOW   Anywhere
Anywhere                   ALLOW   192.168.1.194 80
Anywhere                   ALLOW   0.0.0.0 80
80                         ALLOW   59.181.129.36

---


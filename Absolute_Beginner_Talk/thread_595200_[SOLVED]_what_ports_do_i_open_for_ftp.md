---
title: "[SOLVED] what ports do i open for ftp"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by jtann on 2007-10-28
what ports do i open for in router for ftp to work. i have installed vsftpd but not getting ftp connection made

---

### Post by MegaJim on 2007-10-28
port 21 for unsecured ftp

for future ref. [http://www.iana.org/assignments/port-numbers](http://www.iana.org/assignments/port-numbers)

---

### Post by haldean on 2007-10-28
normally, ftp connections are made to port 21

---

### Post by jtann on 2007-10-28
Resolving host name "xx.xx.xx.xx"
[15:33:04] Connecting to xx.xx.xx.xxPort: 21
[15:33:04] Connected to xx.xx.xx.xx.
[15:33:05] An established connection was aborted by the software in your host machine.

this is what my ftp program says any thoughts where my problem is

---

### Post by Pumalite on 2007-10-28
[http://www.cyberciti.biz/faq/ubuntu-vsftpd-ftp-service-server/](http://www.cyberciti.biz/faq/ubuntu-vsftpd-ftp-service-server/)

---

### Post by jtann on 2007-10-28
this all looks good if i do a run from my other windows machine it says connected then disconnected. something is stopping me from connecting on the ftp server.

---

### Post by haldean on 2007-10-28
are you trying to connect from outside your LAN or within?
it also could be a problem with a firewall on the computer with the server on it.

---

### Post by jtann on 2007-10-28
i am inside lan ftp program with outside ip address to get there.
as far as i know there is no firewall on server i installed server cd, but did not setup firewall. i turned off firewall on xp and now i get message. 
""No connection could be made because the target machine actively refused it""
instead of ""An established connection was aborted by the software in your host machine.""
any ideas

---


---
title: "proftpd"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by mikejose on 2007-10-14
I'm a newbie. just configured proftpd on my ubuntu and i can successfully logged on my ftp using an internet connection without proxy but when  used proxied internet connection i can't log. i disabled the anonymous account on my ftp server.

---

### Post by mendingo84 on 2007-10-14
it may well be that the Proxy doesn't allow FTP connections ( filtering the 20 and 21 port )

---

### Post by bobbocanfly on 2007-10-14
ProFTPd may be bound to only accept connections from some IP's. Make sure server is allowed in the /etc/froftpd file.

---


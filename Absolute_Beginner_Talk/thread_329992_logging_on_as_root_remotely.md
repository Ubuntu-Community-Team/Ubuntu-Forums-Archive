---
title: "logging on as root remotely"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by gecici on 2007-01-02
Hi guys,

URGENT, URGENT, URGENT!!!

Can anybody please please tell me how to log on as 'root' remotely on Ubuntu 6.06 server?

Thanx

---

### Post by Iarwain ben-adar on 2007-01-02
Hiya,
log in via ssh as a normal user, and then type this
```
sudo su -
```


Iarwain

---

### Post by rccharles on 2007-01-02
> **gecici said:**
> Hi guys,

URGENT, URGENT, URGENT!!!

Can anybody please please tell me how to log on as 'root' remotely on Ubuntu 6.06 server?

Thanx

logon to your remote server.

Not sure the difference but this has a powerfull effect:
When asked for the password, type your remote logon passward.  You will have to be in the sudoers file.
sudo bash


...

exit 

when done.

Robert

---


---
title: "new to linux, dont have permission to move a file?"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by ex4n on 2007-05-01
Hi there..
im trying to move a file
patrick@EXAN:~$ cp file /etc/ppp/ip-up.d/
but it says i dont have permission
i am using the account i made when i installed and i have all permissions checked in users and groups->properties.
i tried to log out and log in as the root user but it said the root user isnt allowed to log in like that,,

please help

---

### Post by taurus on 2007-05-01
```
**sudo** cp file /etc/ppp/ip-up.d/
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ex4n on 2007-05-01
sudo = super user do?
thankyou for this.

---

### Post by clevin on 2007-05-01
I normally install **mc** (midnight commander) from official repositories first, then do sudo mc, that feels easier

---


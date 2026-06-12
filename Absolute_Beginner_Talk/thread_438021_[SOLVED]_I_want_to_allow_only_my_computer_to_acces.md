---
title: "[SOLVED] I want to allow only my computer to access my apache server."
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by Masoris on 2007-05-09
I installed Apache server in my desktop ubuntu.
Because it is server it can be access from other computer as default.
But I want to use my server only for me, I want to deny all access from other computer.
I want to allow to access from only localhost (in my computer) and some my friends computer.
How can I deny all connection to my server, except few selected IP?

---

### Post by Ozeuss on 2007-05-09
```
gksudo "gedit /etc/apache2/ports.conf"

```
Change ports.conf so that it contains:
Listen 127.0.0.1:80

this will make apache listen only to your IP. haven't tried it with other ip's but i guess its similar.

---

### Post by Masoris on 2007-05-10
> **Ozeuss said:**
> ```
gksudo "gedit /etc/apache2/ports.conf"

```
Change ports.conf so that it contains:
Listen 127.0.0.1:80

this will make apache listen only to your IP. haven't tried it with other ip's but i guess its similar.

Thank you, It works !!

---


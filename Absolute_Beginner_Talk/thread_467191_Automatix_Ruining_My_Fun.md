---
title: "Automatix Ruining My Fun"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by Mac70 on 2007-06-07
I uninstalled said application because whenever I tried to update I got the "public key" error message. I read through numerous threads but nothing worked. Even though its uninstalled I still get the bloody message.
How do I stay updated with that blocking my efforts?

---

### Post by Outrunner on 2007-06-07
You have to remove the Automatix2 entries from your sources.list

```
gksudo gedit /etc/apt/sources.list
```
```

sudo aptitude update
```

---

### Post by Mac70 on 2007-06-07
Perfect. Thanks Outrunner.

---


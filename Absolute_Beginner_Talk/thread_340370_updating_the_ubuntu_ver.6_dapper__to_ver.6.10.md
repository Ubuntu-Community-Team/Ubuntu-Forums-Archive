---
title: "updating the ubuntu ver.6 dapper  to ver.6.10"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by micro_xii on 2007-01-17
Greetings:

I install the ubuntu 6 dapper. Recently, I download the latest version 6.10 desktop. I just want to know how to update my ubunto 6 to 6.10.


thanks....:mrgreen:

---

### Post by migla on 2007-01-17
According to [this howto]("https://help.ubuntu.com/community/EdgyUpgrades"), you just need to type the following into a terminal or in the box that pops up when you press [Alt]+[F2] :

```
gksu "update-manager -c"
```

They also say that for upgrading from cd, you must use the alternate cd, not the desktop cd.

---


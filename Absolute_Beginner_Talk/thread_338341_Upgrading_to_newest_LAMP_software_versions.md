---
title: "Upgrading to newest LAMP software versions"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by wdarab on 2007-01-14
I downloaded .iso for 6.10 server (Ubuntu), and installed it, chose LAMP server installation. I saw that there are outdated versions of Php, Apache and MySQL on the .iso. How do I downloaded the very updated versions of Php/Apache and MySQL?

Any help is truly appreciated.
W

---

### Post by Iarwain ben-adar on 2007-01-14
Hiya,
try this
```
sudo aptitude update && sudo aptitude upgrade
```

This will update and upgrade your system :D


Iarwain

---

### Post by wdarab on 2007-01-14
Thanks! I'll def try that tonight and see if it works!  :) 

Thanks again,
W.

---

### Post by wdarab on 2007-01-14
Iarwain,
btw, will that upgrade all of Apache, MySQL and Php software versions?

W

---

### Post by Iarwain ben-adar on 2007-01-14
It will upgrade EVERY package currently installed on your system :wink:
(unless you hold them, but no worries)


Iarwain

---

### Post by wdarab on 2007-01-14
beautiful! I'll def try tonight.

Thanks,
W

---


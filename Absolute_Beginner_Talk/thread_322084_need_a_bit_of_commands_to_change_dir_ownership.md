---
title: "need a bit of commands to change dir ownership"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by zetsumei on 2006-12-19
I need some help with the chown command to give rights to read/write/execute files and create/delete files/folders in /var/www/ how would I use the chown command to do this?

---

### Post by meng on 2006-12-19
chown changes ownership
chmod changes permissions
man chown
man chmod
is the quick and dirty answer.

---

### Post by aysiu on 2006-12-19
```
sudo chown -R zetsumei:zetsumei /var/www
```

---

### Post by bodhi.zazen on 2006-12-19
> **zetsumei said:**
> I need some help with the chown command to give rights to read/write/execute files and create/delete files/folders in /var/www/ how would I use the chown command to do this?

use chmod

sudo chmod xyz /var/www/
x = owner
y = group
z = others (all users)

use chown to change owners

sudo chown user:group <file>

---


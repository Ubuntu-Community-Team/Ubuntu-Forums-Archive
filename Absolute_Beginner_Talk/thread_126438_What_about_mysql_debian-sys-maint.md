---
title: "What about mysql: debian-sys-maint?"
date: 2006-02-06
forum: Absolute Beginner Talk
---

### Post by foov2 on 2006-02-06
I noticed after install mysql-server and adding a all privledges user account that there is another account previously setup: debian-sys-maint.

It seems to me that this account should be deleted?

Am I missing something here?

Thanks

---

### Post by lptr on 2006-02-07
/etc/mysql/debian.cnf

```
# Automatically generated for Debian scripts. DO NOT TOUCH!
[client]
host     = localhost
user     = debian-sys-maint
password = xxxxxxxxxxx
socket   = /var/run/mysqld/mysqld.sock
```

all clear?


rob*/

---


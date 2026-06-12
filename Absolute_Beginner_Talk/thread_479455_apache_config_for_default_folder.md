---
title: "apache config for default folder"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by uraliss on 2007-06-20
Hi Folks
Can someone remind me what setting i need to change so that I can host my web pages from folders other than the standard var\www

Many thanks

---

### Post by PetePete on 2007-06-20
DocumentRoot in httpd.conf

(at least in apache 1.x)

cat /etc/apache/httpd.conf | grep -n /var/www

---

### Post by asommer on 2007-06-20
Also, take a look the **DocumentRoot** at:

```
/etc/apache2/sites-available/default
```

---


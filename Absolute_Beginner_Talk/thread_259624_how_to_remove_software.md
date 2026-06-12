---
title: "how to remove software"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by rackne on 2006-09-17
im a linux newbie so my question for some might be a bit silly. anyway, i'd like to know how to remove software using console? what are the basic commands for this?

---

### Post by rackne on 2006-09-17
doh! i forgot to subscribe. please, ignore this.

---

### Post by jordanmthomas on 2006-09-17
```
sudo aptitude remove packagename
```
will get rid of a package
```
sudo aptitude purge packagenmae
``` will remove the program and its configuration files...in case you messed one up and need to reinstall something.

---

### Post by rackne on 2006-09-17
thanks a lot. i'll give it a try.

---


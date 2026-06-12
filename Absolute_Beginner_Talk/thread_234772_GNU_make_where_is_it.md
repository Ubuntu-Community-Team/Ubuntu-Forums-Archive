---
title: "GNU make: where is it?"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by jedsen on 2006-08-12
I don't seem to have GNU make installed on my system. When I type "make" I get a "command not found"? What package is it included in?

---

### Post by Jagot on 2006-08-12
You can install the package 'make' on its own if you want to, but probably best is to install 'build-essential' as it comes with compilers you'll need to build from source:

```
sudo aptitude update
sudo aptitude install build-essential
```

---


---
title: "how to find installed date of ubuntu ?"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by addict3d on 2006-11-08
Hello, i want to find the date on which i installed ubuntu. How do i do this ? Any command available ? Thanks a lot

---

### Post by bodhi.zazen on 2006-11-08
ls -l /etc

Look for the earliest date ?

---

### Post by 23meg on 2006-11-08
```
grep ubiquity /var/log/installer/syslog | less
```should give you an idea. You'll need to be root.

---

### Post by addict3d on 2006-11-08
> **bodhi.zazen said:**
> ls -l /etc

Look for the earliest date ?

Thanks for the reply, but that showed some very old dates (even 1995,2003) .:confused: .Maybe i did something wrong (or maybe i should look for dates in 2006 only :D  ?) ?

> **23meg said:**
> ```
grep ubiquity /var/log/installer/syslog | less
```should give you an idea. You'll need to be root.

That worked a treat ! Thanks :cool:

---


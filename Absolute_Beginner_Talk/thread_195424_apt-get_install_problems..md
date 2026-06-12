---
title: "apt-get install problems."
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by chris062689 on 2006-06-12
chris@chris-desktop:~$ sudo apt-get install bum
Reading package lists... Done
Building dependency tree... Done
Package bum is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package bum has no installation candidate


How can I install BUM?

---

### Post by nalmeth on 2006-06-12
to find the real package, try:
apt-cache search bum

---

### Post by johnc4510 on 2006-06-12
Bum is available in the universe repositories. Have you enabled the universe and multiverse repositories? If not and you need help with that, post back here and I'll help you.

---

### Post by aysiu on 2006-06-12
You probably have conflicting repositories.

Get a fresh list:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Then try again.

---

### Post by chris062689 on 2006-06-12
I did what aysui said, and it still doesn't work.  :-({|=

---

### Post by aysiu on 2006-06-12
After you update your sources, you need to issue two commands: ```
sudo aptitude update
sudo aptitude install bum
```

---


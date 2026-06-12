---
title: "How do i install vidalia"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by synt4xerr0r on 2006-12-18
How do i install vidalia or tor with privoxy

---

### Post by pormogo on 2006-12-18
open a terminal, apt-get -u update

then do an apt-cache search tor (or vidalia or whatever) when you find the package you want.

apt-get install [package name]

---

### Post by synt4xerr0r on 2006-12-18
> **pormogo said:**
> open a terminal, apt-get -u update

then do an apt-cache search tor (or vidalia or whatever) when you find the package you want.

apt-get install [package name]

i dont seem to be getting it to run

---

### Post by bodhi.zazen on 2006-12-18
[http://ubuntuforums.org/showthread.php?t=287349](http://ubuntuforums.org/showthread.php?t=287349)

I am not sure it works for Dapper :(

---

### Post by tbroderick on 2006-12-18
sudo aptitude install tor

Vidalia is not in the repo. So either use google and try to find a .deb or compile from source.

You might want to check out this post;

[http://ubuntuforums.org/showthread.php?t=95527](http://ubuntuforums.org/showthread.php?t=95527)

---


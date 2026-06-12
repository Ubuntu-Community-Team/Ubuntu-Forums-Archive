---
title: "About &quot;check forced&quot; off harddrive."
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by _sAm_ on 2007-06-13
Every 22 time I boot Ubuntu there is a program that checks the harddrives(check forced). Is it possible to get the check when I turn the computre off, and not when I trun it one(and want to use it).

Thanks for any answers!

---

### Post by Cypher on 2007-06-14
There is usually no problem, a quick check is performed each time you mount the partitions, and every so interval a full check is forced to make sure everything is OK. This is done before mounting the partitions. This is perfectly normal and keeps things in proper shape. If you were to start your computer once a day, you will essentially be doing a check once a month and that isn't too much of a hassle, I imagine..

You can change the interval of the forced checks with the "tune2fs" program, but don't change it to something extremely long to avoid doing these checks.

---

### Post by lazyart on 2007-06-14
Just leave it running is my solution.

---

### Post by drs305 on 2007-06-14
Check out this thread. It includes options to check the disks at shutdown, which I think is what you are looking for:

[https://wiki.ubuntu.com/AutoFsck](https://wiki.ubuntu.com/AutoFsck)

There is a spinoff page with a bit more information here:
[https://wiki.ubuntu.com/AutoFsckspec](https://wiki.ubuntu.com/AutoFsckspec)

---


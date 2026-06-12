---
title: "Firefox segfaulting?"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by Kurt` on 2006-04-10
I've been running Firefox 1.0.7 for about a month with no issues.

Rebooted today, haven't changed anything, and this happens:

> kurt@spark:~$ firefox
*** loading the extensions datasource
*** loading the extensions datasource
Segmentation fault

I deleted (after making a backup) ~/.mozilla, as I assumed it was an extension problem. It still segfaults. If I try to launch firefox as root, it says "illegal instruction" instead of segfault.

Ideas?

---


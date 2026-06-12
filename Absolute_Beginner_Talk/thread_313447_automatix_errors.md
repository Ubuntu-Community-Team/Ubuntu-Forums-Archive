---
title: "automatix errors"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by charles.g.moore on 2006-12-06
I keep getting a fatal error when automatix tries to grab certain things here is the output of the log

!!SCRIPT OUTPUT END!!
[12/05/2006 - 23:37.31] - ERRORS OR WARNINGS WHERE REPORTED
[12/05/2006 - 23:37.31] - FATAL - Extra Fonts - An apt-based error occured and installation was unsuccessful
[12/05/2006 - 23:46.02] - !!Starting Automatix 1.1-2.1!!
[12/05/2006 - 23:46.12] - Updated APT
[12/05/2006 - 23:46.22] - !!SCRIPT OUTPUT START!!
Reading package lists... Done
Building dependency tree... Done
Package msttcorefonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package msttcorefonts has no installation candidate

any ideas???

Fresh install of 6.06

---

### Post by kakalaky on 2006-12-06
Try this in a terminal:

```
sudo apt-get install msttcorefonts
```

---


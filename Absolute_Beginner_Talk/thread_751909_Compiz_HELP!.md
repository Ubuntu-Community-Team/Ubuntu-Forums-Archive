---
title: "Compiz HELP!"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by Bender 3000 on 2008-04-11
Hello. I had compiz working today then I updated it through update manager and it messed up the whole thing I had fusion running too.  I have tried reinstalling twice and complete removal and install twice.  My kernel is 2.6.24.14 Ubuntu 7.10, I don't know what version it was upgraded to though.:mad:

---

### Post by wolfen69 on 2008-04-11
> My kernel is ***2.6.24.14*** Ubuntu 7.10

did you upgrade to hardy?

---

### Post by NightwishFan on 2008-04-11
I will do my best to solve your issue. What exactly is broken, be more specific. First check to see if you have direct rendering enabled.
```
glxgears
```
It should be the third line, if not then you likely do not which means you have to install the restricted drivers.

---

### Post by Bender 3000 on 2008-04-11
Yes it is enabled, it doesn't seem to work at all I installed CompizConfig Settings manager after the update to it it quit working, also the command ```
sudo compiz
``` just seems to hang

---

### Post by eternicode on 2008-04-11
Try
```

compiz --replace &

```
?

---


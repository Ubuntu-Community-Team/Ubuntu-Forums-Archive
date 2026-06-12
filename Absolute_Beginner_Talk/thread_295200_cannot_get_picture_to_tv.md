---
title: "cannot get picture to tv"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by ziraff on 2006-11-07
i'm having VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter integrated graphic card on my laptop and i'm not able to see picture on tv.

with winxp i can do it but not with ubuntu. (i also updated 6.06 to efty but it didn't help:()

---

### Post by ziraff on 2006-11-08
anyone?

---

### Post by findus on 2006-11-08
Are you using an ati graphics card using fglrx?

If so, type

```
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```

HTH

Fin

---

### Post by ziraff on 2006-11-08
aticonfig didn't work for me (command not found.)

---


---
title: "After Restoring Xorg"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by vendetta23 on 2007-12-15
I did something with the Xorg file and messed it up. So I restored it with the command that contained dpkg in it. Everything seems to be working except that my graphics are really laggy. Is that because my video card isn't working?

Help would be appreciated!

---

### Post by erfahren on 2007-12-15
post the output of 
```

lspci

```
(actually just the "VGA compatible controller:" line would be good)

and:
```

cat /etc/X11/xorg.conf

```

---


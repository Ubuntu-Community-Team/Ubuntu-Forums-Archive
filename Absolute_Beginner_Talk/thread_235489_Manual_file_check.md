---
title: "Manual file check"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by Clive_ on 2006-08-13
On a recent boot up Ubuntu(6.06) forced a file check.
Is there a way to perform this check on demand?
thank you

---

### Post by Jeroen Vernooij on 2006-08-13
The app is called ```
tune2fs
``` but I don't know the correct usage. It can only check unmounted partitions as far as I know, so you should run it under a commandline-session.

---

### Post by SavageBeginner on 2006-08-13
In Terminal:
```
sudo shutdown -Fr now
```
To learn more:
```
man shutdown
```

---

### Post by Clive_ on 2006-08-17
Works like a charm.

Thank you!

---


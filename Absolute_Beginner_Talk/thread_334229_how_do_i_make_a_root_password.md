---
title: "how do i make a root password?"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by wannaBeHacker on 2007-01-08
Can someoen please tell me how i change/add  the/a root password through terminal?

THANKS!

---

### Post by seuaniu on 2007-01-08
Open up a terminal, and type:

```
sudo passwd root
```

You'll be asked for your password (to become root), then asked to enter the new root password twice.  After that, you'll have a root password.


FWIW, sudo is there for a reason.  It acts as a bit of a cushion from running things as root and potentially messing up your system.  If you can stand using it, sudo is preferred to su.

---


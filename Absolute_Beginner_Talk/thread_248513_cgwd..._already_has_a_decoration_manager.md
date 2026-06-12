---
title: "cgwd... already has a decoration manager"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by srusso on 2006-09-01
srusso@Prometheus:~$ cgwd
cgwd: Screen 0 on display ":1.0" already has a decoration manager; try using the --replace option to replace the current decoration manager.

What do I do here?

---

### Post by hanzomon4 on 2006-09-01
What are you using to start compiz?
Try this ```
cgwd --replace &
```

---

### Post by TFX360 on 2006-09-01
> **srusso said:**
> srusso@Prometheus:~$ cgwd
cgwd: Screen 0 on display ":1.0" already has a decoration manager; try using the --replace option to replace the current decoration manager.

What do I do here?

The answer is given by the output. Why start cgwd like this?

gnome-window-decorator is automatically active that is why it has to be replaced.

---

### Post by hanzomon4 on 2006-09-01
It might not be that simple, I forgot about this issue a user had on the compiz forums. [compiz ran for awhile, then crashed and won't start]("http://www.compiz.net/topic-3415-compiz-awhile-then-crashed-start").

---


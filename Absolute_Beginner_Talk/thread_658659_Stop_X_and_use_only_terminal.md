---
title: "Stop X and use only terminal?"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by kachofool on 2008-01-04
How do I stop the X environment and go back to terminal? If I press Ctrl+Alt+Backspace, X shuts down and starts up again immediately (goes to the log in screen).

Thanks
KF

---

### Post by PeterJS on 2008-01-04
You can leave X running and user ctrl+alt+F1 through 6 to login on one physical terminals. To kill X and make it stay down, run:
```

sudo /etc/init.d/gdm stop

```
before killing X. To get X to restart run:
```

sudo /etc/init.d/gdm start

```

---


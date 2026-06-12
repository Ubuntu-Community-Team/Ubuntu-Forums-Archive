---
title: "power management"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by jhvillegas2 on 2008-01-04
I have tried to keep my monitor from shutting off through the obvious procedure, however, it is still shutting off.  What should I be doing?

Thanks,
John

---

### Post by Yellow Pasque on 2008-01-04
type:
```
sudo gconf-editor
```

Follow this path in the left pane by clicking the arrows:
/apps/gnome-power-manager/timeout/

Look at the sleep_display_ac value in the right pane. If It's anything other than 0, right-click it, edit it, and change it to 0. I'm not sure if it takes effect instantly or the next time you reboot.

---


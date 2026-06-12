---
title: "I finally got Ubuntu working on my computer! but..."
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by Sk1ppy on 2007-07-31
When I went into Ubuntu it had me install drivers for my video card (nvidia 7600gt). After I restarted my comp to get them working it says it is a "restricted driver." Now I cannot change the resolution or the refresh rate to the correct level. Is there a different driver I should download, or some sort of fix?

---

### Post by wolfen69 on 2007-07-31
in terminal:
```
nvidia-settings
```

---

### Post by Jimmyfj on 2007-07-31
Also you can install Sysinfo: Programs>Add or remove>System tools>Sysinfo and access the settings from the Sysinfo GUI.

---

### Post by Sk1ppy on 2007-07-31
One more question: Am I supposed to have to change it every time I restart my computer?

---

### Post by logos34 on 2007-08-01
> **Sk1ppy said:**
> One more question: Am I supposed to have to change it every time I restart my computer?

Not if you saved your resolution and refresh rate to X configuration file (/etc/X11/xorg.conf).  After you do this disregard what it says under Sys>prefs>screen resolution (there's a bug which prevents gnome from correctly detecting nvidia config settings).

---


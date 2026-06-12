---
title: "Automatix and XGL"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by blendmaster on 2006-10-30
Hello!

After getting Automatix installed on my new Edgy system (had to reinstall, but that's a different problem...) I used it's option to install the nVidia drivers, and now I can't get into my Ubuntu system.

I have to go to the safe mode to get to the command line, as when the system attempts to start x, it gets stuck at a black screen that does nothing.

Well, this is my question. Does anyone know the command that automatix tells you to use in this case? I didn't write it down because the last time I tried this (on Dapper) it worked flawlessly. I realize this was a mistake and am now regretting it.

Thank you!

---

### Post by blendmaster on 2006-10-30
Anyway to just uninstall nvidia-xgl?

---

### Post by arnieboy on 2006-10-30
> **blendmaster said:**
> Anyway to just uninstall nvidia-xgl?
```
sudo nano /etc/X11/xorg.conf
``` 
mark the upper and lower cases in above and change **nvidia** to **nv** under **Device**
hit **ctrl-X** and **Y** to save the file and then restart

---


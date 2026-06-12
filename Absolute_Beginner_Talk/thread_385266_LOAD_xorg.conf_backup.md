---
title: "LOAD xorg.conf backup"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by Frickalik on 2007-03-15
Just lk the title says.....How do i load the backup xorg.conf that i made...??!??!?!

Does anyone know if Ubuntu 7.0 supports 8800 gts

---

### Post by kelbizzle on 2007-03-15
```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

```
sudo /etc/init.d/gdm restart
``` or just restart your computer

---


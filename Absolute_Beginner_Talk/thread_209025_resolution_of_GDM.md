---
title: "resolution of GDM ?"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by wolfmaniac on 2006-07-04
how can i shift to a lower resolution in GDM (starting screen).
well i m using XUBUNTU

---

### Post by wombat20 on 2006-07-04
I thought this was linked to System -> Preferences -> Screen Res.

---

### Post by wolfmaniac on 2006-07-04
this do not change resolution of login screen  and only changes that of desktop

---

### Post by confused57 on 2006-07-04
Open a terminal or Ctrl+Alt+F1, & type in:

```
sudo nano /etc/X11/xorg.conf
```

Toward the bottom of the file, you'll see the screen resolutions listed for
Default 24...set the first resolution in this line to be your desired login resolution.

---

### Post by wolfmaniac on 2006-07-05
it didnt work .

the resolution of login screen is still high

---


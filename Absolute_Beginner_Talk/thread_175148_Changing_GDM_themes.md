---
title: "Changing GDM themes?"
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by Just4 on 2006-05-12
I run Xfce but use GDM as my login, how can I change the GDM theme?

---

### Post by uzi09 on 2006-05-12
you should probably have the gdmsetup program if you have gdm. if not, you can probably download it through synaptic/apt-get (ask if more info needed).

type:
```
sudo gdmsetup
```
(enter your passwd when you get a chance).

go to [www.gnome-look.org](www.gnome-look.org) (or any other site for gdm themes)

search for a theme, then click add and then select the tar.gz file. it'll automatically install it and should let you select it.

good luck,
uzi

---

### Post by Just4 on 2006-05-13
Ah, ok, thanks a lot.

---

### Post by aysiu on 2006-05-13
I would advise using *gksudo* for graphical applications: ```
gksudo gdmsetup
```

---


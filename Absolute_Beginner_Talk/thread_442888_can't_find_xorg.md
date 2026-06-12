---
title: "can't find xorg"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by locustfist on 2007-05-14
sudo /etc/X11/xorg.conf
command not found

???

---

### Post by bobplano on 2007-05-14
you need to use some kind of text editor
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by RomeReactor on 2007-05-14
Hi. If you want to edit Xorg.conf, the command is:

```
gksudo gedit /etc/X11/xorg.conf
```

However, I strongly recommend you back it up before editing:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

---

### Post by locustfist on 2007-05-14
thanks

---


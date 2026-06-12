---
title: "I edited a file (xorg.conf, I think), and now GDM won't work"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by Incompl on 2006-09-06
A friend told me to edit part of a file (etc/x11/xorg.conf, or something like that) and now I just have a black screen with white text on it. I edited a part with a lot of screen resolutions repeated over and over again.


Now I don't even know how to edit the file, and if I did I wouldn't know what to edit! I realize I'm not being very specific, but I don't really remember what I did. Any help would be greatly appreciated. :)

---

### Post by bodhi.zazen on 2006-09-06
Try this:
```
Ctrl-alt-F1
Log in
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure -phigh xserver-xorg
sudo gdm
```

---

### Post by Incompl on 2006-09-06
It's working again! Thanks! :D

---

### Post by enopepsoo on 2006-09-06
> **bodhi.zazen said:**
> Try this:
```

sudo dpkg-reconfigure -phigh xserver-xorg

```
What does that line do?

---

### Post by bodhi.zazen on 2006-09-06
> **enopepsoo said:**
> What does that line do?

```
sudo dpkg-reconfigure xserver-xorg
``` re-configures X (re-writes xorg.conf, saves a back up of original). **-phigh** skips all options but but resolution.

---


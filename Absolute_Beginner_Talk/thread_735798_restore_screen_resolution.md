---
title: "restore screen resolution"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by corkscrew on 2008-03-26
I just tried to add an extra monitor to my acer laptop after reboot, i've totally mucked up my monitor settings to a plug n play 640 x 480 60 hz, how can i restore my original settings

---

### Post by om1 on 2008-03-26
in terminal type this```
dpkg-reconfigure xserver-xorg
```
that should do the trick

---

### Post by kesman on 2008-03-26
yeah with sudo in front of it, like this:
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by oedha on 2008-03-26
on terminal :==> sudo dpkg-reconfigure -phigh xserver-xorg
then press **ctrl+alt+backspace** to restart gnome

---


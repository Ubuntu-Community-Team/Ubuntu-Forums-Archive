---
title: "Screen Resolution"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by llzero1337 on 2007-07-25
please help i accidentally changed the resolution from 1280 x 1204 to 960 x 600 help me how can i change back because when i boot up my monitor says invalid screen resolution but i think i can get into the terminal since i can see the log in screen perfectly thanks for help

---

### Post by Raineer on 2007-07-25
If you can get into the terminal (easiest way is Ctrl-Alt-F2):
```

sudo dpkg-reconfigure -phigh xserver-xorg

```
This plugs in all the defaults except for screen resolution, should get you up and running. After the program finishes type:
```

sudo /etc/init.d/gdm restart

```
If you use KDE then type kdm instead of gdm

---

### Post by llzero1337 on 2007-07-25
thanks!

---


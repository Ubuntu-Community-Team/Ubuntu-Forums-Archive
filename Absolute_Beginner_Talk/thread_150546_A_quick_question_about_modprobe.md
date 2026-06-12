---
title: "A quick question about modprobe"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by Gosta on 2006-03-26
Hi, to get my sound working I have to type ```
sudo modprobe snd-sbawe
``` everytime I log in. I guess there is a way to make the sound working automaticly. How?

---

### Post by xtacocorex on 2006-03-26
You can do this by editing the /etc/modules file and placing it at the end of the list.

```
sudo vi /etc/modules
```

You can use the editor of your choice, instead of vi. If you want it graphically:
Gnome
```
gksudo gedit /etc/modules
```
or KDE
```
kdesu kate /etc/modules
```

---

### Post by Gosta on 2006-03-26
Thank you :)

---


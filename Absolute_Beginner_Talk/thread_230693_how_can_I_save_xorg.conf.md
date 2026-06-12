---
title: "how can I save xorg.conf?"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by vaazu on 2006-08-06
It says I dont have permissions but I dont know a way for opening it in admin way. doesnt su work in xubuntu?

---

### Post by lamego on 2006-08-06
```
sudo gedit /etc/X11/xorg.conf
```
The usual way to use administrive commands on Ubuntu is using sudo command.

---

### Post by OU812 on 2006-08-07
Recall that gedit is a gui app. It has been suggested that gksudo be used to launch gui apps. So maybe you should try this command

```
gksudo gedit /etc/X11/xorg.conf
```

and when you finish do this command

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This last bit will enable your modified file to be automatically updated.

john

---

### Post by aysiu on 2006-08-07
If you're using Xubuntu, you may not have *gedit*. Try either ```
sudo nano -B /etc/X11/xorg.conf
``` or ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo mousepad /etc/X11/xorg.conf
```

---

### Post by OU812 on 2006-08-07
My bad - I missed the x prefix. Thanks aysiu for the save.

john

---


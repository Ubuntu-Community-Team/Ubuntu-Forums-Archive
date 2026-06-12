---
title: "cannot edit /etc/X11/xorg.conf"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by number58 on 2007-06-05
I am trying to enable the thumb buttons on my logitech mx510. I have read both ManyButtonsMouseHowTo and IntelliMousemanBackandForwardButtons. But whenever I edit the xorg.cnf file, i cannot save it. it says i don't have the necessary permissions. Any help would be appreciated.

---

### Post by steeleyuk on 2007-06-05
type at the terminal

sudo gedit /etc/X11/xorg.conf

---

### Post by wheredidrealitygo on 2007-06-05
You need to edit it as the superuser (administrator).

from the terminal:
```
sudo gedit /etc/X11/xorg.conf
```

Make sure you backup xorg.conf first.

---

### Post by number58 on 2007-06-05
Thanks, I will try that.

---

### Post by johnc4510 on 2007-06-05
To take steeleyuk's answer a step further, all files in the root file system can only be edited using the sudo and one of the editors, gedit, nano or vim. 

Note: Please be careful when you edit any of these files. It is a good idea to make a backup of the file you are editing in case you need to restore it.

---

### Post by aysiu on 2007-06-05
Alt-F2 ```
gksudo gedit /etc/X11/xorg.conf
``` is the proper way to do it. More details here:
[http://www.psychocats.net/ubuntu/permissions#gui](http://www.psychocats.net/ubuntu/permissions#gui)

---

### Post by number58 on 2007-06-05
It still didn't work. I edited both the xorg.conf and the imwheel just as they said, but nothing has changed.

---

### Post by number58 on 2007-06-05
By the way, i have gnome i thnk, and the guide says gnome already has the software i need.

---


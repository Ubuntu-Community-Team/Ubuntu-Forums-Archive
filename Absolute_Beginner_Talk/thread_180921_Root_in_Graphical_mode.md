---
title: "Root in Graphical mode"
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by hotbrainz on 2006-05-23
How can i switch to root user in Graphical mode.

I want ot do this to move files as i please. With care of course :)

Thanks for the help

---

### Post by Jucato on 2006-05-23
It is possible to move files in the GUI without the need to login root graphically. You can launch your File Manager as root. 

If you are using GNOME, press Alt+F2 and enter:
```
gksudo nautilus
```

If you are using KDE, press Alt+F2 and enter:
```
kdesu konqueror
```

This will launch the respective file managers with root access so that you can do what you want. Just don't forget to close them when you are done.

---

### Post by hotbrainz on 2006-05-23
thanks mate, good stuff

---

### Post by tkjacobsen on 2006-05-23
root user is not enabled by default in ubuntu. see the wiki:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---


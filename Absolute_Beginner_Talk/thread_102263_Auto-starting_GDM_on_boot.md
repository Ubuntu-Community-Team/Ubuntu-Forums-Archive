---
title: "Auto-starting GDM on boot"
date: 2005-12-11
forum: Absolute Beginner Talk
---

### Post by bob phillips on 2005-12-11
after getting all excited about Xubuntu working, i've hit a snag

(probably broken something by messing about 'sudo'ing)

when i boot up, i get a text login screen
i can then login, but the only way i know to get my XFCE session starting is
```
sudo gdm
```

can i either
(a) type something else to start my XFCE session or
(b) automatically start the GDM?

cheers

---

### Post by Kvark on 2005-12-11
[QUOTE=bob phillips](a) type something else to start my XFCE session or[/QUOTE]
This command should start the X server with your default window manager:
```
startx
```

[QUOTE=bob phillips](b) automatically start the GDM?[/QUOTE]
Maybe this will set up the Gnome Display Manager properly including starting it automatically on bootup:
```
sudo dpkg-reconfigure gdm
```

---

### Post by kingsidy on 2006-01-01
this post might be too late but here is how to start xfce automatically. first install gdm by typing in the terminal > sudo apt-get install gdm after that right click and you will see the the option "login screen setup" in settings, click on that and put in your password. then in the  general tab, select "automatically login this user on boot". there you go, next time you boot, xfce will start automatically

---


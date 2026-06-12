---
title: "Gnome &amp; KDE"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by -=Raven=- on 2006-06-11
Ok, i know i can switch between Gnome and a kinda fullscreen terminal by pressing Ctrl Alt + F6, Ctrl Alt + F7. Can i run Gnome on one and KDE on the other and switch between them both?

If so, how do i go about doing this?

---

### Post by bruce89 on 2006-06-11
You will have to install Kubuntu ```
sudo aptitude install kubuntu-desktop
```
Then just use switch user.  Once in the login screen, goto Options>Sessions and select KDE.  You can then go between GNOME and KDE with Ctrl+Alt+F7 and Ctrl+Alt+F8.

---

### Post by -=Raven=- on 2006-06-11
Will this screw up all my settings and stuff?

---

### Post by bruce89 on 2006-06-11
No.

---

### Post by aysiu on 2006-06-11
It actually should be two commands: ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

---

### Post by -=Raven=- on 2006-06-14
Ok, its been running for a few days now.
How do i disable it from asking me about the default X? 
Keeps trying to get me to set one.

---

### Post by aysiu on 2006-06-14
That's what GDM does.
KDM remembers the default each time. ```
sudo cp /etc/X11/default-display-manager /etc/X11/default-display-manager_backup
sudo nano /etc/X11/default-display-manager
``` Change ```
/usr/sbin/gdm
``` to ```
/usr/bin/kdm
```

---


---
title: "HELP! Log on Screen Changed"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by FlukedAnchor on 2006-09-07
I was installing programs from the autmatix menu .. and there was a point where it asked me to choose layout from KDE and I want to say Gnome (what Ubuntu is when u first install it)  I chose KDE when i think i should have chosen the other one .. how can i change this, i mean this changed my whole logon screen and more .. 

HELP
Thomas

---

### Post by orb9220 on 2006-09-07
In your system menu should be the logon window. If it is not listed then go to the apps>accesories>ala carte menu editor to enable it.

That will allow you to set default logon

---

### Post by jordanmthomas on 2006-09-07
I think you've switched to KDM instead of GDM.

try this:
```
sudo nano /etc/X11/default-display-manager
```

It will probably read
```
/usr/bin/kdm
```

Change it to this:
```

/usr/sbin/gdm
```

Press Ctrl-X, then y, then enter.

Reboot and see what happens.

//you can avoid rebooting if you want by doing this:
```
sudo /etc/init.d/kdm stop
```
log in as you.
```
sudo gdm
```

---

### Post by jordanmthomas on 2006-09-07
also, you may need to select 'Gnome' from the Sessions menu on the login screen or else you may get dropped into KDE

---


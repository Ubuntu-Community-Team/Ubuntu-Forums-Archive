---
title: "Ubuntu Server"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by saintj0n on 2007-07-09
I type in startx on ubuntu server and get "command not found". Is this normal?

---

### Post by KIAaze on 2007-07-09
Ubuntu server is meant for servers and servers don't need GUIs.
So X11 is probably not installed.

If you want it, you'll have to install it first.
```
sudo aptitude install xinit
```

---

### Post by Malibu Illusion on 2007-07-09
Considering Ubuntu server does not have a GUI system installed by default, yes.

```
sudo aptitude install ubuntu-desktop
```

Note: this will install the full GNOME desktop environment.  If you do not want this and just want to install the xserver independently, you'll have to install the individual components as documented in the other posts.

---

### Post by moore.bryan on 2007-07-09
[I]yes because x isn't installed in a server-install... you've got to do it yourself.
```
sudo aptitude install x-window-system-core xserver-xorg xbase-clients
```
[/I]

---

### Post by KIAaze on 2007-07-09
It's funny how everybody managed to give different packages to install. ^^
I simply searched for the package containing startx. But with the dependencies and all, the others will do too of course.

---

### Post by moore.bryan on 2007-07-09
[I]that's linux for ya...
;-)
[/I]

---


---
title: "Installed fluxbox, but it doesn't show up under session options!"
date: 2005-12-06
forum: Absolute Beginner Talk
---

### Post by wr0x2 on 2005-12-06
I finally got fluxbox installed from source (v. .9.14) but it doesn't show up under the session options at the login screen as an option for a windowmanager. How can I make fluxbox an option at the login screen?

---

### Post by parktownprawn on 2005-12-06
type ```
sudo gedit  /usr/share/xsessions/fluxbox.desktop 
```
and enter
```
[Desktop Entry]
Encoding=UTF-8
Name=Fluxbox
Comment=Highly configurable and low resource X11 Window manager
Exec=startfluxbox
Terminal=False
TryExec=fluxbox
Type=Application

[Window Manager]
SessionManaged=true

```

save and exit.

fluxbox should appear on the login list. 

This assumes you installed the command startfluxbox somewhere on the path


see [https://wiki.ubuntu.com/Fluxbox](https://wiki.ubuntu.com/Fluxbox) for more information

---


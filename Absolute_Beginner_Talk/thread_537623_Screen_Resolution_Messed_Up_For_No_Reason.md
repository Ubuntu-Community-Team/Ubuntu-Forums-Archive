---
title: "Screen Resolution Messed Up For No Reason"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by Pioneer5000 on 2007-08-29
Somethings wrong logged on and everything is real big the screen resolution is all messed up but when i go into system>prefrences to change screen resolution the button just screws up and doesnt let me change it. Help Please.

---

### Post by tyggna1 on 2007-08-29
here's an idea--just something you can try:

type in

```
gksudo nautilus
```

Then navigate to
/etc/X11

and click on xorg.conf

Post what it says under the section "Screen"


If something has gone hay-wire in that, then it could cause some issues with resolution changing and stuff like that.

---

### Post by kellemes on 2007-08-29
View /var/log/Xorg.0.log for errors.

---


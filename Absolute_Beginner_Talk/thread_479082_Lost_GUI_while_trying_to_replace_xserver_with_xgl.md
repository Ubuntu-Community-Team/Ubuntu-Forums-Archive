---
title: "Lost GUI while trying to replace xserver with xgl"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by videocheez on 2007-06-19
Man this is getting embarassing but while trying to get my ATI video card configured i made a script which i obtained from the following URL but must have done something wrong because i lost my gui.  

[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

The last thing that i did was that i went into the session manager and included my script in the list of startup programs.  What can I do to get rid of that script and boot normally and get my gui back.

[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

FYI

Here are the scripts:

#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
dbus-launch --exit-with-session gnome-session

and

[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Comment=Start an Xgl Session
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application

Thanks in advance,

VC

---

### Post by slimdog360 on 2007-06-20
by looking at that page just undo what you did.

the first is placed at /usr/bin/startxgl.sh, hence the command 
```
sudo rm /usr/bin/startxgl.sh
```
will get rid of the first one and
```
sudo rm /usr/share/xsessions/xgl.desktop
``` will get rid of the second.

---

### Post by videocheez on 2007-06-20
thanks man.  you guys saved my a$$ again.

---


---
title: "scren resolution problems"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by nicholas mccarthy on 2008-02-20
ive recently switched computers and installed ubuntu on the computer im on now, and got rid of the computer that i used to have ubuntu on. well, the screen resolution is too small for my screen and its really annoying, so i went to go change it, and whenever i did, it would say it changed, but it stays the same, so its not letting me change the resolution. any suggestions?

---

### Post by nicholas mccarthy on 2008-02-20
anything?

---

### Post by S15_88 on 2008-02-20
post your xorg.conf ... located in /etc/X11/xorg.conf

Thanks, Alain

---

### Post by oedha on 2008-02-20
or....you can try to edit the xorg manually
open terminal
type :==> gksu gedit /etc/X11/xorg.conf
find monitor/screen section
change the resolution....for example "1280x1024"
save and then sudo /etc/init.d/gdm restart to restart your gnome

---


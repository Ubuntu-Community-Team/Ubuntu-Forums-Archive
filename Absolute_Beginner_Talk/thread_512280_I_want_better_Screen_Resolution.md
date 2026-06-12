---
title: "I want better Screen Resolution"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by 4Real on 2007-07-29
ive been told to go here "/etc/X11/xorg.conf"and edit it...

once i type it and hit enter "in terminal" it says permission is denied. 

I want 1024x768 SR but i only get 800x600 and 640x480

help please! :confused:

---

### Post by meierfra on 2007-07-29
```
gksudo  gedit  /etc/X11/xorg.conf
```

---

### Post by Espreon on 2007-07-29
Back the file up: goto /etc/X11 and copy the xorg.conf file and paste it to your desktop

After using the command listed by meiefra, hit replace on the find area put: 800x600 then on the replace area put: 1024x768 and hit replace all, save, hit CTRL-ALT-Backspace and enjoy.

---


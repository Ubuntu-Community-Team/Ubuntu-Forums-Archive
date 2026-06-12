---
title: "Bring up Terminal"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by Touch.Code on 2007-02-16
Hey,

My stupid Dell Laptop screen keeps blanking out even though it still works. My res for it is to big for my extra monitor to view it, so I need to know if there is away of bringing up a terminal by using the command in Alt+F2 and then changing the res through a terminal?

Thanks, 

Touch

---

### Post by taurus on 2007-02-16
You can edit /etc/X11/xorg.conf and remove the high resolutions from the list.

```
gksudo gedit /etc/X11/xorg.conf
```
Then, restart X again with <Ctrl><Alt>Backspace.

---

### Post by Touch.Code on 2007-02-16
Thanks for that, but my second screen just shows colours with blocks of colour mainly black? 
I can't see my laptop screen as it has lost the backlight?

---


---
title: "I may be being dense, but... (roll-over information)"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by atenlaugh on 2006-06-28
I've looked and looked and can't seem to turn this off: you know when you put your mouse on anything (say, a menu item) and it tells you what that thing does? I don't want that. I can't find anything in System --> Preferences or in gconfig.

---

### Post by wpshooter on 2006-06-28
[QUOTE=atenlaugh]I've looked and looked and can't seem to turn this off: you know when you put your mouse on anything (say, a menu item) and it tells you what that thing does? I don't want that. I can't find anything in System --> Preferences or in gconfig.[/QUOTE]

I am not sure and am not at a Ubuntu system right now, but did you look under the "Windows" menu listing under system preferences ?

---

### Post by wombat20 on 2006-06-28
I don't think there's any way to set this up through the GUI, but there is bound to be a fiddly way to hack GNOME to turn this off.

---

### Post by richbarna on 2006-06-28
Alt+F2
gconf-editor
apps/panel/global/tooltips-enabled
right click /set as false
Might do it, think you have to reboot ;)

---

### Post by atenlaugh on 2006-06-28
[QUOTE=richbarna]Alt+F2
gconf-editor
apps/panel/global/tooltips-enabled
right click /set as false
Might do it, think you have to reboot ;)[/QUOTE]


Exactly what I was looking for! Thanks. 

I must've just missed that, though I'm glad to see it wasn't AS painfully obvious as I had thought!

---


---
title: "Setting key bindings for tilda"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by Jamesbowden on 2006-12-23
i have tilda (a drop down terminal program the drops down when from the top of your screen at the press of a button, much like the terminal in doom) installed, i want the change the keybinding (hotkey) to drop it down it to my "F2" key, but the box set the hotkey is only basic text. 

how do i enter it as "F2".

thanks

---

### Post by jincast90 on 2006-12-23
> **Jamesbowden said:**
> i have tilda (a drop down terminal program the drops down when from the top of your screen at the press of a button, much like the terminal in doom) installed, i want the change the keybinding (hotkey) to drop it down it to my "F2" key, but the box set the hotkey is only basic text. 

how do i enter it as "F2".

thanks

I'll start out by saying that I don't know the solution. I was wondering if you have tried looking through System>Preferences>Keyboard Shortcuts

---

### Post by j0sh0 on 2007-01-23
from a terminal, or thru Atl+F2 (run program), type

tilda -C

which loads the tilda config screen. go to key bindings tab, then type in "None+F2".
The "none" means there is no other key held down while pressing F2.

Hop this helps

---

### Post by debjit_bis08 on 2007-12-18
Hav u tried looking into file ~/.tilda/config_0
its on the 5th line 
key = 
cant get the control key to work though
control key shud be written as Ctrl i hope

---


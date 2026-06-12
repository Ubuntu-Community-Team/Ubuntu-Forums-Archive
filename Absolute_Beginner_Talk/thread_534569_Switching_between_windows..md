---
title: "Switching between windows."
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by GITanker on 2007-08-25
Hello, I'm new to ubuntu, but like it so far. The problem I am having is when I switch between windows using the lower right coner buttons, I lose the top and bottom panels or tool bars, (depends on what they are called). Then I can not go back to any of the other windows/desktops. I can right click on the desktop but that is about it. I can not go online, or to Applications, places, Systems. Nothing. I have to reboot the system and make sure I don't use those other 3 windows. 
This happen after the second time Ubuntu down loaded updates and installed them.

Thanks

---

### Post by asmoore82 on 2007-08-25
:confused: Do you have Desktop Effects enabled?

---

### Post by GITanker on 2007-08-25
Yes, I have desktop Effects enabled.

---

### Post by asmoore82 on 2007-08-25
open a terminal and run this command ....

```
~ $ gconf-editor /apps/compiz/general/screen0/options/number_of_desktops
```

change the value that is highlighted, "number_of_desktops" to 1.
then, change the one 2 above it, "hsize" to 4.

you made need to disable and re-enable effects afterwards.

---

### Post by GITanker on 2007-08-25
Asmoore82, Thanks, it worked. What would cause this to happen anyway???
Once again Thank You

---


---
title: "messed up gnome startup"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by Somenoob on 2007-02-22
I was trying to add "beryl-manager" to the session start up but when the beryl wm is launched it prevents all other gnome apps from starting, i managed to remove the beryl-manager from session start up but it still activates. How can i remove it from the list?

---

### Post by louis_nichols on 2007-02-22
You have to delete it from 2 places. The startup programs is one. Apart from that, you also have to delete it from the tab with the current session properties (and I think there's also an Aplly button there that you have to click after that). Then it will not start at login.

---

### Post by Somenoob on 2007-02-22
> **louis_nichols said:**
> You have to delete it from 2 places. The startup programs is one. Apart from that, you also have to delete it from the tab with the current session properties (and I think there's also an Aplly button there that you have to click after that). Then it will not start at login.

Yeah but i can't access any of that in the xgl seisson. It works in gnome, can't I permanetly remove it from start up?

---

### Post by louis_nichols on 2007-02-22
There is another, more radical way. Press CTRL+ALT+F1 to get a terminal, then login there and use the command line to delete the file

~/.gnome2/sessions

---

### Post by Somenoob on 2007-02-22
thanks, the problem was another current session process that made it the default wm.

---


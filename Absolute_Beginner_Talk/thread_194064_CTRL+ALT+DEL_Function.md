---
title: "CTRL+ALT+DEL Function"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-06-10
how can i get the system monitor to show up (in dapper) by pressing those buttons (just like in windows) ?  I tried going to system->preferences->keyboard shortcuts but there's no system monitor option there, and i dont know how to add it... :-k

---

### Post by aysiu on 2006-06-10
Press Alt-F2 ```
gconf-editor
``` Go to Apps > Metacity > Global Keybindings/ Keybinding Commands

For Command_1 in Global Keybindings, type ```
<Control><Alt>Delete
```

For Command_1 in Keybinding Commands, type ```
gnome-system-monitor
```

---

### Post by celem on 2006-06-10
Well, if its the running processes that you're after, open a shell and execute ps -A

---

### Post by user1397 on 2006-06-10
[quote=aysiu]Press Alt-F2 ```
gconf-editor
``` Go to Apps > Metacity > Global Keybindings/ Keybinding Commands

For Command_1 in Global Keybindings, type ```
<Control><Alt>Delete
``` 
For Command_1 in Keybinding Commands, type ```
gnome-system-monitor
```[/quote]thanks again aysiu!! that did exactly what i wanted it to!

---

### Post by user1397 on 2006-06-10
[quote=celem]Well, if its the running processes that you're after, open a shell and execute ps -A[/quote]no i just wanted to simply have a keyboard shortcut for the system monitor --i dont know, it just makes me feel safer...;)

---

### Post by aysiu on 2006-06-10
If you create a keyboard shortcut for ```
xkill
``` you can kill any offending application by just clicking on it.

---


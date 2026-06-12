---
title: "Task Manager"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by subs on 2007-12-06
Are there any shorcut keys for the System Monitor...... 

If not can i create some shortcut keys to open the system monitor when i press a certain set of keys???:confused::confused:

---

### Post by parhelia on 2007-12-06
Yes, this is simple. Open terminal and type gconf-editor

apps > metacity > global keybindings

Edit run_command_1 (select any number), type anything like <Alt>a

apps > metacity > keybinding_commands

Edit command_1 (if you choose to use this) to be gnome-system-monitor

Now press Alt + A. Beware though, since Alt+A is used by many applications. I recommend using <Ctrl><Alt>Delete

---

### Post by drs305 on 2007-12-06
Go to System, Admin, System Monitor. Click and hold on the symbol, drag it to the panel and release. You now have a shortcut one click away.

---

### Post by subs on 2007-12-06
> **parhelia said:**
> Yes, this is simple. Open terminal and type gconf-editor

apps > metacity > global keybindings

Edit run_command_1 (select any number), type anything like <Alt>a

apps > metacity > keybinding_commands

Edit command_1 (if you choose to use this) to be gnome-system-monitor

Now press Alt + A. Beware though, since Alt+A is used by many applications. I recommend using <Ctrl><Alt>Delete
thnx

---


---
title: "Killing a process?"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by Pobega on 2006-12-31
For some reason Conky is using up 100% of my CPU, and although I don't feel a slowdown my computer is making noise. I used the command top and tried to kill Conky's PID, but it isn't dying! I've restarted X but everytime I log back on Conky is still there.

[img]http://img521.imageshack.us/img521/5875/screenshotkc4.jpg[/img]

**Edit:** Uninstalling Conky and rebooting the computer did this, but I still don't understand what caused it.

---

### Post by Sigudian on 2006-12-31
How to enable Ctrl+Alt+Del to open System Monitor in GNOME

```
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"

```

and then press Ctrl+Alt+Del to open up system monitor, then try to do it graphically

---

### Post by Enkra on 2007-01-01
> **Pobega said:**
> For some reason Conky is using up 100% of my CPU, and although I don't feel a slowdown my computer is making noise. I used the command top and tried to kill Conky's PID, but it isn't dying! I've restarted X but everytime I log back on Conky is still there.

[img]http://img521.imageshack.us/img521/5875/screenshotkc4.jpg[/img]

**Edit:** Uninstalling Conky and rebooting the computer did this, but I still don't understand what caused it.

Try :
```
kill -9 [PID]
```

In your case PID = 8630 and 6260

---


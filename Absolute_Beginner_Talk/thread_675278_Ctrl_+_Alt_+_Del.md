---
title: "Ctrl + Alt + Del"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by intense.ego on 2008-01-22
I have read that you can enable ctrl alt del to bring up the system monitor using automatix (which i have installed) but i never see any instructions on how.

---

### Post by aysiu on 2008-01-22
Forget Automatix. It's too much trouble.

Just paste (with your mouse) these two commands in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"
```

---

### Post by intense.ego on 2008-01-22
does it make a difference if metacity is not my window manager because it is not working right now.

---

### Post by rhc on 2008-01-22
I tried it too and ctrl alt delete is opening the shut down-log off-hibernate etc. screen.

---

### Post by aysiu on 2008-01-22
> **intense.ego said:**
> does it make a difference if metacity is not my window manager because it is not working right now.
Yes, Metacity has to be your window manager for that to work.

What window manager are you using now?

---

### Post by rhc on 2008-01-22
i m using metacity but doesn't work too.

---

### Post by intense.ego on 2008-01-22
I was using beryl at the time, but I just switched over to metacity, because i was running a windows app with wine and didn't want it to crash, and it works just fine. thank you.

---


---
title: "Help what did I do? Did I hurt something (entering commands off of an Ubuntu Wiki)"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by episodic on 2007-10-20
I entered the following commands below into the terminal.

It did not work. It did not give me any warnings, etc.

The wiki was for Feisty. I'm using gutsy - I was hoping it would work. it did not. By entering these commands did I hurt something? Can someone tell me if I need to undo these commands some sort of way. 

The goal was to have "control - alt - delete" open the gnome system monitor - anyone tell me how to accomplish this and what I may have done to bork the system if anything at all?



 How to enable Ctrl+Alt+Del to open System Monitor in GNOME

gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"

---

### Post by Qwerty_ on 2007-10-20
Hmm I am not sure what it might of done to your system however you can easily set shortcuts by going to.

System>Preferences>Keyboard Shortcuts.

---

### Post by episodic on 2007-10-20
You can't set shortcuts to things that are not there. . .

it only lets you do somethings - not this.

anyone else think I hurt anything?

---

### Post by episodic on 2007-10-20
Anyone?

---


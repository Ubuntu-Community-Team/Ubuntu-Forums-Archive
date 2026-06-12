---
title: "alt+ctrl+del?"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by the_nomad on 2006-05-27
everyone knows what those buttons do togheter.... does it exist on linux?

---

### Post by Rinzwind on 2006-05-27
Yes 

In gnome we use **ctrl alt backspace** to stop gnome and then **ctrl alt delete** to restart.

---

### Post by the_nomad on 2006-05-27
:-?actually i need the process list because my xmms is blocking and i wanna close the process....... any ideea?:-?

---

### Post by unnes on 2006-05-27
Applications Menu --> System Tools --> System Monitor

In System Monitor you can kill individual processes much like Windows Task Manager.

---

### Post by mlind on 2006-05-27
killall -9 xmms

from terminal

---

### Post by carverj on 2006-05-27
I have a kill icon on my menu bar which can be dragged and dropped on misbehaving apps. quite handy!!
The only thing is a friend put it there and didn't show me how :D

---

### Post by ifokkema on 2006-05-27
[QUOTE=carverj]I have a kill icon on my menu bar which can be dragged and dropped on misbehaving apps. quite handy!!
The only thing is a friend put it there and didn't show me how :D[/QUOTE]

I'm guessing that's xkill.

Ivo

---

### Post by sam hassell on 2006-05-27
Right click the panel (taskbar), choose "Add to Panel" , look under the "Desktop & Windows" section, and drag the "Force Quit" icon onto the panel. Enjoy easy process destruction.

---

### Post by sYs^ on 2006-05-27
process list: type ps auxf to a terminal :p or ps -A

---

### Post by deja2004 on 2006-05-27
If you'd like to set up Windows-like cntrl-alt-del functionality, and are running gnome, you can set up a keybinding within the Configuration Editor. ```
gconf-editor
```
From there, go to apps/metacity/global_keybindings, choose a "run_command_X", right-click, edit key..., and type in "<Ctrl><Alt>Delete".
Then go to apps/metacity/keybinding_commands, select the corresponding "command_X", right-click, edit key..., and enter "gnome-system-monitor".
Try press ctrl-alt-del and see if it works :p

---

### Post by nixt on 2006-06-01
[QUOTE=deja2004]If you'd like to set up Windows-like cntrl-alt-del functionality, and are running gnome, you can set up a keybinding within the Configuration Editor. ```
gconf-editor
```
From there, go to apps/metacity/global_keybindings, choose a "run_command_X", right-click, edit key..., and type in "<Ctrl><Alt>Delete".
Then go to apps/metacity/keybinding_commands, select the corresponding "command_X", right-click, edit key..., and enter "gnome-system-monitor".
Try press ctrl-alt-del and see if it works :p[/QUOTE]

Does this work in dapper?

---

### Post by sinkxdie on 2006-06-01
Yes, that should work in Dapper too.

---


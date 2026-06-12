---
title: "CTRL + ALT + DEL to bring up system monitor in Gutsy?"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by Old Pink on 2007-11-13
Had this working in Feisty, think I used the good old```
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"

 gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"
```trick. It seems to have been disabled since gutsy, and running those two again has made no difference. 

Help?

---

### Post by philinux on 2007-11-13
why not use system prefs keyboard shortcuts.

Allocate one of those useless windows buttons.

---

### Post by IamAcoconut on 2007-11-13
Doesn't work for me. It only brings up the shutdown dialogue.

---

### Post by philinux on 2007-11-13
Thats because its the default in keyboard shortcuts :lolflag:

---

### Post by Old Pink on 2007-11-13
There isn't a "run system monitor" keyboard shortcut option in the preferences.

---

### Post by Jose Catre-Vandis on 2007-11-13
To do this, if you have compiz up and running, change the keyboard shortcut for CTRL+ALT+DELETE in keyboard shortcuts (I went for CTRL+ALT+SHIFT+DELETE)
(It's under Desktop>Log Out)

Then open up Advanced Desktop Effects Settings>General Options>Commands

For Command0 (or next spare command) type
```
gnome-system-monitor
```

Select the Actions tab
Scroll down to Command0 and double click
Enter as follows:
```
<Contol><Alt>Delete
```
Back out of ADES and try it :)

---

### Post by skymera on 2007-11-13
yeah im looking for it :P

that peeved me when it brings up shutdown dialogue.

---

### Post by philinux on 2007-11-13
Your dead right. Just checked.

I've just added the system monitor to a panel so now just one mouse click to start it.

I've got two windows keys so now one brings up home the other a terminal.

---

### Post by Old Pink on 2007-11-13
> **Jose Catre-Vandis said:**
> To do this, if you have compiz up and running, change the keyboard shortcut for CTRL+ALT+DELETE in keyboard shortcuts (I went for CTRL+ALT+SHIFT+DELETE)
(It's under Desktop>Log Out)

Then open up Advanced Desktop Effects Settings>General Options>Commands

For Command0 (or next spare command) type
```
gnome-system-monitor
```Select the Actions tab
Scroll down to Command0 and double click
Enter as follows:
```
<Contol><Shift>Delete
```Back out of ADES and try it :)This works with Control Shift Delete, but not Control Alt Delete, as requested.

Even when replacing <shift> with <Alt> 

I'm not running Compiz. Control Alt Delete does nothing else. Not shutdown. Not log out. Nothing. At all.

---

### Post by Jose Catre-Vandis on 2007-11-13
> **Old Pink said:**
> This works with Control Shift Delete, but not Control Alt Delete, as requested.

Even when replacing <shift> with <Alt> 

I'm not running Compiz. Control Alt Delete does nothing else. Not shutdown. Not log out. Nothing. At all.

Sorry, my bad - original post edited  :(

And um, if you haven't got compiz running, you do have ADES/ccsm installed so you can make the change, but unless compiz is running, the keyboard shortcut won't call the command

Also looks like you need corresponding commands in gconf-editor

If you have followed my how to, edit your original commands to change command1 and put gnome-system-monitor in command1

Are we there yet?  :)

---

### Post by philinux on 2007-11-13
It's all been done for us.

[http://ubuntuforums.org/showthread.php?t=42404](http://ubuntuforums.org/showthread.php?t=42404)

---

### Post by DarkStarDeity on 2007-12-05
```
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"

 gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"
```


This worked for me (I'm still on Dapper) but only for a single user. I want to make it universal for all existing users and the default setup for new users I create (I'm setting up a couple of new machines for family). Can I do this?

---


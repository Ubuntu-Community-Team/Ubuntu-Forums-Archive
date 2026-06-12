---
title: "Getting rid of grey Gnome?"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by john.n on 2007-05-10
Hiya, iv been installing Compiz on my computer and had to install xgl, was following a walkthrough, pretty sure it was [http://ubuntuforums.org/showthread.php?t=168618](http://ubuntuforums.org/showthread.php?t=168618), now have compiz on(although theres no cube..). But my main problem is that its switched the desktop over to what i think is the original gnome? Does anyone know how to put it back to metacity(if thats what im looking for). Changing the theme just changes the bars, not the colour and stuff which is a very depressing gray... :( 

Any help would be much appreciated.

Also, when i type "metacity " or " metacity --replace"
i get

john@johns-laptop:~$ metacity
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: Screen 0 on display ":1.0" already has a window manager; try using the --replace option to replace the current window manager.
john@johns-laptop:~$ metacity --replace
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

---

### Post by quark_77 on 2007-05-10
Hi john.n,

If you created a separate session for Xgl/Compiz then this is easily remedied (I have the same problem under Xgl/Beryl). 

Go to system > preferences > sessions and add "gnome-settings-daemon" to the list of start up programs, on feisty:
```
Name: Gnome Settings Daemon
Command: gnome-settings-daemon
```

Restart X (Ctrl-Alt-Backspace) and log in again on the Xgl session and your gnome themes etc should be restored.

Quark_77

---


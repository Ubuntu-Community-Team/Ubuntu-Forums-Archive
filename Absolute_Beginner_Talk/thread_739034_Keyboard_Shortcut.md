---
title: "Keyboard Shortcut"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by nebu on 2008-03-29
I wanted to add a shorcut for opening the system monitor.... summin like the Ctrl+Alt+Del in windows.....

However i cant get the option of running the system monitor in System->Preferences->Keyboard Shortcuts

is there a way i can add a shortcut for this particular action??

---

### Post by linuxtoindia on 2008-03-29
[B]wait ,, i provide u the complete guide

[/B]If you want to create shortcuts only for basic tasks, start by opening  SystemPreferences [COLOR=#ffffff]Keyboard[/COLOR]  Shortcuts to see a list of predefined
 actions,



Click on the shortcut entry for an action and then press the  key combination you want to associate with it. For example, if you want F7 to  launch your web browser, click the shortcut entry next to "Launch web browser"  and then press F7. Changes are applied immediately, so there is no need to save  the new settings.
 The built-in GNOME [COLOR=#ffffff]keyboard[/COLOR]-shortcut settings include only predefined actions,  so if you want to launch a custom script or an arbitrary program, you'll need  something more flexible, such as Hotkeys.

---

### Post by legend2440 on 2008-03-29
This worked for me
[http://twodayslate.wordpress.com/2007/12/26/creating-keyboard-shortcuts-in-gutsy/](http://twodayslate.wordpress.com/2007/12/26/creating-keyboard-shortcuts-in-gutsy/)

---

### Post by drs305 on 2008-03-29
Open gconf-editor in terminal.
Go to Apps, metacity, keybinding_commands.
Pick a command number, for instance, command_7
In the value, enter gnome-system-monitor
Now go to apps, metacity, global_keybindings, run_command_7
In the value, put the key combination you want, such as <ALT>L
Done.

---

### Post by nebu on 2008-03-29
> **drs305 said:**
> Open gconf-editor in terminal.
Go to Apps, metacity, keybinding_commands.
Pick a command number, for instance, command_7
In the value, enter gnome-system-monitor
Now go to apps, metacity, global_keybindings, run_command_7
In the value, put the key combination you want, such as <ALT>L
Done.

thnx.... it worked like a charm!!

---


---
title: "ctrl alt delete"
date: 2005-11-17
forum: Absolute Beginner Talk
---

### Post by onesojourner on 2005-11-17
is there something that works like ctrl alt delete in windows?

---

### Post by aysiu on 2005-11-17
Depends on what you're trying to do...

1. Kill a misbehaving program
2. System monitor
3. Restart the computer / Log out

What do you want? You can make keyboard shortcuts for all of them. 

#1 and #2 you go to Applications > System Tools > Configuration Editor > Apps > Metacity > Global Keybindings / Keybinding Commands. The commands you want are *xkill* and *gnome-system-monitor*.

For example, let's say you wanted to make Control-Alt-Delete the keyboard shortcut for killing misbehaving applications. You would make the global keybinding ```
<Control><Alt>Delete
``` and the keybinding command would be ```
xkill
```

To make a keyboard shortcut for #3, go to System > Preferences > Keyboard Shortcuts.

---

### Post by Kvark on 2005-11-17
The default ways that you should know if you don't want to congfigure custom stuff or if you ever use a linux system that you didn't configure custom keyboard shortcuts on are...

When a program missbahaves or things are going abnormally slow, open the System Monitor from the menu to look at how much memory and CPU the programs use and kill the misbaving ones.

If your whole graphical environment is frozen so you can't even open the menu then press Ctrl+Alt+Backspace. This will kill X and with it all your graphical programs. X should restart (if it doesn't, type startx) much faster then a reboot and this fixes most problems.

You can also switch to full screen command line mode by pressing Ctrl+Alt+F1 to F6 (each of those 6 keys has a separate terminal). Then switch back to graphical mode by pressing Ctrl+Alt+F7.

For an advanced example let's say your whole graphical environment freezes but you have unsaved work you don't want to kill with Ctrl+Alt+Backspace. Press Ctrl+Alt+F2 and log in to the terminal. Type "top" and look at all the info there to figure out which proccess is at fault. Let's say a proccess called firfox-bin is eating up all the memory and CPU in this example. Press Q to quit when you have seen enough. Then use the killall command to dispose of the missbahving proccesses. In this example you'd type "killall firefox-bin" to kill all of firefox-bin's proccesses. Lastly switch back to the GUI with Ctrl+Alt+F7.

---

### Post by BoyOfDestiny on 2005-11-17
[QUOTE=Kvark]The default ways that you should know if you don't want to congfigure custom stuff or if you ever use a linux system that you didn't configure custom keyboard shortcuts on are...

When a program missbahaves or things are going abnormally slow, open the System Monitor from the menu to look at how much memory and CPU the programs use and kill the misbaving ones.

If your whole graphical environment is frozen so you can't even open the menu then press Ctrl+Alt+Backspace. This will kill X and with it all your graphical programs. X should restart (if it doesn't, type startx) much faster then a reboot and this fixes most problems.

You can also switch to full screen command line mode by pressing Ctrl+Alt+F1 to F6 (each of those 6 keys has a separate terminal). Then switch back to graphical mode by pressing Ctrl+Alt+F7.

For an advanced example let's say your whole graphical environment freezes but you have unsaved work you don't want to kill with Ctrl+Alt+Backspace. Press Ctrl+Alt+F2 and log in to the terminal. Type "top" and look at all the info there to figure out which proccess is at fault. Let's say a proccess called firfox-bin is eating up all the memory and CPU in this example. Press Q to quit when you have seen enough. Then use the killall command to dispose of the missbahving proccesses. In this example you'd type "killall firefox-bin" to kill all of firefox-bin's proccesses. Lastly switch back to the GUI with Ctrl+Alt+F7.[/QUOTE]

Damn that is cool!

Anyway, I'd think ctrl+alt+delete to launch system manager is the sanest suggestion. I've noticed forcedquit can still leave the app (and it's cpu usage) going... Actually I'll set the short cut now, and thanks for the tips!

---

### Post by MetalMusicAddict on 2005-11-17
This will bind "<Control><Alt>Delete" to the System Monitor.

In a terminal type:
**gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"**
Then:
**gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"**

Works like a charm.

---

### Post by Wolki on 2005-11-17
[QUOTE=Kvark]Type "top" and look at all the info there to figure out which proccess is at fault. Let's say a proccess called firfox-bin is eating up all the memory and CPU in this example. Press Q to quit when you have seen enough. Then use the killall command to dispose of the missbahving proccesses.[/QUOTE]

You can also kill the task from within top, press 'k', then enter the process ID, then the signal (leave blank for default). The process ID is the number displayed in the leftmost column in top, so it's rather easy to find.

---


---
title: "Hotkey"
date: 2005-06-21
forum: Absolute Beginner Talk
---

### Post by Zaare on 2005-06-21
How can I assign a hotkey to a certain program?
(I mean, a program which is not in the Keyboard Shortcuts list under System/Preferences)

---

### Post by intangible on 2005-06-21
**Applications->System Tools->Configuration Editor**

**/apps/metacity/keybinding_commands**
Set "command_1" to the command you wish to run. (or command_2, command_3, etc)

**/apps/metacity/global_keybindings**
Set "run_command_1" to the shortcut you wish to use for command_1, run_command_2 for command_2, etc.
The "Long Description" at the bottom explains how to add <control> and <alt> keys, etc.

Hope this helps, sorry it's not easier, but not too many people do this (I do).
It wouldn't be too hard to write a custom program to manage this though... hmmm...

---

### Post by Zaare on 2005-06-27
It's easy enough. Shortcuts make life a hole lot easier. Thanks a lot. :)

---


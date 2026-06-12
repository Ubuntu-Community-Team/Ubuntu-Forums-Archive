---
title: "Keyboard shortcut problem"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by Snakes on 2007-07-13
Hi

While I was messing in Ubuntu I  somehow managed to create a problem with my keyboard shortcuts.      Ubuntu now opens a bash window ( terminal-like window , but with a black bg in stead of a white one, and without the menu of the terminal window).     Quit annoying since I prefer the ctrl + f combination for opening a search-dialog in firefox or openOffice.

In the system settings for keyboard shortcuts of ubuntu , I don't see something that could prevent this from happening.    First of all I can't find a shortcut for opening the bash window and second of all, I don't see the ctrl + f combination in the list of used shortcuts.

Could someone help me out ? 

Thx
J.

---

### Post by BobCFC on 2007-07-14
Try Alt-F2 and typing gconf-editor

Then look under apps->metacity-->global_keybindings.

There is an entry called run_command_terminal where I can set a keyboard shortcut.


Although this should run your default terminal so if it is launching a similar program look around for a different shortcut..

maybe run_command_1 is bound to xterm?  You can see the target for the shortcuts in keybinding_commands  on the left.  have a look around.

---

### Post by Snakes on 2007-07-16
> **BobCFC said:**
> Try Alt-F2 and typing gconf-editor

Then look under apps->metacity-->global_keybindings.

There is an entry called run_command_terminal where I can set a keyboard shortcut.


Although this should run your default terminal so if it is launching a similar program look around for a different shortcut..

maybe run_command_1 is bound to xterm?  You can see the target for the shortcuts in keybinding_commands  on the left.  have a look around.

Nope that's not it.   There is no key-value <Control>F in there  ...   So I'm still facing this problem.

---


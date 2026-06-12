---
title: "I just disabled several of my keys"
date: 2005-12-11
forum: Absolute Beginner Talk
---

### Post by Othersider on 2005-12-11
Self-nominee for Ubuntu idiot of the year award.

In key shortcut preferences, I was tinkering around and setting some accelerators.  Long story short - I set a few, didn't like them, so I clicked and disabled these shortcuts.

The problem is, all the accelerator keys I chose - minus ctrl and alt - now do not work.  Among these are my 'p' and enter keys.  I've resorted to coying and asting the letter 'p' from the nearest text possible.  Not really fun.

Anybody know what to do?  I just want my shortcuts to go back to how they were (defaults are hexadecimal) and regain usage of my keys :confused:.

----------------------------------------------------------
**SOLUTION:**

1) In terminal:
gedit ~/.gconf/apps/gnome_settings_daemon/keybindings/%gconf.xml

2) Remove all entries that say "disabled".  This returns them to their default settings.

3) Save what you've done and restart Gnome by pressing Ctrl Alt Backspace.

---


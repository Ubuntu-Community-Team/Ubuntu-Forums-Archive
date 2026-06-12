---
title: "[SOLVED] Black screen when using Wine"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by gs110 on 2007-11-02
When ever I attempt to use Wine the window with the wine application is completely black, Any ideas about how to fix this?
Edit: Never mind, it somehow fixed itself...somehow...

---

### Post by tmask on 2007-11-02
it sounds like you're wine is bringing up the emulated desktop.  Try this:

[LIST=1]
[*]Open up the terminal.
[*]Type "winecfg"; push enter
[*]Select the "Graphics" tab
[*]Make sure that "Emulate Virtual Desktop" is UNCHECKED
[/LIST]

That should take off the emulated desktop. Thats all I can think of.

---


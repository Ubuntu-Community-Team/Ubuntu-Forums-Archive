---
title: "configuring ctrl+alt+backspace"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by maddot on 2007-06-19
how do i make ctrl+alt+backspace to go into console mode instead of logging out?

---

### Post by eldepeche on 2007-06-19
Well, ctrl-alt-F1 takes you to a console where you can log in. Most (all?) GNU/Linux distros start 6 virtual terminals, accessible by hitting ctrl-alt-F?, and alt-F? to switch between them. The X server is on the 7th virtual terminal, so you can get back to the graphical environment by pressing alt-F7.

There's an xorg.conf option that disables zapping the X server, and I think you can set a shortcut for the keystroke in Gnome.

---

### Post by maddot on 2007-06-19
cool...i'll experiment with that later once i reinstall ubuntu....i broke something after instaling nvidia drivers :/

---

### Post by Golyadkin on 2007-06-19
Control-Alt-Backspace restarts the X server. It is not a shortcut for logging out.

Ah, I was too slow :)

---


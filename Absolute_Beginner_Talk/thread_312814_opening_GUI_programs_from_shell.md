---
title: "opening GUI programs from shell"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by paritosh1010 on 2006-12-05
I tried opening xload from shell, and it said error:can't open display

I tried doing gksudo with xload commands, and sudo too, and it gave:

gdk warning: locale not supported by Xlib
gdk warning: oannot set locale modifies
gdk warning: cannot open display

same happens if i try to open nautilus from shell.
any suggestions?

---

### Post by RAOF on 2006-12-05
When you say "shell" what do you mean?  Options I can think of are:
1) From a Terminal in a GUI session
2) From a virtual terminal (switching from the GUI to a terminal using Ctrl+Alt+F1, for example)
3) From a remote terminal - eg: logging in remotely using SSH.
4) From a local terminal, but with no GUI running at all

The solution depends on which one describes your situation.  From the top:
1) This should just work.
2) You probably want to run it using "DISPLAY=:0 xload", etc
3) You'll need to enable X11 forwarding over SSH
4) You can't.  There's no X server running, so you can't run X programs.

My guess would be that (4) is what applies to you.

---

### Post by paritosh1010 on 2006-12-05
yea, virtual terminal(ctrl+alt+f1).
i have gnome running.

[edit] the solution display=0 worked. could you explain what display=:0 does?

---

### Post by RAOF on 2006-12-05
Ok, well you can't display graphical programs in the terminal (obviously, it's a terminal), but you **can** load programs from there, and they'll display in the gui (Ctrl-Alt-F7), with (for example):
```

DISPLAY=:0 xload

```
The "DISPLAY=:0" bit is just to tell the program where to look for the X server (the program that actually does all the drawing).

---

### Post by IcemanV9 on 2007-01-12
[COLOR="Orange"]xload -remote [host][/COLOR] does NOT work.

[COLOR="Orange"]man xload[/COLOR] did showed me that my syntax is correct. So, what did I missed?!?

---


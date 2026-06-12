---
title: "Replace gnome-terminal with guake/tilda"
date: 2011-06-09
forum: Any Other OS
---

### Post by rodamu on 2011-06-09
Is there a way to totally replace the gnome-terminal with guake/tilda?

The problem I have is that in mint, in nautilus there is in the context menu, an entry which says "Open In Terminal" which is really usefull. What I want to do Is that whenever I right click on that entry, guake/tilda terminal pops up. In other words, make guake/tilda the default terminal.

PD: I recently discovered tilda, but it looks promising, thats why I'm asking for a solution regarding guake/tilda

---

### Post by yetiman64 on 2011-06-09
After installing guake/tilda, go to (for 10.10 and earlier) System > Preferences > Preferred Applications > System Tab and set the terminal emulator there.  

If you are on Natty search for Preferred Applications or go to System Settings on the log out menu and Preferred Applications will be in the control panel window somewhere.

That should set your choice for system wide use.

---

### Post by rodamu on 2011-06-10
I kept guake. I also found the option that you said, but when I set up guake as the default terminal app, when in nautilus, when i trie to open a location in the terminal nothing happens. I think that there must be a parameter, as in gnome terminal (which by the way is -x i think)

---

### Post by yetiman64 on 2011-06-11
You are correct guake cannot be launched from the preferred applications. I installed it here and checked "man guake" and it doesn't have the execute switch needed like gnome terminal or xterm. It is designed as a "drop down" quick access terminal only.

From "man guake",
> Guake is a drop-down terminal for GNOME and any other desktop.  It aims to  provide a  quick-access  terminal, that show/hide on screen with a simple key pressing. You need to put it in startup applications to have it available all the time. It installs an icon in the system tray for quick access when loaded. When loaded the key presses F11 and F12 are used to control it. F12 toggles it open/closed and F11 toggles it full screen and back to normal when it is opened. I like how configurable it is.

It can't replace gnome-terminal system wide it appears. I don't know if tilda is different with regard to its switches.

---

### Post by rodamu on 2011-06-11
ohh what a pity, seems I will have to keep gnome-terminal

---


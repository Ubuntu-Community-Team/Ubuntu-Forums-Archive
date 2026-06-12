---
title: "Launcher of a Terminal Command?"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by dmber on 2007-11-03
I'm using VNC Viewer to control a headless box I've got on my network.  Everything works fine, I'd just like to be able to launch it without having to go into the terminal type it in.

the command is:

```
$ vncviewer 192.168.1.4

```

can I make a launcher for that?  i'd also like to make it so the terminal doesn't stay open with vncviewer.

thanks!

---

### Post by jdg.gehrig on 2007-11-03
Do you run Gnome?

I run KDE and to do it in KDE you right click on the desktop and click "create new -> Link to application" Then go into the application tab and type your command in the command text box.

I've used XFCE too and it's almost the same but never Gnome.

I hope this helps, John

---

### Post by dmber on 2007-11-03
thanks for the help john.

I actually ended up using Compiz-Fusion.  

Under General -> Commands, I can put a shell command, then in General -> Action, I determined a keyboard shortcut for the command.

Works flawlessly...if you have CF.

---


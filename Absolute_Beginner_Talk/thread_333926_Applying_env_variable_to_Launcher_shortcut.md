---
title: "Applying env variable to Launcher shortcut"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by Seine on 2007-01-08
Hi

I'm running compiz and receive a white box when running netbeans 5.5.  This is resolved by setting the environment variable AWT_TOOLKIT=MToolkit.

I put *export AWT_TOOLKIT=MToolkit* in my .bashrc file. If I run netbeans from the terminal it works fine, but if I use the netbeans launcher from the gnome "taskbar thingy" the white box error remains.

Seemingly the env AWT_TOOLKIT is not set when I use the launcher. I changed the netbeans shell script (which is called by the launcher) so that it explicitly sets the variable, but this doesn't fix the problem either.

Any hints as to how I can effect this env var from the launcher?

Thanks
Seine

---

### Post by Seine on 2007-01-08
2 views, page 8. I must remember to post in prime time.

---


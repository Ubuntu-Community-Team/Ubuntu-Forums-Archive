---
title: "Exiting X Session / Booting to Console"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by tomcalloway on 2006-06-20
What is the right term "recovery console", or "console"?  Basically, I mean the command-line interface when an X session is not running.

I need to know how to exit a Gnome desktop X session, so I can use the "console" to edit my xorg.conf...  I've seen posts that recommend not to do this in your terminal during an X session.  Plus, I broke .conf and can't get to an X session.  I want to restore my backup .conf file

Also, it would be nice to know how to use a boot option to access the console directly on boot-up without entering an X session.

---

### Post by scr on 2006-06-20
To get into the console, you can hit for instance ctrl+alt+f2. However, to shut down X you will need to kill gnome display manager by:

sudo /etc/init.d/gdm stop

---

### Post by linear on 2006-06-20
Ctrl-alt-F1 should get you a shell prompt (a/k/a console or command prompt).
 
Once editing is done, **sudo /etc/init.d/gdm restart** or **sudo killall -HUP gdm** to restart Gnome.

---

### Post by IYY on 2006-06-20
Ctrl+Alt+Backspace also kills X, but it's a dirty method. I'd suggest the methods described above, even though I often use this way.

---


---
title: "stopping xterm"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by alienexplorers on 2007-02-16
What command do I use to shut down xterm and allows me to get to a command prompt.  I know startx starts the xterm, but I don't know how to end it.

Don

---

### Post by Bachstelze on 2007-02-16
xterm is just a terminal emulator for X, you can run it with the command *xterm* from the Run dialog.

I guess you were talking about the whole X server. You can switch from it to a console by typing Ctrl+Alt+Fx - where x is a number from 1 to 6 - and from there you can go back to your X with Alt+F7. If you want to rally stop the X serve (e.g. for installing the nvidia driver), do *sudo /etc/init.d/?dm stop* - put start instead of stop to start it againn or restart to stop it and rester it just after.

---


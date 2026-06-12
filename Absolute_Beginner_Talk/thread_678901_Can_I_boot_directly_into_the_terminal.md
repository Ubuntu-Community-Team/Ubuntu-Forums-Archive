---
title: "Can I boot directly into the terminal?"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by psam3 on 2008-01-26
Then if I do that can I update my video card drivers from there?

---

### Post by mortsahl on 2008-01-26
If you're running gnome, open a terminal window and type "sudo /etc/init.d/gdm stop" ... if running KDE, type "sudo /etc/init.d/kdm stop".  This will kill the graphical environment and drop you to a comamnd line.  From here you can do whatever you need to do to install your graphics driver.

If you need to return to the graphical environment (short of rebooting), just type startx

---

### Post by b0rka7a on 2008-01-26
Use [Envy]("http://albertomilone.com") for the drivers. It will install them automatically.

If you want to be in the terminal without the X server started you can press Ctrl+Alt+F1 and type:
```
sudo /etc/init.d/gdm stop
```
to stop the X server, then install the drivers.

---

### Post by psam3 on 2008-01-26
I can't boot into Ubuntu because I get the Input not supported message.

---


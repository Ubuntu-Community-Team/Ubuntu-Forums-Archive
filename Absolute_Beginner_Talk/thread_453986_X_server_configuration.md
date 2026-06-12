---
title: "X server configuration"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by azizzle on 2007-05-25
so i totally screwed up my x conf. I know what I did and know what to do to fix it, but I can't get to the X server because I can't get to the gui. is there a way i can configure it through terminal. oh yeah i tried  /etc/X11/xorg.conf. to no avail. TIA

---

### Post by Ek0nomik on 2007-05-25
Did you create a backup?  I hope so.

If you can only get to a command line, use:

```
nano /etc/X11/xorg.conf
```

nano will allow you to edit in command line (you don't need a GUI).  ;)

---

### Post by azizzle on 2007-05-25
edit: ok i fixed it, now how do i save this conf?? (sorry for my noobness) but it doesn't have a save option at the bottom.

---

### Post by Ek0nomik on 2007-05-25
Again, you can use nano to edit the file in command line.

Use the command I listed before... unless you have no idea what you changed.

In that case, you can **reconfigure** your xorg:

```
sudo dpkg-reconfigure xserver-xorg
```

This will **reconfigure** your xorg, so be warned you will lose any big changes you made.

---

### Post by azizzle on 2007-05-25
sorry, i neglected to elaborate. I used the nano, and fixed what i changed. But when i tried to save it, it told me that permission was denied. how should i get around this?

---

### Post by Ek0nomik on 2007-05-25
> **azizzle said:**
> sorry, i neglected to elaborate. I used the nano, and fixed what i changed. But when i tried to save it, it told me that permission was denied. how should i get around this?

Oh, just use sudo in that case.  Permission denied almost always means you don't have the proper "authentication" to change a file.  If your new to Linux, well, it's a Linux thing, but it's there to help.

```
sudo nano /etc/X11/xorg.conf
```

---

### Post by azizzle on 2007-05-25
Thanks! now how do i get back to the gui?? oh, did i mention, THANKS!!:D

---

### Post by Ek0nomik on 2007-05-25
No problem.  If you fixed your xorg, just do:

```
sudo shutdown -r now
```

than after it restarts, finishes loading, you should be back to your colored world.  :)

---


---
title: "Oops - There's gotta be a way to fix this..."
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by Corvalis on 2007-01-27
I've got Xubuntu installed and was playing around with the settings and I turned off the Graphical Login and now I can't launch the GUI.  I can log in from the terminal in recovery mode but how do I relaunch the GUI so I can fix my error?

Thanks in advance.:(

---

### Post by JamieC on 2007-01-27
Type 'startx' and hit return.

---

### Post by Tomosaur on 2007-01-27
Type:
```

sudo dpkg-reconfigure -phigh xserver-xorg
sudo dpkg-reconfigure gdm

```

---

### Post by Corvalis on 2007-01-27
wow you guys are quick.

its fixed, thx for the speedy help.

until next time...:D

---


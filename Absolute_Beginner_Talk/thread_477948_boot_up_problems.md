---
title: "boot up problems"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by ynot8tony on 2007-06-18
When initially installing Ubuntu, during the middle of the process there is an error message, "error starting GNOME Settings Daemon" the page keeps freezing at this point and I have to hard boot the system. What does this indicate?

It freezes on the page that is salmon colored background and a thin bar with the Ubuntu logo and three other icons.

---

### Post by st33med on 2007-06-18
I think you most likely mean that you are loading the desktop, not installing. Try Safe Graphics Mode when the Ubuntu menu loads.

---

### Post by ynot8tony on 2007-06-18
I tried starting the Safe Grpahics mode and the same error message popped up and the computer froze. I don't get it... I want to use Ubuntu but if it dosen't even load correctly then what is that saying about the program?

---

### Post by shamushand on 2007-06-18
Sounds like a video card problem...

Try doing this:
When GRUB loads, press ESC and select recovery mode
In the command line, type in 

```
sudo dpkg-reconfigure xserver-xorg
```

Configure it as needed, see if that helps. ;)

---


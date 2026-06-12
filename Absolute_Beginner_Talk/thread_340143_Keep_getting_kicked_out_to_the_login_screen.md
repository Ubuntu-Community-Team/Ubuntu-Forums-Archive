---
title: "Keep getting kicked out to the login screen"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by dlynch13 on 2007-01-16
I just installed Kubuntu for the first time yesterday.  Then, I tried to install Firefox.  It said it was successful, but I didn't see Firefox anywhere in the menus. After I rebooted, everytime that I try to login, I get the stopwatch and then it kicks me out to the login screen again. I am locked out. I've tried the Failsafe, KDE and Default sessions (available as options at the login screen) and they don't work either.  There are no error messages. 

How do I recover from this? 

Note that I can still do stuff from a terminal in the other windows (Ctrl+Alt+F3 for example.) I just can't get into the GUI.

Thanks, David.

---

### Post by aktiwers on 2007-01-16
I dont know, but I used to get this after installing my ATI drivers.
I normaly fixed it by login into Terminal mode and typing..

```
sudo dpkg-reconfigure xserver-xorg
```

But sorry I dont know.. you could try it :)

---

### Post by dlynch13 on 2007-01-16
Well...that didn't work. After I did this procedure, it did the same thing.  After rebooting, I am stuck at the command prompt again! ](*,) 

This EZ going version of Linux is not living up to it's promise...

-David.

---

### Post by highneko on 2007-01-16
Maybe this will help. It couldn't hurt.

Ctrl+Alt+F1. Enter your login name and password. Update with "sudo apt-get update && sudo apt-get dist-upgrade". Then restart with "sudo shutdown -r now".

Have you been trying to install beryl or something like that lately?

---


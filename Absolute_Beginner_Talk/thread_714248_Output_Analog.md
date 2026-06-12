---
title: "Output Analog"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by Valthinos on 2008-03-03
I had problems with my mouse and I followed the instructions here: [http://ubuntuforums.org/showthread.php?t=713453](http://ubuntuforums.org/showthread.php?t=713453). I must've done something wrong because whenever I start up Ubuntu, I get an error saying something like 1. Output Analog This Video Mode cannot be displayed. I can't do anything. It's a black screen with that text in the middle, somebody please help!

---

### Post by Infinite Recursion on 2008-03-22
Sounds like there's an error in the xorg.conf file.  You can try editing it through the command line using an editor like nano, to see if you can find the error.  If you don't see a command prompt on startup, try ctrl-alt-f2 from the error screen; that should take you to the command line.

Alternatively, you can restore the backup by using:
```
sudo cp /etc/X11/xorg.conf-backup /etc/X11/xorg.conf
```

To return to your desktop, you can either reboot or use ctrl-alt-f7.

Hope this helps!

---


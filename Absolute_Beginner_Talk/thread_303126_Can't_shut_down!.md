---
title: "Can't shut down?!"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by kbsuperstar on 2006-11-19
I recently installed beryl, and when I load my XGL session everything works fine. But when I try to shut down, the buttons for shutdown and restart are gone. How the hell do I fix this ?!

---

### Post by loell on 2006-11-19
well, you can stop beryl

 by

   ```
killall beryl-manager
```
 then now, the sutdown/restart/logoff window will show
 but normally it will show, even if beryl is running

---

### Post by kbsuperstar on 2006-11-19
Didn't work. killall beryl-manager only kills the manager; beryl is still running, and I still can't shut down. :(

---

### Post by loell on 2006-11-19
oh sorry, it should have been "killall beryl"
you can start the beryl-manager by running it in the command line, though in beryl icon, you can right click and "select window manager" and choose metacity, then try shuting down , if the window shutdown will show.

---

### Post by grte on 2006-11-19
If all else fails, opening a terminal and typing ```
sudo shutdown -h now
``` will work.

You can also replace -h with -r if you want to reboot, rather than halt.

---

### Post by kbsuperstar on 2006-11-19
Still doesn't work.

I really don't want to open a terminal every time I have to shut down or reboot, though. Any other ideas?

---

### Post by loell on 2006-11-19
this problem is similar to xcompmgr, where you can't shutdown , because the shutdown window is not shown.

if you press quit, will it just freeze?

---

### Post by MellonCollie on 2006-11-19
Just logout, and then shutdown from the login screen.

---

### Post by kbsuperstar on 2006-11-19
I can get log out, switch user, lock screen, and hibernate from my session

---

### Post by Cyr4x on 2006-12-03
The same for me with xcompmgr. Any advice? I'm tryin' to recreate an OSX desktop on my Gnome and, so need shadows.

---

### Post by loell on 2006-12-03
actually , in xcompmgr the shudown windw isn't just shown , you can memorize on where to click the shutdown button , somewhere along the center jus lower right, 


or create a script > logout.sh

```


#!/bin/sh

killall xcompmgr
gnome-session-save --kill




```

and creat a launcher in gnome panel, for the script

---

### Post by Cyr4x on 2006-12-04
If i could add this script to close button in System menu it would be great.

---


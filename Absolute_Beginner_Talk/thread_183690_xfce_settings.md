---
title: "xfce settings"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by u04f061 on 2006-05-28
i opened settings>disks>partition1 and my xfce settings lost and desktopbackground of gnome came up. now i can't see xfce default  background.now xfce is not as fast as before.now it is running with gnome speed.
now i can't open files with single click as before.plz help me in resolving this

---

### Post by bluenova on 2006-05-28
If nautilus is running, close it.

---

### Post by 5-HT on 2006-05-28
Easiest thing would be to just logout of the session without saving, and boot back into XFCE.

If that doesn't do it, as bluenova mentioned, kill off any instances of nautilus.
You might need to start up xfdesktop again: ```
 xfdesktop & 
``` and save your session.

Funny how that happened for you though, running that utility has not mucked up xfdesktop for me.

If you do want to use nautilus and not have it draw the desktop, you can call it up with: ```
 nautilus --no-desktop 
``` 
HTH

---

### Post by u04f061 on 2006-05-28
i also rebooted my pc.still the problem persists.i don't know how to run nautilus ,how to close.can u tell me how to close it.does it open itself?

---

### Post by u04f061 on 2006-05-28
[QUOTE=5-HT]Easiest thing would be to just logout of the session without saving, and boot back into XFCE.

If that doesn't do it, as bluenova mentioned, kill off any instances of nautilus.
You might need to start up xfdesktop again: ```
 xfdesktop & 
``` and save your session.

Funny how that happened for you though, running that utility has not mucked up xfdesktop for me.

If you do want to use nautilus and not have it draw the desktop, you can call it up with: ```
 nautilus --no-desktop 
``` 
HTH[/QUOTE]

strange thing happened.when i posted my reply ,then i came across your reply and used
 xfdesktop & 
my xfce desktop came again.thnx

---


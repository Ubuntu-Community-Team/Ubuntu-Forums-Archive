---
title: "[SOLVED] this thing logs me out, whata..."
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by Gmbrdilos on 2007-08-06
whenever I log in I hear the log in sound, see the splash screen, then see the following error and it logs me right out.
```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "gevorg"
SESSION_MANAGER=local/seberus:/tmp/.ICE-unix/5613
Initializing gnome-mount extension

(update-notifier:5663): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-power-manager:5680): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

```

what is this? can anyone help?

---

### Post by Gmbrdilos on 2007-08-06
I hate to bump, but I am really left without a desktop here, could use some help.

---

### Post by Rocket2DMn on 2007-08-06
A similar post is found here - [http://ubuntuforums.org/showthread.php?p=1454505](http://ubuntuforums.org/showthread.php?p=1454505)
I'll keep looking into it and post back if I find more.
Can you log in with recovery mode?

---

### Post by Rocket2DMn on 2007-08-06
More here - [http://ubuntuforums.org/showthread.php?t=510293](http://ubuntuforums.org/showthread.php?t=510293) 
and here - [http://ubuntuforums.org/showthread.php?t=386841](http://ubuntuforums.org/showthread.php?t=386841)

It seems like removing your gnome config files/directories might help, though it is an imperfect solution.  Maybe just changing their names or moving them somewhere else is a good idea so you can recover them later if needed.  Proceed at your own discretion.  I'll keep looking for another few minutes.

ADDED: The posts by Omegatron here might be of interest to you as well (pages 1 and 2) - [http://ubuntuforums.org/showthread.php?t=249411](http://ubuntuforums.org/showthread.php?t=249411)
Good luck.

---

### Post by Gmbrdilos on 2007-08-06
> **Rocket2DMn said:**
> A similar post is found here - [http://ubuntuforums.org/showthread.php?p=1454505](http://ubuntuforums.org/showthread.php?p=1454505)
I'll keep looking into it and post back if I find more.
Can you log in with recovery mode?

thanks I'll give those links a try, actually when I log in and get that window if I minimize it and dont click ok I will stay logged in an operating normal. as soon as I click ok the session ends.

---

### Post by Gmbrdilos on 2007-08-06
none of those threads helped, however,
well I dunno how much of a solution this was but I tried to retrace my steps from previous session and removed a custom splash screen from a program called gnome art, that resolved the issue.

---


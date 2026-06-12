---
title: "Session lasted only 10 seconds, hm... not &quot;.ICEauthority&quot; 's problem"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by Jeremy_Wlk on 2007-11-05
Hi there! Now I see that Ubuntuing demands more of my involvement that I expected at the beginning. The problem is I can't login into GNOME-session, so I have use GNOME-failsafe last few days instead.

There is what I see when trying to login (copy&past from .xsession-errors log):

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "jwlk"
/etc/gdm/Xsession: Beginning session setup...
Failed to execute message bus daemon /usr/bin/dbus-daemon: Permission denied.  Will try again without full path.
Failed to execute message bus daemon: Permission denied
EOF in dbus-launch reading address from bus daemon
```

Seems rather known issue, I've read forums and bug reports, but I haven't found appropriate solution. Mm, someone advised me to delete all stuff from Home folder containing "gnome" gradually, but I really in doubt to follow this way...

**Deleting or renaming the .ICEauthority either in GUI nor in safemode didn't help, unfortunately.**

What should I try to do else? Please help.

---

### Post by jimbren on 2007-11-05
Do you own all of the files in your /home directory?

Try this:
```
sudo chown -R yourusername:yourgroupname *.*
```

---

### Post by Jeremy_Wlk on 2007-11-05
```
sudo chown -R jwlk:jwlk *.*
```
resulted in:
```
chown: cannot access `*.*': No such file or directory
```
I tried
```
sudo chown -R jwlk:jwlk *****
```
and
```
sudo chown -R jwlk:jwlk **.***
```
but still couldn't log in as jwlk.

Also I attempted to experiment with permission's rights for */home/jwlk* and ended up with 644 and exec: on.

Now many of commands in Terminal don't demand "sudo" - is it normal?

The problem remains actual.

---

### Post by Jeremy_Wlk on 2007-11-07
As my experiments hadn't led me to solution, i prefered to reinstall Linux. Ok, I hope this problem won't appear again...

---


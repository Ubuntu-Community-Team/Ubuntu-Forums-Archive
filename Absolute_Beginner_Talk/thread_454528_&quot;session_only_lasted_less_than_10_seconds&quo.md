---
title: "&quot;session only lasted less than 10 seconds&quot;"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by Outrunner on 2007-05-25
Hello, when I try to login I get the error above... details

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /etc/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l " :0" "overmind"
/etc/gdm/Xsession: Beginning session setup...
mkdtemp: private socket dir:Permission denied
```

Fixing errors in the dead of night, just what I hoped for... I'm sorry if I missed anything, I'm pretty tired at the moment.

---

### Post by Seisen on 2007-05-25
What did you do before this happened?

---

### Post by Outrunner on 2007-05-25
Let's see... I was running firefox, and also making an .iso with gnomebaker out of my starcraft cd to use instead of the cds themselves(there's a thread about this in the Tutorials section). Then, while still having desktop effects on, I decided to start nexuiz. Such a big surprise when the screen went all fuzzy for a minute and instead of starting the game the screen goes black. The only thing I could do except a hard reboot was to restart the xserver so I did. 

Imagine my surprise when I couldn't log in

EDIT: Only failsafe termial works, which I'm using now...

EDIT: Since nobody has any ideas as of yet, I'll be off for the night. I hope I'll see you in the morning ;)

---

### Post by Outrunner on 2007-05-26
Well, it's been about 9 hours now, does anyone have an idea? I tried creating a new user and logging in, but there's the  same problem.

---

### Post by fenian on 2007-05-26
When this happened to me I had to reconfigure xorg with this command...

> sudo dpkg-reconfigure xserver-xorg

you will lose beryl and probably have to setup nvidia drivers aagain.

---

### Post by Outrunner on 2007-05-26
Reconfigured xorg then restarted, but I still get the same error. 

Why Ubuntu why are you tormenting me??

---

### Post by JDahl on 2007-05-26
I've run into similar problems when write properties to my home-dir were wrong,  and when my
disk was full.

---

### Post by Outrunner on 2007-05-26
Doesn't matter now, I decided to take the easy way out and backup/reinstall. Thanks for your help anyway.

---


---
title: "Help with sessions!"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by andycyca on 2007-04-16
Hi everyone!

Straight to the point. I was using Firefox in my usual session in Xubuntu. While I was at it, I wanted to change themes and icons. I did, but Firefox froze completely and my User Interface window dissapeared completely. My 2 panels were gone too, so I couldn't do anything. I let it waiting like 15 minutes and still nothing. I restarted the whole system.

Now, usually when I enter my session a window comes out asking which session I want to use (**not the login screen**). Since I'm the only user of this mahine, there's only one session "default". When I logged in, the splash screen displayed "select session" , froze for some seconds and took me back to the login screen. Now it seems I can't use that login session. What can I do? I have many things there that I don't want to re-install (like my Firefox plugins)

I'm pretty sure, I wasn't downloading anything when all froze
I'm posting as root

Any ideas? Thanks!
-----------
EDIT: My "normal" username is general. I've found on home/general a .txt named '.xsessions errors'. This is what it has:

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "general"
/etc/gdm/Xsession: Beginning session setup...
/usr/bin/startxfce4: X server already running on display :0

(xfce4-session:4575): Gtk-WARNING **: Theme file for zelda-cursors-1.0 has no directories

Segmentation fault (core dumped)
```

BTW I wanted to change my icons theme to "zelda-cursors". That's the last thing I did befor all this began.

---

### Post by leibowitz on 2007-04-25
themes are located in **~/.themes** directory. Just try to delete the whole zelda-cursors-1.0 directory. Because that's  maybe what is causing the crash

---


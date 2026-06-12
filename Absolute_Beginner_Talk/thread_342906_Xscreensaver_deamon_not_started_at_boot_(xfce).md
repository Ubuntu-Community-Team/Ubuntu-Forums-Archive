---
title: "Xscreensaver deamon not started at boot (xfce)"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2007-01-20
**[COLOR="Red"]Edit: I solve this and for anyone else who wants to know all you have to do is log out then log back in but make sure you select your session type as Xfce.[/COLOR]** To see why or if it does not work read the [7th post]("http://ubuntuforums.org/showthread.php?p=2047486#post2047486")

I'm running Edgy, command line system with xfce install. So I install xscreensavers manually and now it does not start on boot. How to do fix this?

---

### Post by guysmiley25 on 2007-01-20
Bump!

---

### Post by guysmiley25 on 2007-01-22
Bump again. I know I could just auto start it but I want to know why its not starting? also I don't want to have to setup the auto start for each person and machine.

---

### Post by bodhi.zazen on 2007-01-22
[http://doc.gwos.org/index.php/CustomXSession](http://doc.gwos.org/index.php/CustomXSession)

---

### Post by guysmiley25 on 2007-01-22
Solved.

All I had to do was select xfce from the session thing in gdm. startxfce4 was not being executed!

Do not know how xfce was starting before hand though.

---

### Post by bodhi.zazen on 2007-01-22
? xfce4-session

---

### Post by guysmiley25 on 2007-01-22
Well I still had Ubuntu Dapper installed on my laptop so I started comparing the difference between files between that and my new Edgy desktop.

So I got to the point where I found where xscreensaver was being executed. and that was ```
/etc/xdg/xfce4/xinitrc
```

On both machines the file contained
```

# Launch xscreensaver (if available), but only as non-root user
test $UID -gt 0 -a -z "$VNCSESSION" && xscreensaver -no-splash &

```

So the only reason that xscreensaver would not start would be because "/etc/xdg/xfce4/xinitrc" is not being started.

So I checked out startxfce4 ```
/usr/bin/startxfce4
``` and found this at the very bottom of both machines.

```

if [ -f $BASEDIR/xinitrc ]; then
  exec $prog $BASEDIR/xinitrc $*
elif [ -f $HOME/.xfce4/xinitrc ]; then
  mkdir -p $BASEDIR
  cp $HOME/.xfce4/xinitrc $BASEDIR/
  exec $prog $BASEDIR/xinitrc $*
else
  exec $prog /etc/xdg/xfce4/xinitrc $*
fi

```

Studying that and the rest of the file, and knowing that I have no "$HOME/.xfce4/xinitrc" or "$BASEDIR/xinitrc" I decided that "/etc/xdg/xfce4/xinitrc" must be getting executed. So whats going on I wonder?

Oh but what if startxfce4 was not being run??? But of course it is because the "/usr/share/xsessions/xfce4.desktop" executes startxfce4 witch then executes xinitrc, witch then executes xscreensaver. Or is it?

So I logged out and then in gdm from the sessions sections selected Xfce and logged in and it worked.

So I have no idea what session I was logging into before hand! Guess it does not really matter now because it's fixed but I still want to know. And what ever it was it was starting xfce4 without startxfce.

---

### Post by foresto on 2008-06-26
For the sake of anyone who comes across this thread, I had the same problem.  It kept gnome-screensaver from running, which kept my monitor from powering down when idle.  It also kept ~/.config/xfce4/Xft.xrdb from being merged into the xrdb database at login time, which kept my font settings from being visible to Firefox 3.  Here's a related bug report:

[https://bugs.launchpad.net/ubuntu/+bug/231311](https://bugs.launchpad.net/ubuntu/+bug/231311)

---


---
title: "Problems starting default Gnome session"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by saphil on 2007-03-13
Here is my .Xsession-errors file.  What is happening is that the session will not start, comes up with a "You have been logged in less than 10 seconds.  If this is not what you intended, log in using a failsafe mode to effect repairs."  Or something like that.

The detail of the error mssg is in the Xsession-errors file.  I have been told to dump .ICEauthority and .Xauthority, but this has no effect on the issue.  Having the .Gnome2 and .Gnomeprofile stuff deleted and letting the system rebuild them resulted in messing up all my icons, so I put the old ones back

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "wolf"
/etc/gdm/Xsession: Beginning session setup...
export: 18: //this: bad variable name
Xsession: X session started for wolf at Tue Mar 13 02:57:01 EDT 2007
SESSION_MANAGER=local/yossarian:/tmp/.ICE-unix/8063

** (gnome-session:8063): WARNING **: Host name lookup failure on localhost.
Initializing gnome-mount extension

** (update-notifier:8177): WARNING **: no cdrom: disk

evolution-alarm-notify-Message: Setting timeout for 79368 1173848400 1173769032
evolution-alarm-notify-Message:  Wed Mar 14 01:00:00 2007

evolution-alarm-notify-Message:  Tue Mar 13 02:57:12 2007

** Message: drive = 0
** Message: volume = 0

(gnome-panel:8139): Gtk-CRITICAL **: gtk_icon_theme_lookup_icon: assertion `GTK_IS_ICON_THEME (icon_theme)' failed
** Message: drive = 0
** Message: volume = 0

```What now?

---

### Post by wizzard7 on 2007-03-13
Hey.. I have had the exact same error, this is the first Ihave found refering to it online.  I'd be interested in the cause also. i ended up having to reinstall to get it fixed. Not my first choice, exactly.. [http://ubuntuforums.org/images/smilies/smiley-faces-75.gif](http://ubuntuforums.org/images/smilies/smiley-faces-75.gif)

---

### Post by saphil on 2007-03-14
Well, a reinstall would certainly "fix" the issue.  I do reinstalls fairly often, but it takes a lot of time.  I have seen several references to similar issues, but no solutions, so far.  What I like about Unix and Linux is that everything is a file and so can be modified (if you know where to look).  The answer is out there somewhere..  Somebody knows it.  
:popcorn::popcorn::popcorn:
Seems like the issue is in some file called by the gdm scripts in /etc/gdm/..

---


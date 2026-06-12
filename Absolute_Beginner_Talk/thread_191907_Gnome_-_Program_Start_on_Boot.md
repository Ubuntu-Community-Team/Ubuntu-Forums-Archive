---
title: "Gnome - Program Start on Boot"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by fopetesl on 2006-06-08
It has been said that in Gnome it's easy to add a startup-on-boot program.
Well, I cannot find it.

Also my 'Help' program has nada in it, should I have loaded something?

---

### Post by frodon on 2006-06-08
What do you want to do ?
Start a program/script at the beginning of the session or on startup (i mean before the login screen) ? 

For session scripts/programs go to System > Preference > session there a tab to add scripts to execute on startup.

To execute a script on startup put it under /etc/init.d and run a : ```
sudo update-rc.d *name_of_script* defaults
```Then reboot
If you just want to save your session you can use this command : ```
gnome-session-save
```

---

### Post by nkhansen on 2006-06-08
It's in the 'Startup programs' flag, in the 'Sessions' dialog.

---

### Post by fopetesl on 2006-06-08
Thanks for that.
Before or after login screen?  At this point I am not sure since I am (re)writing a touchscreen kiosk application which normally would bypass gdm (still haven't got that bypass sorted) but it would be nice to have the kiosk (mozilla) running full screen on top of a 'normal' gnome desktop which I could access by plugging in a USB keyboard and maybe switching workspaces.

I have read that an ~/.xsession file will be executed in preference to gdm (or with?) but that doesn't work for me unless I hide /etc/rc2.d/@S13gdm, login as User-me and run startx (sorry, that uses ~/.xinitrc).  Not a lot of use in kiosk mode.

The [COLOR="Blue"]System > Preference > session[/COLOR] option works fine.

---

### Post by robinsons on 2006-06-09
Found this myself today, check in System -> Preferences -> Sessions.  There's a 'Startup Programs' tab in there.

Whoops!  Just realised the forum wasn't showing replies by default, thought this was unanswered.  Sorry for the bounce :)

---


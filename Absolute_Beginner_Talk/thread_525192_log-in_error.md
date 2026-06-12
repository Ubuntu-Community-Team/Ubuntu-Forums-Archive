---
title: "log-in error"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by subfactors on 2007-08-14
I enabled the save session function under System -> Preferences -> Sessions. So I restarted the computer to test it. Since then the following error message appeared every time I log on to ubuntu 7.04. I can only avoid it by log on via failsafe mode. Can anyone help please?

-------------------------------------------------------------------------------------------------------------------
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "jason"
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/scim.
Launching a SCIM daemon with Socket FrontEnd...
Loading simple Config module ...
Creating backend ...
SESSION_MANAGER=local/desktop:/tmp/.ICE-unix/5850
Loading socket FrontEnd module ...
Starting SCIM as daemon ...
Launching a SCIM process with x11...
Loading socket Config module ...
Creating backend ...
Loading x11 FrontEnd module ...
GTK Panel of SCIM 1.4.4

Starting SCIM as daemon ...
SCIM has been successfully launched.
Smart Common Input Method 1.4.4

Initializing gnome-mount extension

(gnome-cups-icon:5941): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-terminal:5949): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-power-manager:5950): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(update-notifier:5940): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

---

### Post by DeHorde on 2007-08-14
Not sure if this will work, but you could try moving the file ~/.gconfd/saved_state out of the way (don't delete it for now). 
Also, what is in your ~/.xsession-errors (if anything)?

---


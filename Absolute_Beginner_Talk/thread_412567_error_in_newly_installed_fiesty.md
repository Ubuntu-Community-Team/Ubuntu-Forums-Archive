---
title: "error in newly installed fiesty"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by locke.dragon on 2007-04-18
SOLVED

i just upgraded to fiesty.  now when i log in,  i get the message...

> 
Your session only lasted less than 10 seconds.  If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.  Try logging in with one of the failsafe sessions to see if you can fix this problem.


with the details...

```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "link"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/Ubuntu:/tmp/.ICE-unix/5875
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: "" found in configuration database is not a valid value for keybinding "panel_main_menu"
Window manager warning: "" found in configuration database is not a valid value for keybinding "run_command_window_screenshot"
Initializing gnome-mount extension

(gnome-power-manager:5973): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(update-notifier:5969): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.


```

if i press ok or close it, it goes back to the login screen.  i can just ignore it and the whole system works fine, but i'd like to fix it.  any ideas?

it may help to add that beryl, my usual window manager, won't start automatically.  but i can get it running through terminal.

---

### Post by locke.dragon on 2007-04-18
fixed it after updating with apt-get.

---

### Post by matt91 on 2007-04-20
i have same problem. my error details are:

> 
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "link"
/etc/gdm/Xsession: Beginning session setup...


i cannot login even after pressing ok and trying again.

---

### Post by zerohalo on 2007-04-21
locke.dragon, would you mind elaborating on how you fixed it? What did you update with apt-get? I'm experiencing the exact same problem and have been unable to fix it (though my system is fully up-to-date with apt-get as far as i can tell. thank you.

---

### Post by redbluemangle on 2007-04-21
I'm having the same problem and the updater only installed some nfs related packages.

---

### Post by zerohalo on 2007-04-21
I figured the problem had something, because logging in as another user worked fine, but my main user (where I had beryl enabled) was causing the error.

I had already removed beryl and still it hadn't solved the problem, but I finally realized that I should have purged the beryl config files. So I reinstalled beryl and beryl-core and then:

# apt-get remove beryl --purge
# apt-get autoremove --purge 
(the second line to get rid of all the dependencies).

I haven't gotten Beryl working yet, but at least this problem is solved.

---

### Post by locke.dragon on 2007-04-23
the main problem for me was that i had cairo's clock installed.  after un-installing and updating my system, it's working perfectly.

---


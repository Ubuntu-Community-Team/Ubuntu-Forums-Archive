---
title: "I just killed Gnome."
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by Rotaj on 2007-04-14
I just killed Gnome. I was experimenting with a couple of icon themes. After clicking on one, all panels and desktop items went away, just the desktop and the mouse left. I shut down the computer. I restarted, logged in, and waited. There are no desktop or gnome icons at the slpash screen. It hangs at this point.

Is there a way to restore the previous desktop settings from the CLI?

I can access file on this drive from XP.

---

### Post by Rotaj on 2007-04-14
unfortunately, the information below does not tell me much

sudo nano .xsession-errors

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "XXXXXX"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/Hailey:/tmp/.ICE-unix/4548

(gnome-session:4548): Gtk-WARNING **: Theme file for ComixCursors-Black-Large has no directories

---

### Post by ComplexNumber on 2007-04-14
its because you clicked on a cursor theme. do the following:
-logout
-select failsafe terminal as your session
-go to the following location and change the icon theme setting to  'Human'.
**/home/<your-username>/.gconf/desktop/gnome/interface**
-exit to get back to the login screen
-change your session back to gnome and log in



btw although whether the cursor themes show up in the list of icons themes is up to the author of the cursor theme, they should ideally make them hidden by default. why they don't i don't know. howver, what you can do is go to the index.theme file in all your cursor themes and add the following line:
**Hidden=true**

---

### Post by Rotaj on 2007-04-14
You would think hiding the cursor themes would be automatic under a synaptic package.

---

### Post by ComplexNumber on 2007-04-14
true.
did you solve the problem?

---

### Post by Rotaj on 2007-04-14
not yet,  I cannot find an icon_theme directory. Please see attached image

---

### Post by ComplexNumber on 2007-04-14
> **Rotaj said:**
> not yet,  I cannot find an icon_theme directory. Please see attached image
there isn't an icon theme directory in there. its a setting called Icon_theme. in the interface directory, there is a file called %gconf.xml. in there, there is a setting called "Icon_theme". change the icon theme from "ComixCursors-Black-Large" to "Human"

---

### Post by Rotaj on 2007-04-14
Thank you for all of your help!!!

---

### Post by ComplexNumber on 2007-04-14
you're welcome. so is everything restored back to normal now then?

also i would suggest that you change the cursor themes in your icon directory to include the line 'Hidden=true' so that this doesn't happen again.

---

### Post by picpak on 2007-04-14
I've done this before too. I think my solution was to delete the .gnome2 directory in my home folder, but this is a much better solution. Thanks!

---


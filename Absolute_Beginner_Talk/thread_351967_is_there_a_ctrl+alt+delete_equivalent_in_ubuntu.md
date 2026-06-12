---
title: "is there a ctrl+alt+delete equivalent in ubuntu?"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by MSlaveubu on 2007-02-02
or some other way to stop programs when they are running wild?

---

### Post by kerry_s on 2007-02-02
ctrl+alt+esc will give the kill icon(skull&bones) then you just click on the app you want to kill.

---

### Post by MSlaveubu on 2007-02-02
> **kerry_s said:**
> ctrl+alt+esc will give the kill icon(skull&bones) then you just click on the app you want to kill.


when I do that, nothing happens?

---

### Post by NewOldTimer on 2007-02-02
I'm using edgy, and right clicking on the panel >add to panel> force quit  gives  1 way of doing it.

---

### Post by annda on 2007-02-02
you can run

```
top
```

from the terminal, identify the rogue application by pid (just try it) and type k for kill - it will ask you for the pid.

another great possibility is **xkill** - from the terminal or press Alt+F2 and type xkill. that will give your cursor the skull (mentioned in a previous post) with which you can kill any window application - one of the best things windows users miss (including me in the past).

---

### Post by tchoklat on 2007-02-02
there is a synaptic applcation that mimics <ctr><alt><del>
 
 
tony

---

### Post by l951b951 on 2007-02-03
> **MSlaveubu said:**
> when I do that, nothing happens?

Same here, it changes my focus to the panels but nothing happens.  I just had a freeze up where my mouse quit responding.  I tried alt+F4 and ctrl+alt+del to no avail.  Had to hard boot it.  Any other solutions?

---

### Post by kregg on 2007-02-03
If you get [Automatix](http://www.getautomatix.com), then you can download and install this a task manager similar to Windows XP/NT/2000

---

### Post by mcglnx on 2007-02-03
You can aslo configure an extra button to trigger the logout menu - I've done this on my laptop and it's quite handy! and no more complicated keyboard sequence!

---

### Post by Rhubarb on 2007-02-03
> **kerry_s said:**
> ctrl+alt+esc will give the kill icon(skull&bones) then you just click on the app you want to kill.

This will not work in Gnome, I know for sure this works on KDE (Kubuntu).

---

### Post by me1on on 2007-02-03
You can enable Ctrl+Alt+Del to open the GNOME system monitor by copying this code (from ubuntuguide.org) and pasting it in the terminal:
```
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"
```
The GNOME system moniter can view/kill processes and view the computer's resources that are being used.

---

### Post by lwtinman17 on 2007-02-03
automatix does have an option to implement a ctrl-alt-del.  It's listed under the miscellaneous listing and does work with gnome.

---

### Post by Patrick K on 2007-02-03
> **MSlaveubu said:**
> when I do that, nothing happens?

The right <alt> key doesn't work the same in Ubuntu as in windows. Try the left key. I'm in KDE right now and the left <alt+del+esc> combo brings up the kill icon. The right <alt+del+exc> combo brings up the process table (KDE System Guard). From here you can select the app to kill. 

I've remapped the right <alt> key in Gnome to act as a normal <alt> key so I don't know for sure what it does now.

---

### Post by david_2001 on 2007-02-03
Ctrl + Alt + <-- (the back space) will kill the current X session, taking you back to the login screen.  Otherwise, use the Force Quit panel applet to kill individual applications.

---

### Post by jediborger on 2007-02-03
If you goto System-Administration-System Monitor, this gives you something similar to the windows task manager. Basically a list of process that you can kill as well as computer statistics and a list of all mounted drives. I use this and the panel applet when I have application problems.

---


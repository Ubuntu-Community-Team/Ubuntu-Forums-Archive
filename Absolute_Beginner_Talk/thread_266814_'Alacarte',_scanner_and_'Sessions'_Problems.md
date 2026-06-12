---
title: "'Alacarte', scanner and 'Sessions' Problems"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by TheForkOfJustice on 2006-09-27
I can no longer get Alacarte to start and I don't know why. Therefore I cannot edit my menu. Smeg is not installed.

In my System>Preferences>Sessions>Startup Programs I cannot get any changes to the Starup tab to save. I'm trying to add 'gaim' and 'xscreensaver -no-splash' (for replacing gnome-screensaver with xscreensaver) and they won't save. Nothing saves.

ALSO ... :wink:

While I'm here can you guys tell me how to get my Mustek 600 III EP Plus scanner to work. I followed the HOWTO and enabled mustek_pp and changed the port to parport0 but still nada. I also have a 
printer which connects to the parport through the second port on the scanner, a Canon BJC-250.

If you need info let me know so I can deliver. If you need a log file tell me where to find it first (I have no clue where those are).

---

### Post by llamakc on 2006-09-27
the flag to xscreensaver would be (provided you installed the package "xscreensaver":

xscreensaver --no-splash

and not

xscreensaver -no-splash

Logs are in /var/log

---

### Post by TheForkOfJustice on 2006-09-27
It doesn't matter what I type into 'Sessions'. NOTHING SAVES.

Doesn't matter if I carefully type it in or smash my hand on the keyboard. None of the settings remain once I close the window and restart 'Sessions'. I always have to use the launcher I created to start the xscreensaver daemon.

---


---
title: "I'm lost: log in to xgl-session constantly returns to login"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by fsando on 2007-01-28
situation:
laptop ati x1600
Everything was working but had to fix what wasn't broken :( 
Had a working xgl-session with beryl and all.
ati-drivers was 8.28.8
Downloaded and installed the 8.33.6 drivers from ati-site.
Had to uninstall previous drivers - (ignored warnings to stay with the old ones - sic!)
From then on every attempt to login to xgl has failed.
I completely removed everything xgl and fglrx and then reinstalled (through synaptics)
Login to xgl still fails (ending up at the login screen)

What should I do?
Should I do the Ms-windows thing and reinstall everything from scratch? Or is there some other solution?

/usr/bin/startxgl.sh
```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
exec dbus-launch --exit-with-session gnome-session

```What other info is needed?
UPDATE:
Changed /usr/bin/startxgl.sh to:```
#!/bin/sh
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1 gnome-session

```Now I'm allowed in and Beryl will run. But its a kde-like desktop, the font is too big and I'v lost my native keyboard (some of it at least)

UPDATE 2:
Now everything work as before
Changed /usr/bin/startxgl.sh to:```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer & DISPLAY=:1
exec dbus-launch --exit-with-session gnome-session

```I see no obvious difference except 'DISPLAY' is on a line of its own in the first version.
I've spent most of today searcing the net, restarting, experimenting - looking through my own notes on how I got things working etc. to no avail - and the moment I post a question my system starts working. It probably got scared of the Ubuntu-hordes rushing to 'deal' with it. :D

UPDATE 3:
Even got my 'restart' and 'shutdown' buttons back:```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer & DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie" 
exec dbus-launch --exit-with-session gnome-session
```

---


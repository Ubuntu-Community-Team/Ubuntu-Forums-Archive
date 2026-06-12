---
title: "fluxbox startup problem"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by zetsumei on 2006-12-23
heres my .fluxbox/startup file

> 
exec /usr/local/bin/fluxbox
fbsetbg -l
gnome-volume-manager &
xscreensaver -nosplash &
gdesklets &
gaim &
conky &
devilspie &
gnome-terminal &


when i log into fluxbox none of these programs start up...why!?

---

### Post by taurus on 2006-12-23
Add these two lines to the end of it!!!

```

# This MUST be the last command!
exec /usr/bin/fluxbox -log ~/.fluxbox/log

```

---

### Post by zetsumei on 2006-12-24
yea that worked, someone in the #ubuntuforums told me XD

---

### Post by taurus on 2006-12-24
> **zetsumei said:**
> yea that worked, someone in the #ubuntuforums told me XD

XD!!!  I don't even know what that is...  :-k

---

### Post by spockrock on 2006-12-24
its just suppossed to be a simley face just on its side smile but eyes close kinda something like this, >_<

---

### Post by bodhi.zazen on 2006-12-24
> **zetsumei said:**
> yea that worked, someone in the #ubuntuforums told me XD

:redface: Wonder who that was :rolleyes:

Hey, sorry about that, but I don't have a line

exec /usr/bin/fluxbox -log ~/.fluxbox/log

In my startup.

At any rate, welcome to Fluxbox :p

---


---
title: "Lock screen keys stops working"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by UltraMathMan on 2006-09-10
I like to use ctrl+alt+l to lock my screen when I need to leave my computer. The problem is occasionally the shortcut doesn't work (I can still lock the screen manually). Any suggestions?

---

### Post by goatmale on 2006-09-10
are you using gnome?
Mine is set to ctrl l and mine works fine...

---

### Post by UltraMathMan on 2006-09-11
yeah, I am using gnome. It works fine most of the time but occasionally (like right now) it just doesn't work until I reboot the entire OS.

---

### Post by jordanmthomas on 2006-09-11
when it doesn't work...is the screensaver running?
```

ps -A | grep screen

```

---

### Post by UltraMathMan on 2006-09-11
It returns

```
31098 ?        00:00:00 gnome-screensav
```

---

### Post by UltraMathMan on 2006-09-11
hmmm now it's working again - I still had /usr/bin/startcompiz running as a start up program so I changed it to /usr/bin/compiz-start and restarted the xserver and now it's working again (maybe logging into XGL/Compiz with that running then running /usr/bin/compiz-start then going back to the regular GUI was causing the problem?) Anyway, if it happens again I'll be back - thanks  for your help :)

---


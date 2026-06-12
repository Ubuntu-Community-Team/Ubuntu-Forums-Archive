---
title: "My desktop terminal starts up when i login..."
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by zetsumei on 2007-09-10
My desktop terminal comes up transparent when I login via Gnome, but if I login under fluxbox, it won't show up.  I've added it to the list of start up programs, but nothing happens.

---

### Post by zetsumei on 2007-09-10
is there something else i have to run to get my terminal to startup in fluxbox?

---

### Post by RedSquirrel on 2007-09-10
You need to add it to ~/.fluxbox/startup, near the bottom.

```

.
.
.
# Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.
#
# unclutter -idle 2 &
# wmnd &
# wmsmixer -w &
# idesk &
[COLOR=Blue]gnome-terminal &[/COLOR]

# And last but not least we start fluxbox.
# Because it is the last app you have to run it with ''exec'' before it.

exec /usr/bin/fluxbox
# or if you want to keep a log:
# exec /usr/bin/fluxbox -log "/home/user/.fluxbox/log"
```

---

### Post by zetsumei on 2007-09-11
SOLVED.

I forgot the devilspie and terminal in the startup file.

---


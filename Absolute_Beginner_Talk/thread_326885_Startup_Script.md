---
title: "Startup Script"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by opticalfiber on 2006-12-28
Hi guys, I'm new on this forum and I need some help... I have an HP laptop nc6400 and as it says in this page [http://hpwiki.cactii.net/hpwiki/NC6400](http://hpwiki.cactii.net/hpwiki/NC6400) in SD/MMC reader Paragraph: "To fix this, just put the following somewhere in the startup scripts: setpci -s 02:06.2 4c.b=02" Can somebody tell me how can I make it?:confused:  Thx a lot
p.s.: I thought about making a script called (for ex.) cardreader:
#! /bin/bash
setpci -s 02:06.2 4c.b=02

and put in /etc/init.d/ 
I guess it's wrong, but I'm here to learn!

---

### Post by daller on 2006-12-28
Run this command:

echo "setpci -s 02:06.2 4c.b=02" >> /etc/init.d/bootmisc.sh

---

### Post by opticalfiber on 2006-12-28
thx a lot daller!!!

---

### Post by insane_alien on 2006-12-28
system > preferences > sessions  > startup

add the command in there and it'll do it. i don't know how to do it via CLI but this is the GUI way and it works.

---

### Post by daller on 2006-12-28
> **insane_alien said:**
> system > preferences > sessions  > startup

add the command in there and it'll do it. i don't know how to do it via CLI but this is the GUI way and it works.

Doesn't "setpci" require root permissions? (and therefore to be run before gnome...)

---


---
title: "customize avant-window-navigator"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by locke.dragon on 2007-05-04
hey there.  i just installed avant and am impressed.  i had a similar program in windows before i switched.  what i'm wondering tho is...

1. is there any way to change the speed of the dock (when a new window opens it slides a little bigger and adds the icon)
2. can i make the icons NOT blurry somehow?  (only some of them are, but the ones that are annoy the heck out of me)
3. can i make it load the icons quicker?  (at the moment it takes about five seconds of staring at a blank space before an icon becomes visable, sometimes it doesn't come up at all.)

any and all help is appreciated!  :D

---

### Post by jargoman on 2007-05-04
just curius how did you install avant.

I have an amd processor. I'm at the moment trying to compile it from source but am having dependency problems. Is there an easier way

---

### Post by locke.dragon on 2007-05-04
all i did was follow these instructions...

[http://ubuntuforums.org/showthread.php?p=2093300](http://ubuntuforums.org/showthread.php?p=2093300)

(installed all repos needed and then did option 2).  i hit a snag when it told me to use "make," but i just restarted x and then did a search with led me to find a bit of code that finished up the install.  i'll let you know if i can find that code again.

---

### Post by locke.dragon on 2007-05-04
found that bit of code.

```

gconftool-2 --install-schema-file=/etc/gconf/schemas/avant-window-navigator.schemas

```
or
```

gconftool-2 --install-schema-file=/usr/etc/gconf/schemas/avant-window-navigator.schemas

```

hope that helps!  :D

---

### Post by jargoman on 2007-05-04
thanks for pointing me in the right direction as that is exactly what I'm trying to do but on my own.

---

### Post by locke.dragon on 2007-05-04
you're quite welcome!  :D

---


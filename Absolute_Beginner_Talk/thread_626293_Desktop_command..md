---
title: "Desktop command."
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by Law506 on 2007-11-28
I have asked this once before and got an answer... but I have lost that answer along with what post it was in.

I am just trying to get the command to enter that allows me to select what is on the desktop.  The place where you can unselect showing the mounted drives and just show nothing or My Computer and Network... 

If anyone knows this I would appreciate it.

-Thanks.

---

### Post by jordanmthomas on 2007-11-28
I'm not sure if this is what you did last time, but it will work.
```
gconf-editor /apps/nautilus/desktop
```

Then, (un)check what you want / don't want.

---

### Post by Hospadar on 2007-11-28
open a file browser (nautilus) it's in those preferences

---

### Post by jordanmthomas on 2007-11-28
> **Hospadar said:**
> open a file browser (nautilus) it's in those preferences
I couldn't find them there.  Is it an obvious option?

---

### Post by Law506 on 2007-11-28
dude, this is freaky.

This is going to the Jordan reply, my ex-wife's name was Jordan Thomas... crazy.

---

### Post by jordanmthomas on 2007-11-28
I promise you I was not her.
:lolflag:

---

### Post by dpar on 2007-11-29
As jordanmthomas said, in terminal type > gconf-editor
Then browse to apps>nautilus>desktop

---


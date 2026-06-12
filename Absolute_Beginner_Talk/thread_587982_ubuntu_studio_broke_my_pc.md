---
title: "ubuntu studio broke my pc"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by discmaster on 2007-10-23
I installed ubuntu studio last evening, thought all went well; Shut down pc, restarted this morning, pc won't boot. Instead, I get "Failed to start the X server" (your graphical interface) Looks like a problem with my nvidia video card. What do I need to do to get this pc operating again?
:confused:

---

### Post by skymera on 2007-10-23
right ok
when it fails go to the TTY (ctrl+alt+2) etc

then tyep

```
 sudo dpkg-reconfigure -phigh xserver-xorg 
```

dont wrry, this has happened to me LOADS of times :lol:

---

### Post by realvz on 2007-10-23
try sudo dpkg-reconfigure xserver-xorg

---

### Post by discmaster on 2007-10-23
>  sudo dpkg-reconfigure -phigh xserver-xorgok, did that. gives me a message about the backup file in etc/x11 ,etc location & I a desktop~$prompt. Where do I go from here?

---

### Post by discmaster on 2007-10-23
Disregard - I got it working - don't have a clue how... :confused:

---

### Post by justinmiller87 on 2007-10-23
> **discmaster said:**
> Disregard - I got it working - don't have a clue how... :confused:
I love it when that happens, sort of. It works, but darn it if I don't know why. That's why I switched to Linux - so I can figure out why it works.

---


---
title: "Compiz annoying game transparency"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by FuzZy2006 on 2006-07-31
I have Compiz/XGL installed and games became transparent. It is really annoying :(. How can I deactivate this?

---

### Post by mcduck on 2006-07-31
Start the game from a terminal like this: 

XLIB_SKIP_ARGB_VISUALS=1 <application name>

..or modify the laucher for your game to use this command.

---

### Post by _simon_ on 2006-07-31
This works for me:

[http://www.ubuntuforums.org/showthread.php?t=176636&highlight=XGl+opengl+games](http://www.ubuntuforums.org/showthread.php?t=176636&highlight=XGl+opengl+games)

---


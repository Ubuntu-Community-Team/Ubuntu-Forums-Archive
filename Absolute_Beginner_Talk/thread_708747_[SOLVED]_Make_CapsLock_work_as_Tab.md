---
title: "[SOLVED] Make CapsLock work as Tab?"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by ralphz on 2008-02-26
Is it possible? 

If yes how?

Ralph

---

### Post by ralphz on 2008-02-26
Answer:

[http://www.math.umn.edu/~aoleg/hacks.shtml](http://www.math.umn.edu/~aoleg/hacks.shtml)

Sorry

---

### Post by Origin415 on 2008-02-26
Its possible, try creating a file in gedit and put in
```
remove Lock = Caps_Lock
keycode 0x42 = Tab
```

and save it as .xmodmap in your home directory

now run the command
```
xmodmap .xmodmap
```

---


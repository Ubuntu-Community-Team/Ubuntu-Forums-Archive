---
title: "hotkey sudo?"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by tsanoff on 2007-03-07
I know it sounds stupid, but is there a way I can assign a keyboard key that can act as a sudo? Meaning, when i hold the key and i open an application it runs it as root. It may come in pretty handy with airsnort and other programs that i need to run as root. I know i can just do it from the terminal but it gets anoyng having to do it so often and have both, terminal and applicatin window, running.

---

### Post by fusiachi on 2007-03-07
Well, I'm not so sure on assigning a key to such a function, but if you create/edit the launchers for any program, there is a field for "command"--change it to the appropriate command, and you should be set.

I think that being able to assign a key as described might not be the most secure "feature" in the world.  I'd hate to have people accidentally hose their system.

---

### Post by jordanmthomas on 2007-03-07
It'd probably be best to just run the program as 
```
gksudo airsnort
``` instead of just ```
airsnort
```

(just adding to what fusicahi already said, in case you didn't know about gksudo)

---

### Post by 23meg on 2007-03-07
If you're used to drag and drop, you may find  [this trick]("http://www.ubuntuforums.org/showthread.php?t=24008") useful as well.

---


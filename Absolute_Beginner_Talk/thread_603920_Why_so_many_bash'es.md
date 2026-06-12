---
title: "Why so many bash'es?"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by Phristen on 2007-11-05
Why are there like 6 bash processes already running in Ubuntu when I log in?

---

### Post by trak87 on 2007-11-05
I just tested it at a terminal using "ps aux | grep bash" and I only see one bash instance, the one I'm using for the test. Perhaps you have other bash terminals open in another desktop or other terminal tabs are open in the same window?

---

### Post by Phristen on 2007-11-05
And this is what I have (there's only one terminal window actually running):```
ubuntu    7279  0.0  0.3  20648  3544 tty4     S+   22:19   0:00 -bash
ubuntu    7283  0.0  0.3  20652  3544 tty5     S+   22:19   0:00 -bash
ubuntu    7294  0.0  0.3  20652  3548 tty1     S+   22:19   0:00 -bash
ubuntu    7298  0.0  0.3  20648  3544 tty6     S+   22:19   0:00 -bash
ubuntu    7299  0.0  0.3  20648  3540 tty2     S+   22:19   0:00 -bash
ubuntu    7301  0.0  0.3  20652  3548 tty3     S+   22:19   0:00 -bash
ubuntu    9041  0.0  0.3  20524  3424 pts/0    Ss   22:22   0:00 bash
ubuntu    9148  0.0  0.0   5120   808 pts/0    R+   22:27   0:00 grep bash

```Oh, and I'm using a liveCD right now, maybe that's why?

---

### Post by trak87 on 2007-11-05
The PID 9041 is the one you've got open. I'm not sure what the -bash means. The dash is unknown to me. There's probably a way to find out more about the other PID's but I don't know the method.

---

### Post by trak87 on 2007-11-07
It's probably because you are using the Live CD. Something is running in each of the terminal windows. You can access each window with Ctrl-Alt-F1, Ctrl-Alt-F2, etc. to see what's in each terminal. Use Alt-F7 to return to GUI mode.

---

### Post by argie on 2007-11-07
> **trak87 said:**
> It's probably because you are using the Live CD. Something is running in each of the terminal windows. You can access each window with Ctrl-Alt-F1, Ctrl-Alt-F2, etc. to see what's in each terminal. Use Alt-F7 to return to GUI mode.

Yeah, that seems like it. I have only the one running. And when I open one of those terminal emulators (Ctrl-Alt-F1), and login and check, I then have one more on tty1.

---


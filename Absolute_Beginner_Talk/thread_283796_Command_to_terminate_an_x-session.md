---
title: "Command to terminate an x-session?"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by pbaehr on 2006-10-24
A while back I was having difficulty running my 3d games while compiz/Xgl was running. Somewhere along the lines someone gave me a command which starts a new x-session for the game to run in. The command is:
```

X :1 -ac & DISPLAY=:1 [name of game]

```

This works great. My only complaint is that after I exit the game I am left on an empty X Windows desktop and need to press ctrl+alt+backspace to kill it.

Is there a command I could add to my script at the end to kill the X session?

Thanks in advance!

---

### Post by TitusDalwards on 2006-10-24
You can kill X by opening a terminal, using `su` to switch to root, and then typing `killall X`.

---

### Post by pbaehr on 2006-10-24
But I only want to kill the one specific X session. Not my normal one.

---

### Post by netimen on 2007-09-27
> **TitusDalwards said:**
> You can kill X by opening a terminal, using `su` to switch to root, and then typing `killall X`.

But I get "X: no processes killed".

---


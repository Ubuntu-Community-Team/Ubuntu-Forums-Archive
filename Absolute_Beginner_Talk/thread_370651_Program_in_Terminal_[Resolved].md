---
title: "Program in Terminal [Resolved]"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by Ek0nomik on 2007-02-26
I know for a fact this has been asked before, but for some reason I can't find it anywhere.  When I run a program like gAIM from the terminal, simply by typing gaim, it opens just fine.  However, I can't use the terminal anymore, because it's occupied by gAIM.  When I close gAIM, than the Terminal also closes.

I know that I can add something onto my command of "gaim" so that I can continue using the terminal, I just don't remember what it is.

Any help would be appreciated!

Thanks!

---

### Post by nanotube on 2007-02-26
append '&' to the commandline to background it. so you'd run, for example,
```
gaim &
```

---

### Post by aysiu on 2007-02-26
```
gaim &
```

---

### Post by nanotube on 2007-02-26
> **aysiu said:**
> ```
gaim &
```

heh heh, looks like i beat you by a hair ;)

---

### Post by 23meg on 2007-02-26
Another way to start a program by typing its name without keeping a terminal busy is the "Run Application" dialog (Alt + F2 by default).

---

### Post by Ek0nomik on 2007-02-26
Thanks!

---

### Post by Patrick K on 2007-02-26
You can also open another terminal window. AFAIK, there is no limit on the number of terminals that can be open.

---

### Post by 23meg on 2007-02-26
> **Patrick K said:**
> You can also open another terminal window.

Or a new tab in the same gnome-terminal window (Ctrl + Shift + T). Having multiple tabs and launching an app in each comes in handy when testing, to track error output from multiple apps.

---


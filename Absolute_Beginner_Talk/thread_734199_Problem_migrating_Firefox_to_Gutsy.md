---
title: "Problem migrating Firefox to Gutsy"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by ahurd on 2008-03-24
I have just installed Gutsy after Feisty fouled up. I kept a copy of my FF .mozilla directory and inserted it into my Gutsy home page. When I tried to start FF using Kmenu, it said FF was already running ("firefox is already running but is not responding). I deleted .parentlock and lock files with no luck via kmenu. I then tried sudo firefox in terminal and by some miracle it worked perfectly. Could anyone tell me how to get it to work via kmenu or panel?

---

### Post by herbster on 2008-03-24
This is most likely that an instance of FF was running, you just have to kill it.

```
kill 9 firefox-bin
```

Will work in ALT+F2 or a terminal.

---

### Post by ahurd on 2008-03-24
Done all that (kill). No FF running via ps aux. What now?

---

### Post by herbster on 2008-03-24
Now do you still get the same "firefox is already running" error when clicking on it in the menu?

---

### Post by ahurd on 2008-03-24
Yes!

---

### Post by herbster on 2008-03-24
Reboot, try it again.

---

### Post by ahurd on 2008-03-24
Did that, Also uninstalled and reinstalled FF. Same problem again.

---

### Post by herbster on 2008-03-24
Try moving your ~/.mozilla directory out to your Desktop or somewhere temporarily, then restart FF.

---


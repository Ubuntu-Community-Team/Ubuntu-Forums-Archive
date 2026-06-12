---
title: "Program won't close"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by kensmith on 2007-01-17
I was running Mplayer and the network went down. After it came back up I tried to stop the mplayer but it will not close. It is not playing and I can move it to another workspace but it still will jot quit. I am only asking this question in case others do the same thing.

---

### Post by taurus on 2007-01-17
See what PID (first column) for mplayer and kill it with the kill command from a terminal.

```
ps -A
sudo kill -9 **PID**
```

---

### Post by kensmith on 2007-01-17
Thanks, I had 3 running and that did it.

---


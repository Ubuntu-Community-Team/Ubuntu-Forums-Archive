---
title: "[SOLVED] Turn off monitor: Bash script or keyboard shorcut?"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by jjsonp on 2008-03-07
The power switch on my monitor is broken - always on.

I would like to know how to turn off the monitor at will with a short script or keystroke. It powers itself down based upon my power settings, and I can set it for like 3 minutes, but then I have to 'wake up' my screen constantly.

Thanks.

---

### Post by herbster on 2008-03-07
```
xset dpms force off
```

Pop 'er in a script, make a launcher or whatever you like and giddy up.

---

### Post by jjsonp on 2008-03-08
That works perfectly! Thanks.

---


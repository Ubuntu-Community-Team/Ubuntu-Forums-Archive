---
title: "SOunds crackly"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by ghoran on 2008-02-09
My sound is very cracky. Can someone help? What information do you need?

---

### Post by spiderbatdad on 2008-02-09
maybe start by posting ```
asoundconf list
```

---

### Post by smothpocket on 2008-02-09
This happened to me when I upgraded to the 2.6.24 kernel

All i did to fix it was opened the gnome volume control settings by right clicking on the volume control and moved the PCM settings down to about half.

My speakers still were at normal loudness but the crackly sound went away.

Hope this helps!! :D

---

### Post by mmb1 on 2008-02-09
You might also want to post the output from "alsamixer" in the terminal

---

### Post by ghoran on 2008-02-12
Thanks. I hope this helps. I also attached a screen shot of alsamixer

gary@gary-desktop:~$ asoundconf list
Names of available sound cards:
V8235
gary@gary-desktop:~$

---


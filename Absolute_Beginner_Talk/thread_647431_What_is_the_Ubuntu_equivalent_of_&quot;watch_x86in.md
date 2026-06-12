---
title: "What is the Ubuntu equivalent of &quot;watch x86info -mhz&quot;"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by komputes on 2007-12-22
I would like to monitor my CPU speed from the shell. Is there an equivalent for the "watch x86info -mhz" command in the Debian Family of Linux?

8-[ Faster...CPU....don't...blow...up.

---

### Post by spiderbatdad on 2007-12-22
```
top
```

works for what you want, i believe

see: ```
man top
``` for more info

---

### Post by fastTalker on 2007-12-22
```
watch x86info -mhz
```
should still work.

---

### Post by komputes on 2007-12-22
@spiderbatdad: top gives me CPU %, not specific current speed in Khz/Mhz

@ fastTalker: this is what I get from the "watch x86info -mhz" command:
```
                                s
h: x86info: not found
                             
```

Even when run under the SuperUser.

---

### Post by tgalati4 on 2007-12-22
>sudo apt-get install x86info

Then run your command.  However it only posts the stated processor speed for me:  2.8 GHz not the overclocked speed that I am running (2.94 GHz).

Edit:  Seems to be working now, displays 2.95 GHz (estimate).  The program needs to create some device files to place the info so give it some time before executing.

---

### Post by jken146 on 2007-12-22
Is x86info installed?  It isn't by default.

---


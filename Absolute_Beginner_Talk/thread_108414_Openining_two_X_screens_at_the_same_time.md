---
title: "Openining two X screens at the same time?"
date: 2005-12-26
forum: Absolute Beginner Talk
---

### Post by harisund on 2005-12-26
Hi everyone.. 

I am trying to start two X sessions at the same time. One using root at terminal 7 (accessible by pressing Alt + F7) where I do administrative stuff, and the other at terminal 8 where I do regular stuff.. when I do startx for the second time, it says X server already running. How do I do that? 

Thanks !

---

### Post by steve.horsley on 2005-12-26
I know you can start a second X session on terminal 8 from a console login with the command: ```
startx -- :2
``` I don't know how you might automate the process though.

---

### Post by harisund on 2005-12-26
Hey thanks.. that worked.. and I am not really keen on the automation part.. startx -- :2 is great.. thanks !

---


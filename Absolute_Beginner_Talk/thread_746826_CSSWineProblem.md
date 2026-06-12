---
title: "CSS/Wine/Problem"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by sirfonners on 2008-04-05
Alright so I got everything to work for the first time
and CSS was opened and running, but I went to option to switch the game to 1240x768
and then after I applied it, it immediately closed and this popped up


"failed to lock vertex buffer in Cmeshdx8::LockVertexBuffer"

Is there a way I can fix this, or make CSS open without the 1240x768 option??

---

### Post by buried on 2008-04-05
try running this in the terminal
"wine (directory of where your CSS is) -800x600"
or
"wine (directory of where your CSS is) -opengl"
Or go to WineCFG and set a resolution in there manually.

---


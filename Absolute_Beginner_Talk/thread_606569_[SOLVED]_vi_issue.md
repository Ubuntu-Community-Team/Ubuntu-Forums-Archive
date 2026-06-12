---
title: "[SOLVED] vi issue"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by aspen_dv on 2007-11-08
Something weird with vi editor in 7.04 and even on my desktop with 7.10 Ubuntu
vi editor does not work right. Pressing i does not change to Insert mode. Even the arrow keys not working right (just output characters instead). I google this and someone mention to reinstall vi. I will do that if it solves but out of curiosity, can anyone give an explain or other solution to this?
Thanks.
p/s: DON'T tell me to use pico, emac or gedit. I just like vi.

---

### Post by mali2297 on 2007-11-08
Which terminal do you use? Try to change its keyboard settings. 
..or try another terminal (like xterm).

Is it only vi that doesn't respond correctly to the arrow keys?

---

### Post by eldragon on 2007-11-08
vi is old, i had this kind of problems, especially with different language settings on my ubuntu box.

sudo apt-get install vim

vim is vi-IMproved :D

fixes issues. and works just like vi

---

### Post by taurus on 2007-11-08
You need the vim-full package.

```
sudo apt-get update
sudo apt-get install vim-full
```

---

### Post by aspen_dv on 2007-11-08
Thank taurus, vim-full seems to address the issue.

---


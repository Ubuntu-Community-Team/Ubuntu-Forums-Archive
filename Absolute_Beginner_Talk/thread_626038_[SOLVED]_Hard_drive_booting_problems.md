---
title: "[SOLVED] Hard drive booting problems"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by natman on 2007-11-28
I installed 7.10 on a pc and it worked perfect, i then wanted to use a second pc ( which has no cd drive ) so unpluged the hard drive and swaped it into the second computer. Now when i boot i get the little progress bar and then a black screen with
"running boot scripts"
the screen flashes and then it just stalls. I put another windows hard drive into the computer and it booted no problem.

Any help?

---

### Post by Dr Small on 2007-11-28
It is taking you to Virtual Terminal 8, the startup listing terminal.
You will need to press ALT + F1, and it should take you to a terminal where you can login.

Login and reconfigure X (since you installed it on another system, you will need to reconfigure X for this display):
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by natman on 2007-11-28
Wow that worked perfect, thank you very much and i actually think i understood how i was fixing it .
Thanks

---

### Post by Dr Small on 2007-11-28
it's always good to understand how you are fixing something :D

Glad to help.

Please mark this thread as Solved from Thread Tools :)


Dr Small

---


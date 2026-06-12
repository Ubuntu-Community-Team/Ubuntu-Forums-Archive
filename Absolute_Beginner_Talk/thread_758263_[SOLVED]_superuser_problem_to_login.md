---
title: "[SOLVED] superuser problem to login"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by bengar on 2008-04-17
Hi everybody
I have had a power failure a few hours ago, after that I power up the PC and the screen resolution change. Is like it lost the video driver. I tried with su but the following error was showed in the terminal.

> bengar@bengar-desktop:~$ su
Password: 
su: Authentication failure
bengar@bengar-desktop:~$

I did use the normal password to login as a root, Is that the right way to login? I make a sudo man and I followed the instruction and still with the same log in problem. Any help will be appreciated

---

### Post by spiderbatdad on 2008-04-17
use: ```
sudo -i
```

---

### Post by bengar on 2008-04-17
> **spiderbatdad said:**
> use: ```
sudo -i
```

Thanks, it works

---


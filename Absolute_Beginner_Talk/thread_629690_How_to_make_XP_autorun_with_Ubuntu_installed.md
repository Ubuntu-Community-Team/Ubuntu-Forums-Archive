---
title: "How to make XP autorun with Ubuntu installed?"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by Marbash on 2007-12-02
After I installed Ubuntu I get a choice when I turn on my comp. Either I have to choose a operatingsystem in ten seconds, or else the highlighted one will start. When I turn on my comp. it's always Ubuntu that is highlighted. My question is: How can I make my comp. highlight XP first?

---

### Post by Dr Small on 2007-12-02
Bootup in Ubuntu, edit /boot/grub/menu.lst:
```
sudo nano /boot/grub/menu.lst
```

Find "default 0"
and replace it with whatever "title" number XP is.

Example, go down to the bottom, and count the "title" entries until you get to XP. That will be XP's "title" number.

Save the file:
CTRL + O
And exit:
CTRL + X

Reboot and try it.

---

### Post by Marbash on 2007-12-02
Thank you very much. :)

---

### Post by Dr Small on 2007-12-02
No problem. Glad I could help :D
Please mark your thread as Solved from Thread Tools, if it worked successfuly ;)

Dr Small

---


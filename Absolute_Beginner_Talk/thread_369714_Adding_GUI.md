---
title: "Adding GUI"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by Hamm on 2007-02-24
I just installed Ubuntu server 6.10 with no GUI. I want to add Fluxbox as my GUI desktop. How can add it from command line?

Hamm

---

### Post by taurus on 2007-02-24
```
sudo aptitude update
sudo aptitude install fluxbox
```

---

### Post by zeroblitzt on 2007-02-24
Edit: Taurus just beat me to it, and his is better.

---

### Post by Gerard Barberi on 2007-02-24
sudo aptitude install fluxbox

Make sure you have the Universe repository enabled.

sudo nano /etc/apt/sources.list

and uncomment them.

EDIT: Too late as well

---


---
title: "gusty server cant instal ubuntu-desktop"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by tny5357 on 2007-10-19
ok so i just did a fresh install of the new gusty server after the installation finished i tried installing the ubuntu-desktop by running the command
sudo apt-get install ubuntu-desktop
but it tells me it cant find the package ubuntu-desktop

help please

---

### Post by por100pre1 on 2007-10-19
```
cat /etc/apt/sources.list
```

post the results... :-k

EDIT: Just in case I'm not around:

```
sudo nano -w /etc/apt/sources.list
```

and remove the # before repository lines.

---


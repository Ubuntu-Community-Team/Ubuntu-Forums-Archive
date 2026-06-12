---
title: "unable to sudo make install"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by Hranj on 2006-08-23
im trying to install festival from a package that i downloaded. but when i go into the terminal and CD the the extracted directory and do a sudo make install the terminal comes up with this...
```
sudo: make: command not found
```
what can i do to fix this. its been driving me nuts for hours.

---

### Post by aysiu on 2006-08-23
```
sudo aptitude update && sudo aptitude install build-essential
``` Then try again.

---

### Post by halitech on 2006-08-23
have you install build-essentials?

in a terminal, type

sudo apt-get install build-essential

and that should get everything you need to install what you are trying to do

---

### Post by Qrk on 2006-08-23
You need to install a compiler before you can make. Ubuntu keeps all of the stuff you need in a nifty metapackage named build-essential

```
sudo apt-get install build-essential
```

---


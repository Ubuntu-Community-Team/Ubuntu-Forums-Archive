---
title: "I really just broke my ubuntu.. please help."
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by Vasant56 on 2006-12-04
It all started when I tried to install Beryn, anyways it messed up a little and when I tried to undo what i did i think i broke my xorg.. when i login my graphics are allk messed up and i can barely see what im doing. I really don't know what i messed up.

I tried this command but it didn't work:
> sudo aptitude install ubuntu-desktop

i can just reset to what it was like?

---

### Post by bodhi.zazen on 2006-12-04
Heck, you call that broken :(

I've done better then that :p

I do not know if it will help,

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Vasant56 on 2006-12-04
No luck =(

Anything else?

---

### Post by bodhi.zazen on 2006-12-04
Do you have a backup of xorg.conf ?

Can you post ;your current xorg.conf ?

---

### Post by Vasant56 on 2006-12-04
I DO have a backup.. thank god. Thanks for the help, everything seems to be working now

---


---
title: "Compiz fusion, apple keyboard and mouse"
date: 2007-07-20
forum: Apple Intel Users
---

### Post by bimo on 2007-07-20
Hi i just installed ubuntu studio
and currently using apple wireless keyboard and mouse
it works! 
but not quite perfect because
when i press and hold a key in the keyboard for example "w" or "F1"
the mouse didn't want to move 
and i have to release the keyboard first in order to move the mouse again
is there anything done with the compiz fusion??
thx

---

### Post by misfitpierce on 2007-07-20
Well if you need to you can change the hotkeys for each effect.

---

### Post by cyberdork33 on 2007-07-20
This is a bug. Please see:
[http://ubuntuforums.org/showthread.php?t=503721&highlight=hold+key+mouse+games](http://ubuntuforums.org/showthread.php?t=503721&highlight=hold+key+mouse+games)

```
sudo /etc/init.d/mouseemu stop
```

---

### Post by bimo on 2007-07-20
Wow i know that will work...
but i already did something else hehehe
sudo apt-get remove mouseemu
it works...
is there a bad effect if i remove the mouseemu??

---

### Post by cyberdork33 on 2007-07-20
Here is the description:
[http://packages.debian.org/unstable/utils/mouseemu](http://packages.debian.org/unstable/utils/mouseemu)

Personally, I think it is just an annoyance.

---


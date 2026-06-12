---
title: "sudo: gedit: command not found"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by aalr1986 on 2007-03-13
Hey guys, I need some help here:
I type this: "gksu gedit /etc/apt/sources.list"
and this is what I get:

sudo: gedit: command not found

what is wrong?

I'm using Xubuntu Dapper.

Thanks!

---

### Post by AndyCooll on 2007-03-13
Ubuntu uses "sudo" rather than "su"
You need to type:
```
gksudo gedit /etc/apt/sources.list
```

:cool:

---

### Post by aalr1986 on 2007-03-13
ok, I tried that
same thing happens.

Any ideas?

---

### Post by Billy McCann on 2007-03-13
Try

```
sudo nano /etc/apt/sources.list
```

Nano is different than gedit.  I'm changing both the "sudo" from "gksudo" and the "nano" from "gedit" just to see if trying something completely different will work.

Nano will open within the terminal.  You have to scroll with your direction buttons.  Close it with ctrl-X.  A prompt will come up (at the bottom of the terminal screen) asking if you want to save.  Of course you want to save.  All cool people save.

---

### Post by Tyr Norian on 2007-03-13
Does this work?
```
gksu /usr/bin/gedit /etc/apt/sources.list
```

---

### Post by aalr1986 on 2007-03-13
Yeah Man, It Worked!!!!!!!!

Thanks A Lot!!!!!

---

### Post by Tyr Norian on 2007-03-13
You're very welcome.

---

### Post by ardchoille42 on 2007-03-13
> **aalr1986 said:**
> Yeah Man, It Worked!!!!!!!!

Thanks A Lot!!!!!

In that case, you might want to check to see why your $PATH variable is messed up.

---


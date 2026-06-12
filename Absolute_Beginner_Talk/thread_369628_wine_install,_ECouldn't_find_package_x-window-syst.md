---
title: "wine install, E:Couldn't find package x-window-system-dev"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by clark0820 on 2007-02-24
Hi all,

           I'm trying to install wine on my Ubuntu Edgy, I try to do ./tools/wineinstall, but it tell me to "Install the X development headers and try again".  So, I do "apt-get install x-window-system-dev" and then the following msg come up saying: "E:Couldn't find package x-window-system-dev" I don't really know what I should do next.

           Please help. Thanks.

Clark

---

### Post by jordanmthomas on 2007-02-24
Wouldn't that package be:
```
xserver-xorg-dev
```
?

Also, wine is available precompiled if you'd rather go that way.

---

### Post by clark0820 on 2007-02-24
no, I did the "apt-get install xserver-xorg-dev"

but it still didn't work,

the msg  "Install the X development headers and try again" still appear when I try to do ./tools/wineinstall


beside fixing the problem,
what's the different between doing what I'm doing right now and getting the compiled version install??

Thanks

---

### Post by clark0820 on 2007-02-25
can anyone help on this?? cos I still couldn't fix it yet? I don't know why I can't "apt-get install" the "x-window-system-dev", I try "apt-get install x-window-system", it works, but it doesn't help the situation.

---

### Post by gangrelsurf on 2007-03-13
did you try xorg-dev? That is different that xserver-xorg-dev.

---

### Post by GEdWay Ingasia on 2007-11-06
This worked the new line  would be : 
__________________________________________________________________________________
apt-get install cvs build-essential bison flex-old libasound2-dev xorg-dev libpng12-dev libjpeg62-dev libfreetype6-dev libxrender-dev libttf2 libttf-dev msttcorefonts libfontconfig1-dev 
__________________________________________________________________________________
hope this helps :)

---

### Post by rudeboyskunk on 2007-11-06
Or you can just try:

```
$ sudo apt-get install wine
```

Make sure all of your repositories are enabled as well.

---


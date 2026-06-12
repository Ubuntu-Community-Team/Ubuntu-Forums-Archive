---
title: "Trying to install moblock, get error - &quot;Can't Open File To Write&quot;"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by ajskhan on 2007-07-12
ok

[http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/)

trying to follow this in noob terms :)
i go to home folder>>>filesystem>>> browse to etc/apt/sources.list or w/e

then at the bottom i try to add the two lines:
deb [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) unstable main
deb-src [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) unstable main

then it says in a pop-up "Can't open file to write"

er, i am stuck

pls help

---

### Post by Inxsible on 2007-07-12
You have to open the file as root to be able to modify anything.

try ```
gksudo gedit /etc/apt/sources.list
```

---

### Post by Inxsible on 2007-07-12
i just saw that you have Xubuntu ..so gedit might not work. I am not sure if gedit is installed in Xubuntu. Use your favorite editor.

you could also use vi or nano

---


---
title: "navigate to desktop"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by jtmedin on 2007-04-08
Downloaded adobe flash player & was told to start teminal & navigate to desktop. i have no idea how one navigates to desktop in 'terminal'. Starting terminal i can do but ... TIA

---

### Post by jondecker76 on 2007-04-08
from terminal ..

cd /home/your_user_name/Desktop

---

### Post by zvacet on 2007-04-09
```
cd Desktop
```

This page can be helpfull


[http://www.linux.org/lessons/]("http://www.linux.org/lessons/")

---

### Post by jtmedin on 2007-04-10
Ahhh i keep forgetting unix is case sensitive :-(. Thanks
Now the problem: i was told to navigate to desktop & type
# rpm -Uvh flash-plugin-9.0.31.0-release.i386.rpm then click enter
(this must be done as a root user)

I get no action when i try the above :-(.
tried 'sudo ls' to get to root user. No banana :-(

---

### Post by darrenm on 2007-04-10
Thats an RPM file, they don't work (by default) with Ubuntu.

You need a deb file or just install the flashplayer through add/remove at the bottom of the applications menu.

---


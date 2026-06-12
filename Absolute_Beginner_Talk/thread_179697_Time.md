---
title: "Time"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by olejlowens on 2006-05-20
I have a dual boot system. When returning to windows XP from Ubuntu the clock is five (5) hours fast and must be reset. Can this be corrected?

---

### Post by confused57 on 2006-05-20
Check out this thread:

[http://www.ubuntuforums.org/showthread.php?t=174390&highlight=clock](http://www.ubuntuforums.org/showthread.php?t=174390&highlight=clock)

---

### Post by stalefries on 2006-05-20
There's a certain setting that needs to be changed. By default, Linux systems are set to UTC time, and not your local time zone. 

To fix this, edit the 
```
/etc/default/rcS
```
file, changing the UTC line so it says
```
UTC=no
```.

This should fix it, although you may need to modify your time once more to set it to the proper time.

---

### Post by olejlowens on 2006-05-20
Thanks- Changing UTC=yes to UTC=no corrected the problem.

---


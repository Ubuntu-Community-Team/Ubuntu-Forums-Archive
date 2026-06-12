---
title: "no graphical logon, kde help please"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by hungrybuddha on 2007-02-10
I can only log onto x by that scary black screen.

I was trying to follow some of the guides that allow the microsoft intellimouse in KDE. In particular, I was using the following guide:

[http://ketsugi.com/panegyrist/howto-intellimouse-explorer-with-ubuntu-dapper/](http://ketsugi.com/panegyrist/howto-intellimouse-explorer-with-ubuntu-dapper/)

after I configured the imwheelrc file, i restarted X and it went kaboom. No more graphical interface. AND..

getting up to leave the room to calm down my frustrations, i bumped my desk with my toe! :mad: 

help anyone? i think my toe will be fine....

---

### Post by tbroderick on 2007-02-10
Did you change;
```
 Option "Device "/dev/input/xxx"
```

My guess is it's wrong. Cause that would cause X to fail.

---

### Post by hungrybuddha on 2007-02-10
> **tbroderick said:**
> Did you change;
```
 Option "Device "/dev/input/xxx"
```

My guess is it's wrong. Cause that would cause X to fail.

negative. i reverted back to the original input/mice and still didnt give.

---

### Post by tbroderick on 2007-02-10
Do you have a backup of your xorg.conf? You should also check the log file in /var/log.

---


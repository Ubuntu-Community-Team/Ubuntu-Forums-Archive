---
title: "where is rc3.d,????"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by huggy77 on 2006-08-14
just wondering where to find the directories to put my symlinks to start up and shut down...


thanks!

---

### Post by reacocard on 2006-08-14
in /etc/rc3.d i believe.

---

### Post by stanz on 2006-08-14
Most link from the *'/etc/init.d'* folder.
Are you not wanting *rc2.d* or *rcS.d* ? ~ Not saying, ya don't know what`cha doing...
It prob be me - that may learn something !  ;)

---

### Post by steve.horsley on 2006-08-14
Stanz is right. Ubunti defaults to runlevel 2, which means you probably want to put you service start script in there. And it is convention to put the script in /etc/init.d and put a symlink to that in the /etc/rc2.d directory. e.g.
/etc/rc2.d/S99myservice -> /etc/init.d/myservice

---

### Post by huggy77 on 2006-08-15
you guys are right - i had a brain lock.

---

### Post by stanz on 2006-08-18
You to !? ...I thought I just got that!  ;)

---


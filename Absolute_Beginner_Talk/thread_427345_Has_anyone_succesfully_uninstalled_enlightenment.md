---
title: "Has anyone succesfully uninstalled enlightenment?"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by riminicat on 2007-04-29
I tried the normal command line codes and it just goes nuts and logs me out, then when I log back in enlightenment is back on

---

### Post by Kobalt on 2007-04-29
With which command line did you try to uninstall it ? Simply this : ```
sudo aptitude remove e17
```?

Did you select another session from the Options menu at login screen (then you can run aptitude again and search and remove orphaned packages of e17) ?

---

### Post by riminicat on 2007-04-29
I have no choices under the sessions option at the login screen, sudo aptitude remove e17 says there is no such thing

---

### Post by riminicat on 2007-04-29
I found the problem!!  The log in window I had on couldn't access my sessions for some reason, I just switched windows!!

---


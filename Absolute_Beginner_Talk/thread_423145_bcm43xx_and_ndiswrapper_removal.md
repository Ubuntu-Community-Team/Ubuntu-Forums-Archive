---
title: "bcm43xx and ndiswrapper removal"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by tcebak on 2007-04-25
hey, i've been having tons of problems. i had my bcm43xx wirless card wroking fine. then i can connect for two days. getting angry. i removed all my bcm43xx packages and i want to remove ndiswrapper so that i basically start over again fixing it.  the problem is it never connect to a network. thanks

---

### Post by Bachstelze on 2007-04-25
```
sudo apt-get remove ndiswrapper*
```

should do the trick, rememeber to also remove ndiswrapper from /etc/modules if you added it to it.

---


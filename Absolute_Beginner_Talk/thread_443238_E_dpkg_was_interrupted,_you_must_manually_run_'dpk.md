---
title: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the p"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by locustfist on 2007-05-14
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

what does this mean?
Ubuntu won't let me install any apps

---

### Post by taurus on 2007-05-14
It means that there is a broken package.  Open a terminal and do

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo aptitude clean
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by doobit on 2007-05-14
> **locustfist said:**
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

what does this mean?
Ubuntu won't let me install any apps

That means open a terminal type ```
su dpkg --configure -a
``` Then follow the instructions.


Apparently you stopped an installation in the middle of a process and dpkg needs to reconfigure.

<edit> Follow Taurus's advice since it's more complete.

---

### Post by locustfist on 2007-05-15
I did this, and now when i select an app in the add/remove to install it just hangs
> Errors were encountered while processing:
 sun-java6-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
e

---

### Post by Kemical on 2007-05-22
I am having the same issue, any resoloution?

---

### Post by keka on 2007-05-22
Thanks a lot! it worked for me!

---

### Post by BlueTree on 2007-05-24
I am having a similar problem, and when I run 'sudo dpkg --configure -a', I get an EULA with no option to enter more commands... what do I do?

---


---
title: "problem in installing programs"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by phanipalagummi on 2008-03-04
when i m trying to install programs from synaptic package manager
or add/re prog
i m getting this error
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
please  help

---

### Post by Joeb454 on 2008-03-04
umm...did you try running the command it tells you...I know it sounds a bit stupid.

Open up a terminal (Applications>Accessories>Terminal) and then type ```
sudo dpkg --configure -a
```

It will ask for your user password, though be aware that it won't show that you are typing anything :)

---


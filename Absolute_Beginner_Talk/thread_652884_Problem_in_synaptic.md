---
title: "Problem in synaptic"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by ronb94 on 2007-12-29
hello
i have problem in ubuntu gusty. i cant open synaptic or install something(includes updates) or even run in terminal sudo apt-get update.
i am getting this messege:
[IMG]http://img411.imageshack.us/img411/12/screenshotsynapticuj4.png[/IMG]

---

### Post by SOULRiDER on 2007-12-29
Reboot, if you still get the error try this in a terminal
```
sudo fuser -vki /var/lib/dpkg/lock;sudo dpkg --configure -a
```

---


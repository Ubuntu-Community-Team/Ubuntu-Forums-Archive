---
title: "Permissions issue"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by Robotuner on 2007-02-03
Hi;

I am trying to install the 855resolution package to adjust my monitors resolution.  Part of the instructions is to execute the following commands

make
su
make install

when I issue the su command, it asks for a password.  When I enter the password, I am told that there is an authentication failure.  What gives? I can get admin access everywhere else on the machine using the same password.

Thanks

---

### Post by taurus on 2007-02-03
```
./configure
make
**sudo** make install
```

---


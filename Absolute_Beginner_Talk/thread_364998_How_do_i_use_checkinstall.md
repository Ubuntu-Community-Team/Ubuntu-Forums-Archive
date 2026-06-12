---
title: "How do i use checkinstall???"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by islander_810 on 2007-02-19
K, i downloaded and installed checkinstall using apt-get, the super cow :) sry for the bad joke but it's too good

anyway, now how do i use it?

---

### Post by Maestro23 on 2007-02-19
> **islander_810 said:**
> K, i downloaded and installed checkinstall using apt-get, the super cow :) sry for the bad joke but it's too good

anyway, now how do i use it?

[http://asic-linux.com.mx/~izto/checkinstall/](http://asic-linux.com.mx/~izto/checkinstall/)

---

### Post by islander_810 on 2007-02-19
Thx for the excellent link but i faced a severe prob of info overload :( . 

Can u provide a starting pt in the form of default terminal commands? I'll expt with the options later once i'm comfortable

For eg, once i have the source, i do ./configure, make and make install
What deviations do i need to do in order to accomodate checkinstall?

---

### Post by tbroderick on 2007-02-19
You really should read the README, but basically you do checkinstall instead of make install.

---

### Post by nanotube on 2007-02-19
> **tbroderick said:**
> You really should read the README, but basically you do checkinstall instead of make install.

to clarify, you'd do
```

./configure
make
sudo checkinstall
```

key points: 
run checkinstall with sudo or it will fail
and do /not/ run 'make install'.

---


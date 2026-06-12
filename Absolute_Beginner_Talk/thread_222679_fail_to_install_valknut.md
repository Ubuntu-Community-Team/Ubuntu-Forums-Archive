---
title: "fail to install valknut"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by penguinKabuki on 2006-07-25
==========
root@root:~# sudo apt-get install Valknut
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package Valknut
==========

why this thing happen?

---

### Post by madmetal on 2006-07-25
give a try installing from synaptic

---

### Post by Kilz on 2006-07-25
> **penguinKabuki said:**
> ==========
root@root:~# sudo apt-get install Valknut
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package Valknut
==========

why this thing happen?

Because you used a capital V. Try this

```
sudo apt-get install valknut
```
Most if not all package names in apt are all lower case.
Valknut is my fav direct connect client for Linux. So I know it installs and works.

---


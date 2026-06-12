---
title: "Booting into ubuntu from OS X"
date: 2008-07-19
forum: Apple Hardware Users
---

### Post by Scientia on 2008-07-19
I just installed OS X into a G3 iBook previously running only ubuntu. I partitioned using the OS x install disc, then installed ubuntu. (I didnt install OS x first) Later, i installed OS X, then only i realized i didn't know how to boot back into ubuntu from os x. Apparently os x doesnt recognize the linux system.

Help, anybody?

---

### Post by ditsch on 2008-07-19
You will have to recover yaboot with the help of a live cd, chroot into your system, check you yaboot.conf and perform ```
sudo ybin
```.

---


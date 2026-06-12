---
title: "How to Uninstall"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by adi_das on 2008-02-18
How to Uninstall anything installed?

---

### Post by jken146 on 2008-02-18
```
sudo aptitude remove <package>
```

Or use Add/Remove... or Synaptic.

---

### Post by kpkeerthi on 2008-02-18
Open Synaptic (System -> Admin -> Synaptic), search for the package name/description and mark for uninstall.

---

### Post by LeAstrale on 2008-02-18
i would prefer using the apt-get command instead of aptitude because you cant use both, then theyll delete each others packages saying that they weren't needed.

if its installed through the repos you can from terminal/Konsole write sudo apt-get remove "name of the program"

---

### Post by oedha on 2008-02-18
if you really know the name.....terminal is the best
if you not sure.......add/remove program or synaptic
that's if i want to do like what you wanna do :)

---

### Post by kpkeerthi on 2008-02-18
> **astral-1 said:**
> i would prefer using the apt-get command instead of aptitude because **you cant use both, then theyll delete each others packages saying that they weren't needed**.

if its installed through the repos you can from terminal/Konsole write sudo apt-get remove "name of the program"
No... it is not true. You can **install** a package 'X' with apt-get and then remove the same with aptitude **safely**. 

Apart from the command-line switches both use, apt-get and aptitude differ from each other in the 'defaults'  they assume when you add or remove a package. So it is usually considered not advisable to mix and match apt-get and aptitude though they work perfectly normal in tandem.

---

### Post by lucasl on 2008-02-18
If you installed by building from source (./configure, make, make install), "sudo make uninstall" in the source directory normally does the trick.

---


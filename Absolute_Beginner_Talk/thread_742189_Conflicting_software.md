---
title: "Conflicting software?"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by Mr noodle on 2008-04-01
I tried to install Wine and some others from add/remove. The packages seem to download,but then an error pops up saying it can't be installed due to conflicting software.'

 How do find out what the conflicting software i so I can remove it? :confused:

---

### Post by forrestcupp on 2008-04-01
Try installing them from Synaptic and see if it gives you a better answer.  If not, you'll have to figure out exactly what the package names are and try it from the command line to get a better readout.

But Synaptic should give you more info than Add/Remove Programs.

---

### Post by zvacet on 2008-04-01
Or you can try to install from terminal

```
sudo apt-get install wine
```

If you get any errors post it here.

---

### Post by macanations on 2008-05-07
I just installed Ubuntu 8.04 64-bit and am having the same problem.  When I run sudo apt-get install wine I get the following error:

```
The following packages have unmet dependencies:
  wine: Depends: ia32-libs (>= 1.6) but it is not going to be installed
        Depends: lib32asound2 (> 1.0.14) but it is not going to be installed
        Depends: lib32nss-mdns (>= 0.10-3) but it is not going to be installed
        Depends: libc6-i386 (>= 2.6-1) but it is not going to be installed
E: Broken packages
```

I think it has to do with running the 64-bit version.  Any help would be greatly appreciated.

---


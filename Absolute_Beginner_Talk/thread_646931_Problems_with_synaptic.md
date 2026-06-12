---
title: "Problems with synaptic"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by Jeht on 2007-12-21
I'm having some pretty big problems with synaptic at the moment, when I run the update manager and select install updates an error message appears saying;

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

so I open the run application terminal and type in synaptic, synaptic then runs perfectly well.
I go to the updates mark them for upgrade and see that there is no install updates button in synaptic or anything similar,
I'm not sure how I can get these updates installed, I know it's a little dull but linux noob talking.
Maybe I should've stuck to windows, but I'm using ubuntu and I'm having problems can I please have some help if anyone wouldn't mind

---

### Post by wormser on 2007-12-21
Applications> Accessories> Terminal

```
sudo dpkg --configure -a
```

```
sudo apt-get update
```

---


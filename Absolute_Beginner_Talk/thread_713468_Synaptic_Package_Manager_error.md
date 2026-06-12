---
title: "Synaptic Package Manager error"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by thischarmingman on 2008-03-02
Hi 
Whenever I try to access synaptic package manager I get the following errors

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I've tried running dpkg in a terminal window but with no success. I'm completely stuck on this matter. Any suggestions? Much appreciated!

---

### Post by neurostu on 2008-03-02
did you type:
```

sudo dpkg --configure -a

```
Exactly?

---

### Post by JoshuaRL on 2008-03-02
So you've tried:
```

sudo dpkg --configure -a

```
right?

Have you tried:
```

sudo apt-get -f install

```

---

### Post by thischarmingman on 2008-03-02
Whoops, had a bit of a blond moment, forgot to include the sudo part of the code. Forgive me, I've only just come from the dark side of windows. Thanks for your help, both of you. You haven't seen the last of me!

---

### Post by JoshuaRL on 2008-03-02
How charming!

---


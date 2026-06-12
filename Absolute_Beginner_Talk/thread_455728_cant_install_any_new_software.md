---
title: "cant install any new software"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by chris8sirhc on 2007-05-26
every time i try to run the default os updater, install new software, or anything like that I get the same error msg:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

any ideas on what i can do to fix this?

---

### Post by aysiu on 2007-05-26
Paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo dpkg --configure -a
```

---

### Post by Happy_Man on 2007-05-26
You have run
```
sudo dpkg --configure -a
``` right?

EDIT: Darn, beat by a mod. Again. sigh.....

---

### Post by aysiu on 2007-05-26
It's not a race. It's totally cool. chris8sirhc is just getting double help.

---

### Post by chris8sirhc on 2007-05-26
cool, it worked, but it says i have one broken file and I need to use the broken filter to find it.  I know i keep asking newb questions but how to i find that program and use it?

---

### Post by aysiu on 2007-05-26
> **chris8sirhc said:**
> cool, it worked, but it says i have one broken file and I need to use the broken filter to find it.  I know i keep asking newb questions but how to i find that program and use it?
```
sudo apt-get -f install
``` should fix the broken package. If not, you can use System > Administration > Synaptic Package Manager to find broken packages.

---


---
title: "prolem with synaptic"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by Labren on 2007-12-31
I was installing vmware and the system froze up and quit responding. After rebooting the system and trying to restart synaptic i get the following error message..

..E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


I went into terminal and tried what it said but it didnt do anything and i am still unable to use synaptic as well as the add remove function as well.

I would really appreciate any help i can get with this problem.

I refuse to give up and go back to the dreaded winblows.

---

### Post by taurus on 2007-12-31
Close synaptic.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
**sudo** dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by icheyne on 2007-12-31
You have to run dpkg --configure -a as root.

Did you try sudo?

sudo dpkg --configure -a

---

### Post by Ub1476 on 2007-12-31
Did you run the command as root(admin)?

```
sudo dpkg --configure -a
```

> 
I refuse to give up and go back to the dreaded winblows. 

Very good:)

---

### Post by rockinlinux on 2007-12-31
i had that happen and i restarted x and it worked fine....might work for you.

---

### Post by Labren on 2007-12-31
Thanks Taurus for the help. it all seems to be working great now. again many thanx to you and the rest of y'all that offered help.

---


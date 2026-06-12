---
title: "problem with compizfuision and graphics"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by tototime on 2008-01-28
hello i am new to ubuntu and i need help i downloaded the restricted drivers for my ati x1400 graphics card and when i hit custom for compiz fusion to work it says the composite extension is not available.  How do i fix this problem?  Thanks.

---

### Post by erfahren on 2008-01-28
in the terminal do:
```

sudo apt-get install xserver-xgl

```
log out and back in and you should be able to enable them

---


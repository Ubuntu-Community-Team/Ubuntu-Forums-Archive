---
title: "Fsck died with exit code 1"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by nthpro on 2007-02-26
When my fsck runs it errors out and refuses to correct any errors.  Any suggestions on why this is doing it/ how to stop it from doing it?

---

### Post by taurus on 2007-02-26
Boot from the LiveCD and see if you can run the fsck from a terminal, assuming your Ubuntu is on /dev/hda1.

Applications -> Accessories -> Terminal
```
sudo fsck /dev/hda1
```

---


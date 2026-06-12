---
title: "[SOLVED] Getting back to the basic"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by wil313 on 2007-10-16
How do you get back to the just the basic programs that came preinstalled on ubuntu without completely re-installing?

---

### Post by wil313 on 2007-10-16
Please... Someone?

---

### Post by ubuntu27 on 2007-10-16
So basically, you onyl want the programs that comes by default when you do a fresh install?

You will have to delete unwanted applications one by one by either Synaptic or Terminal
```
sudo aptitude remove package-name
```


and install ubuntu-desktop which is a meta package that install all the basic applications that comes with UBuntu

```
sudo aptitude install ubuntu-desktop
```

---

### Post by wil313 on 2007-10-16
Thanks a lot man

---


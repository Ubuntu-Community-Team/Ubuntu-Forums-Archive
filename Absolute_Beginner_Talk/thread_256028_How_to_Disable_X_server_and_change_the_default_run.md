---
title: "How to Disable X server and change the default run level"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by D_frag on 2006-09-12
I need to install the nvidia graphics driver for the 64 bit architecture 
and in the manual i read i have to disable X server and set the default run level on my  system such that it will boot to a VGA console. I dunno how ?
any help

---

### Post by taurus on 2006-09-12
You don't have to install nvidia by hand.  You can do that with aptitude...

---

### Post by D_frag on 2006-09-12
how is that ?

---

### Post by Quasaur on 2007-04-02
Excuse me, folks...but I would still like to know how to change the default runlevel...?

---

### Post by zvacet on 2007-04-04
If you want to be single user than 
```
sudo init 1
```

for multiuser mode is be tween 2-5 so let say  

```
sudo init 4
```

---


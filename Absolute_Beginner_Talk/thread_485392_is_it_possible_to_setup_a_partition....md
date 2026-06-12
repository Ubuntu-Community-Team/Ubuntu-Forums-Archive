---
title: "is it possible to setup a partition..."
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by yui chan 18 on 2007-06-26
between ubuntu and ubuntu studio? from what i hear, they both have completely different applications. i'm happy with the regular feisty, but would i be able to setup a partition just in case? any input would be much appreciated.

---

### Post by canadianwriterman on 2007-06-26
You can use the gparted live CD to shrink your Ubuntu partition and create some empty space for Ubuntu Studio to install in. When installing Ubuntu Studio, you would just select the largest free space into which to install

---

### Post by yui chan 18 on 2007-06-26
and i'm guessing this is why the computer is not accepting the disc image of ubuntu studio upon startup?

---

### Post by Nekiruhs on 2007-06-26
> **yui chan 18 said:**
> between ubuntu and ubuntu studio? from what i hear, they both have completely different applications. i'm happy with the regular feisty, but would i be able to setup a partition just in case? any input would be much appreciated.
You don't really need to. You can just install the packages and then choose when you login. [Heres a guide]("http://www.ubustu.com/globe/2007/05/23/add-ubuntu-studio-to-an-existing-ubuntu-install/")

---

### Post by yui chan 18 on 2007-06-26
now i have a new problem...it won't install from the cd. what now?

---

### Post by yui chan 18 on 2007-06-27
ok...so what programs was it supposed to install?

---

### Post by cwood06 on 2007-06-27
if you got on the ubuntu studio site they have there repo there just install there repo then install thier software no need to set up a partition if you had to you can use gparted 

```
 sudo apt-get install gparted 
```

if you want there graphic programs just look at the packages itll install them all for you.

---


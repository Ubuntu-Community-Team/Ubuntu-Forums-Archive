---
title: "unresolved dependancy"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by PeterRedford on 2008-02-20
anytime I try to install anything either with synaptic package manager, I get an error saying unresolved dependency error.

is there anyway to force it to just install the dependencies

---

### Post by spiderbatdad on 2008-02-20
```
sudo dpkg --configure -a
```
or
```
sudo dpkg  --audit
```

---

### Post by PeterRedford on 2008-02-21
the problem still occurs even when i enter those codes in terminal. im absolutely  new to ubuntu and have no idea what this problem means. thanks

---

### Post by lespaul_rentals on 2008-02-21
```
sudo apt-get install -f
```

---

### Post by spiderbatdad on 2008-02-21
synaptic install the necessary dependencies for you. It is unlikely you would see that message unless trying to install a broken package.  deb packages also come with the necessary dependencies, and aptitude makes every effort to inform you of the name of any missing dependencies. So your statement, "anytime I try to install anything either with synaptic package manager, I get an error saying unresolved dependency error," doesn't seem accurate.

---

### Post by lespaul_rentals on 2008-02-21
> **spiderbatdad said:**
> synaptic install the necessary dependencies for you. It is unlikely you would see that message unless trying to install a broken package.  deb packages also come with the necessary dependencies, and aptitude makes every effort to inform you of the name of any missing dependencies. So your statement, "anytime I try to install anything either with synaptic package manager, I get an error saying unresolved dependency error," doesn't seem accurate.

Nah, I've seen it happen before.  What he's saying is true.  That's why I encourage people to use the command-line verson of APT, so they can see any helpful output.  Most of the time, you just have to run the following command to fix it:

```
sudo apt-get install -f
```

It should then fix it for you.

---


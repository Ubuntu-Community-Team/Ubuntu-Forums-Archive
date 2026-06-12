---
title: "Unable to update"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by novice1969 on 2008-03-04
I am unable to install updates because of the following message:
Any solutions?

---

### Post by taurus on 2008-03-04
Close that window.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by kellsens on 2008-03-04
Hi, Taurus !

   Doing this

```
sudo dpkg-reconfigure -a
```

 is too slow, because will reconfigure all your packages dependencies, try this first :

```
sudo dpkg-reconfigure -a -p high
```

maybe works and will be more faster.


P.S.: Sorry my english

---


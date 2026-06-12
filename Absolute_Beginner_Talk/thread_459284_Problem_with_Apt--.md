---
title: "Problem with Apt--"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by weapon-x on 2007-05-30
hi friends today i have install a fresh ubuntu 7.04 and i use aptoncd software to make the backup  of the all the previous apt downloaded by me, Now  i use the AptonCD on restore all the packages .
Now there is a problem that i want to install all of the at the same time or in one command not one by one because it will take a lot of time to install all of them.

Please help me solve this problem i m also attaching my package list ..

---

### Post by austin on 2007-05-30
I thought aptoncd lets you select the packages to restore from a list when you enter the cd ??? ...

---

### Post by zvacet on 2007-05-30
```
cd /var/cache/apt/archives
```

```
sudo dpkg -i *deb
```

If you have Java you can remove it from /var/cache/apt/archives because it can stop installation of other packages.This is because you need to agree with Java licence.When you install all packages put Java in /var/cache/apt/archives and install it with synaptic.Just an idea.

---

### Post by weapon-x on 2007-05-31
> **zvacet said:**
> ```
cd /var/cache/apt/archives
```

```
sudo dpkg -i *deb
```

If you have Java you can remove it from /var/cache/apt/archives because it can stop installation of other packages.This is because you need to agree with Java licence.When you install all packages put Java in /var/cache/apt/archives and install it with synaptic.Just an idea.



thanks dude its work man it helps me a lot............:p

---


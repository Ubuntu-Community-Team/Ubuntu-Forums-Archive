---
title: "trying to install firefox"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by PhantomX17 on 2008-03-02
I am trying to use apt-get to install firefox.  I have Kubuntu 7.10 gutsy.  When i use the shell i get this error:

phantomx@laptopX:~$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package firefox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package firefox has no installation candidate

If anybody could offer some advice or tell me what I'm doing wrong that would be great.

---

### Post by SOULRiDER on 2008-03-02
Try first doing a
```
sudo aptitude update
```
and finally
```
sudo aptitude install firefox
```

---

### Post by Oldsoldier2003 on 2008-03-02
> **PhantomX17 said:**
> I am trying to use apt-get to install firefox.  I have Kubuntu 7.10 gutsy.  When i use the shell i get this error:

phantomx@laptopX:~$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package firefox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package firefox has no installation candidate

If anybody could offer some advice or tell me what I'm doing wrong that would be great.

try updating your package listings:
```
sudo apt-get update
```
then see if trying to install gives you an error

---

### Post by PhantomX17 on 2008-03-02
that work great thanks so much.

---


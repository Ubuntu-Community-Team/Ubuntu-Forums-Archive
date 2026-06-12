---
title: "removing files"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by sports fan Matt on 2008-01-18
I already used the howto: by wacktomack (great guide) but then i saw i have over 9.4 mb in my  /var/cache/apt/archives/ folder in the home directory

How can i remove all those files?

---

### Post by wolfen69 on 2008-01-18
```
sudo nautilus
```
then navigate to the desired directory and delete.

---

### Post by p_quarles on 2008-01-18
For graphical apps use gksudo:
```
gksudo nautilus
```
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by qpieus on 2008-01-18
you can also use apt-get to do it. From the apt-get man page:```
apt-get clean clears out the local repository of retrieved
           package files. It removes everything but the lock file
           from /var/cache/apt/archives/ and
           /var/cache/apt/archives/partial/. When APT is used as a
           dselect(8) method, clean is run automatically. Those who
           do not use dselect will likely want to run apt-get clean
           from time to time to free up disk space.
```

So, ```
sudo apt-get clean
```in a terminal should do the trick.

---


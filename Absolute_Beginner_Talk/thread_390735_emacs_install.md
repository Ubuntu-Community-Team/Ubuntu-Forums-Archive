---
title: "emacs install"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by CrabbyPete on 2007-03-22
The LAMP server version does not contain emacs. I tried installing it using apt-get, but I keep getting that the package does not exist.

---

### Post by compiledkernel on 2007-03-22
sudo apt-get install emacs21 

I do believe will do it.

---

### Post by mills on 2007-03-22
delete

---

### Post by taurus on 2007-03-22
You need to enable both universe & multiverse in /etc/apt/sources.list.  From a prompt, run

```
sudo nano -Bw /etc/apt/sources.list
```
Then, remove the # in front of all the lines with deb at the beginning.  Save and exit with <Ctrl>o and <Ctrl>x.  Now, see if you can install emacs again.

```
sudo aptitude update
sudo aptitude install emacs
```

---

### Post by charles.g.moore on 2007-03-22
My best friend when searching for a package is:
sudo aptitude search <partial package name>

---


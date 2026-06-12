---
title: "How would you know what version of Ubuntu you are using ?"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by nd0627 on 2006-09-10
just installed ubuntu this am, just copied installation cd from my officemate. this is why i don't know what Ubuntu version I'm using.  any help is much appreciated. thanks !

---

### Post by Najand on 2006-09-10
The easiest way is to push:
ALT+CTRL+F1
The version is written on top of the screen.
To go back to the X window, push
ALT+F7

UBUNTU VERSIONS:
6.06 Dapper Drake
5.10 Breezy Badger
5.04 Hoary Hedgehog

---

### Post by Qrk on 2006-09-10
Open up firefox. The page that is displayed should have your version number. 6.06 is Dapper Drake, 5.10 is the previous version, Breezy Badger.

You can also go to System->help

---

### Post by mbmccormick on 2006-09-10
from a terminal window type "uname -r"

---

### Post by bulldog on 2006-09-10
> **mbmccormick said:**
> from a terminal window type "uname -r"

That's to know which kernel you use,not which Ubuntu you have.:cool:

---

### Post by Najand on 2006-09-10
> **mbmccormick said:**
> from a terminal window type "uname -r"

That will just show the kernel version, not Ubuntu Version. When using Debian there is a file /etc/debian_version has the version  of Debian distribution. There is an identical file in Ubuntu, but there is no version is shown inside.

---

### Post by savoysavvy on 2006-10-26
This command will show you the Ubuntu version:

more /etc/issue.dpkg-dist

---

### Post by meng on 2006-10-26
lsb_release -a
also shows the version.

---

### Post by ChrisNiemy on 2006-10-26
lsb_release -a says something like this:
```
c@localhorst:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu edgy (development branch)
Release:        6.10
Codename:       edgy

```

package, which provides this is "lsb-release" should be pre-installed, I guess.

---

### Post by aysiu on 2006-10-26
```
cat /etc/issue
```

---

### Post by Bloch on 2006-10-26
You need the command line to know what version you are running?

That's maaaad!!!

---

### Post by aysiu on 2006-10-26
I find it mad that people need to even ask what version they're running. Haven't most people installed their own Ubuntus?

---

### Post by happy-and-lost on 2006-10-26
Generally... the blurb on "System-->About Ubuntu" tells you ;)

---


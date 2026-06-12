---
title: "how to install programs"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by platinum on 2006-07-08
in windows, it was click setup.... :| sigh....

i want to install zsnes. but when i downloaded and extracted it, it was just a bunch of files in a src folder.

how do i install a program in ubuntu? help!

---

### Post by meng on 2006-07-08
> **platinum said:**
> in windows, it was click setup.... :| sigh....

i want to install zsnes. but when i downloaded and extracted it, it was just a bunch of files in a src folder.

how do i install a program in ubuntu? help!

Well there are several options. In the case of zsnes, it can also be installed from repositories using Synaptic or aptitude.
[http://psychocats.net/ubuntu/installingsoftware.php](http://psychocats.net/ubuntu/installingsoftware.php)

---

### Post by catlett on 2006-07-08
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by reacocard on 2006-07-08
use the package manager
Applications -> Add/Remove

if that's not powerful enough for you, then
System -> Administration -> Synaptic Package Manager

if you want to install from a package, try to find a .deb file. those you can just double-click to install. .tar.gz files are usually what is known as "source" packages, and can be tricky to install. most software you need should be available to you through one of the package managers though.

---

### Post by platinum on 2006-07-08
k. i've been fiddling with aptitude, adept, apt-get, and whatnot to get the essentials, (zsnes has to be installed from src) but when i go to install, it says that i don't have SDL 1.2 or greater, but i think i do. can someone post the apt-get for it?

---

### Post by meng on 2006-07-08
> **platinum said:**
> k. i've been fiddling with aptitude, adept, apt-get, and whatnot to get the essentials, (zsnes has to be installed from src) but when i go to install, it says that i don't have SDL 1.2 or greater, but i think i do. can someone post the apt-get for it?
Looks like zsnes is available through repositories, but you have to enable multiverse.
[https://help.ubuntu.com/community/Repositories/Ubuntu?highlight=%28repositories%29](https://help.ubuntu.com/community/Repositories/Ubuntu?highlight=%28repositories%29)

---

### Post by koshari on 2006-07-08
planinum, the whole idea of using synaptic is that any dependencies will be satisfied for you automaticly :-)

---

### Post by reacocard on 2006-07-08
and if you insist on installing from source, it may need the dev package as well as the normal one. just use

```
sudo apt-get install libsdl1.2-dev
```

to get it.

---


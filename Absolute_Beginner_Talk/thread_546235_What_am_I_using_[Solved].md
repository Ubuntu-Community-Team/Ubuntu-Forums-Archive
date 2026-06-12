---
title: "What am I using [Solved]"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by DGentry on 2007-09-08
I know this may seem rather dumb but how can I tell what Ubuntu am I using.
I see all these names, feisty fawn, kumbuntu and Gutsy something.. I'm confused.

I believe I'm using the Feisty Fawn one but I'm not for sure.

I think I want to know because I'm going to want to do the LAMP thing pretty soon and want to follow the install directions for the correct version.

---

### Post by oilchangeguy on 2007-09-08
> **DGentry said:**
> I know this may seem rather dumb but how can I tell what Ubuntu am I using.
I see all these names, feisty fawn, kumbuntu and Gutsy something.. I'm confused.

I believe I'm using the Feisty Fawn one but I'm not for sure.

I think I want to know because I'm going to want to do the LAMP thing pretty soon and want to follow the install directions for the correct version.

system, about ubuntu

---

### Post by diatribe on 2007-09-08
cat /etc/issue
or
lsb_release -a
from a terminal

---

### Post by sumguy231 on 2007-09-08
To explain the versioning, each version has a codename. For example:
6.10 = Edgy Eft
7.04 = Feisty Fawn
7.10 = Gutsy Gibbon

There are also several variations on Ubuntu, which include Kubuntu, Xubuntu, and Edubuntu. All of these release new versions at roughly the same time as Ubuntu, and have the same codenames. Chances are you're using Ubuntu.

lsb_release -a will display both the version and codename that goes with it.

---

### Post by DGentry on 2007-09-10
AH HA!!!!

doug@doug-linux:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.04
Release:        7.04
Codename:       feisty
doug@doug-linux:~$ 

Thanks Guys!!

---

### Post by z600 on 2007-10-06
Is there any way to find the version of Ubuntu (as in 32 bit or 64 bit) currently running?

---

### Post by tgalati4 on 2007-10-07
>uname -a

---

### Post by z600 on 2007-10-08
thanks mate! :)

---


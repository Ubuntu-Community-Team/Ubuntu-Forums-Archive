---
title: "installing Mercurial on Ubuntu 7.10"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by Semjah on 2007-12-07
HI I'm new to Ubuntu and I've been trying to install Mercurial. I'm getting this error message when I try to install  it.

building 'mercurial.mpatch' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O2 -Wall -Wstrict-prototypes -fPIC -I/usr/include/python2.5 -c mercurial/mpatch.c -o build/temp.linux-x86_64-2.5/mercurial/mpatch.o
mercurial/mpatch.c:23:20: error: Python.h: No such file or directory

---

### Post by celticbhoy on 2007-12-07
Where did you download from, I just checked the site and if you select binary/packages you then have the option for the Ubuntu version you are using

---

### Post by aktiwers on 2007-12-07
Hi and Welcome!

You can install in many ways, but the easiest way must be going to Applications => Accessories => Terminal

And in there type:
```
sudo apt-get install mercurial
```

Or if you are on the newest release of Ubuntu then just click this link:
[apt:mercurial](apt:mercurial)

Or go to Synaptic (its in System =>Administration=>Synaptic) and search for "Mercurial" and install the package.

Hope that helps :)

---

### Post by Semjah on 2007-12-07
> **aktiwers said:**
> Hi and Welcome!

You can install in many ways, but the easiest way must be going to Applications => Accessories => Terminal

And in there type:
```
sudo apt-get install mercurial
```

Or if you are on the newest release of Ubuntu then just click this link:
[apt:mercurial](apt:mercurial)

Or go to Synaptic (its in System =>Administration=>Synaptic) and search for "Mercurial" and install the package.

Hope that helps :)
Thanks that seems to have done the trick.

---


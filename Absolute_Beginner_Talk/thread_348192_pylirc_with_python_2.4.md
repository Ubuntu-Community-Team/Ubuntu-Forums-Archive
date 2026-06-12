---
title: "pylirc with python 2.4"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by eltidi on 2007-01-28
Hi,

I'm having trouble setting up my media center remote to work with freevo. My remote works with the lircd daemon but i can't make it work with freevo. The program complain about pylirc missing. Problem is the package I found for pylirc are only for version 2.3 of python.
So has anybody been able to make it work?

---

### Post by eltidi on 2007-01-29
Anybody

---

### Post by innercid on 2007-05-25
Hi,

I managed to get pylirc working on Ubuntu Edgy by doing the following. (assuming you have python-2.4 already installed)

Download: [http://downloads.sourceforge.net/pylirc/pylirc-0.0.5.linux-i686.tar.gz?modtime=1105050069&big_mirror=0](http://downloads.sourceforge.net/pylirc/pylirc-0.0.5.linux-i686.tar.gz?modtime=1105050069&big_mirror=0)

Extract the contents, it should create and place the following file:

```
/usr/lib/python2.3/site-packages/pylircmodule.so
```

To check if pylirc works, start a python session and type 

```
import pylirc
```

If you get an import error then it doesn't work and probably can't find the pylircmodule.so in the standard library directories.

To add a directory to the python path type:

```
export PYTHONPATH=/usr/lib/python2.3/site-packages:$PYTHONPATH
```

Now fire up a python session and type "import pylirc" again, it will now hopefully not complain ;-)

Then create your /etc/freevo/lircrc and start freevo.

Good luck!

---


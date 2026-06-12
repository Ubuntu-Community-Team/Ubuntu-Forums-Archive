---
title: "Ubuntu server installation help"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by doctorbighands on 2008-02-20
I believe I have installed Ubuntu Server 7.10 successfully. The problem has arisen when I tried to install a GUI on top by executing
```
sudo apt-get install xubuntu-desktop
```
It's giving me all sorts of dependency errors, and I don't know how to fix those.

Here are the processes it's complaining about:
hplip
guidance-backends
launchpad-integration
liblaunchpad-integration0
python-cairo
python-numeric
python-gobject
python-gtk2
python-glade2
python-notify
python-xdg
restricted-manager-core
synaptic

I tried just executing "xubuntu-desktop", and it gives me an error message beginning with "KABOOM!!!". 

I'm really stuck here.

EDIT: This install is on a desktop legacy machine, not the one I'm currently using. so copying/pasting won't be possible.

EDIT 2: I have attempted to execute ```
sudo apt-get -f install
``` but that didn't help me.

---

### Post by louieb on 2008-02-20
did you do?
```
sudo apt-get update
```
and```

sudo apt-get dist-upgrade
```
first?

---

### Post by doctorbighands on 2008-02-20
Yes and no. Won't running "dist-upgrade" turn my server install into a development version?

---

### Post by robkeys on 2008-02-20
Maybe not the most elegant fix, but you could always:

```
sudo apt-get install hplip guidance-backends launchpad-integration liblaunchpad-integration0 python-cairo python-numeric python-gobject python-gtk2 python-glade2 python-notify python-xdg restricted-manager-core synaptic
```

---

### Post by doctorbighands on 2008-02-20
The hplip file seems to be the one getting in the way. I don't need printer support on this machine, so I tried to remove it by using ```
sudo apt-get remove hplip
```

I received the following error:
```
Traceback (most recent call last):
File "/usr/sbin/update-python-modules", line 8, in <module>
from outparse import OptionParser
ValueError: bad marshal data
```

???

---

### Post by robkeys on 2008-02-20
Oh, i misunderstood: I thought it was missing those dependencies.

---

### Post by louieb on 2008-02-20
dist-upgrade just updates packages you already have.
there is an alternative.
```
sudo aptitude safe-upgrade  
```at any rate it will give you the option of saying yes or no.

>  Won't running "dist-upgrade" turn my server install into a development version?it can - if you have updated /etc/apt/sources.list to point to the Hardy repositories.  otherwise it will look for updates in the 7.10 repositories only.

---


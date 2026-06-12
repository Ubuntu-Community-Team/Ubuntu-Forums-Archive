---
title: "Update Manager"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by ayed on 2007-02-24
I installed beryl, but now I can't start my update manager! Whats wrong?
Please Help!

---

### Post by ayed on 2007-02-24
Please anyone! AAAHHAAA

---

### Post by mcduck on 2007-02-24
what happens if you try to run 'update-manager' from a terminal? Do you get any error messages?

---

### Post by ayed on 2007-02-24
ayed@ayed-desktop:~$ update-manager
Introspect error: The name org.freedesktop.UpdateManager was not provided by any .service files
no listening object (The name org.freedesktop.UpdateManager was not provided by any .service files) 
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 87, in ?
    app.main(options)
  File "/usr/lib/python2.4/site-packages/UpdateManager/UpdateManager.py", line 960, in main
    self.fillstore()
  File "/usr/lib/python2.4/site-packages/UpdateManager/UpdateManager.py", line 808, in fillstore
    self.initCache()
  File "/usr/lib/python2.4/site-packages/UpdateManager/UpdateManager.py", line 898, in initCache
    self.cache = MyCache(progress)
  File "/usr/lib/python2.4/site-packages/UpdateManager/UpdateManager.py", line 90, in __init__
    apt.Cache.__init__(self, progress)
  File "/usr/lib/python2.4/site-packages/apt/cache.py", line 36, in __init__
    self.open(progress)
  File "/usr/lib/python2.4/site-packages/apt/cache.py", line 53, in open
    self._cache = apt_pkg.GetCache(progress)
SystemError: E:Type 'repository' is not known on line 43 in source list /etc/apt/sources.list, E:The list of sources could not be read.
Unhandled exception in thread started by 
Error in sys.excepthook:

Original exception was:
ayed@ayed-desktop:~$ 


Is what happens :s!

---

### Post by ayed on 2007-02-24
People please help me...I don't like begging!!! AHAHAHAH!

---

### Post by ayed on 2007-02-25
I am sending a call out...how can I fix this problem ubuntu people?

---

### Post by alienexplorers on 2007-02-25
Try sudo apt-get update then try update-manager again.

---

### Post by jvc26 on 2007-02-25
Can we have the output of 
```

cat /etc.apt/sources.list

```
Il

---

### Post by ayed on 2007-02-25
ayed@ayed-desktop:~$ cat /etc/apt/sources.list

deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted
deb [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe
# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
# deb [http://gandalfn.club.fr/ubuntu](http://gandalfn.club.fr/ubuntu) edgy dev

deb [http://nvidia.limitless.lupine.me.uk/ubuntu](http://nvidia.limitless.lupine.me.uk/ubuntu) edgy stable
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main

## nVidia driver repository
repository

## nVidia driver repository
repository



there it is man

---

### Post by ayed on 2007-02-25
but I have a feeling there is a prob with the beryl and the nvidia at the last lines, cuz this happened after I installed beryl

---

### Post by SigmundFreud on 2007-02-25
I suggest comment out those last lines from the sources.list file (by putting a # in front of the line). Then, try again sudo apt-get update.

---

### Post by ayed on 2007-02-25
Anyone, I post the lines above, and I already stated that when I open the synaptic it says that there is a prob in line 45 in other words the nvida line, which were added becuase of beryl

---

### Post by ayed on 2007-02-25
it worked! its updating now...thanks man

---

### Post by jvc26 on 2007-02-25
I'd remove those lines from the sources.list as they arent proper repos - its just the word repository so it won't find anything there. So:
```

gksudo gedit /etc/apt/sources.list

```
And delete these lines:
```

## nVidia driver repository
repository

## nVidia driver repository
repository

```
It may work with them commented out, but to be honest they're pointless lines :)
Il

---


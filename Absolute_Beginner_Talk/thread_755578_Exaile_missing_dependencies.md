---
title: "Exaile missing dependencies"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by sdlyr8 on 2008-04-15
I am trying to install Exaile on my Ubuntu 6.06 LTS system using the instructions from [http://www.exaile.org/downloads]("http://www.exaile.org/downloads")

And every time I do, I get...
```
The following packages have unmet dependencies:
exaile:
  Depends: libatk1.0-0 (>=1.20.0) but 1.11.4-0ubuntu1 is to be installed
  Depends: libc6 (>=2.7-1) but 2.3.6-0ubuntu20.5 is to be installed
  Depends: libcairo2 (>=1.5.14) but 1.0.4-0ubuntu1.2 is to be installed
  Depends: libglib2.0-0 (>=2.12.0) but 2.10.3-0ubuntu1 is to be installed
  Depends: libgtk2.0-0 (>=2.12.0) but 2.8.20-0ubuntu1.1 is to be installed
  Depends: libpango1.0-0 (>=1.20.0) but 1.12.3-0ubuntu3 is to be installed
  Depends: python (>=2.5) but 2.4.2-0ubuntu3 is to be installed
 Depends: python-dbus  but it is not installable
  Depends: python-support (>=0.7.1) but 0.1.1ubuntu1 is to be installed

```

Even when i try using the Synaptic Package Manager, it still says the same exact message.

Can any one help me out? Thanks a ton!!

---

### Post by Inxsible on 2008-04-15
you are using the older versions of python and libpango etc.

you need to manually update those since you are still using 6.06. 

Either that, or you should upgrade to a latest version of Ubuntu.

---

### Post by joshrobinson on 2008-04-15
looks like a newer version of exaile snuck into the repo's, and not the newer packages it depends on

Dapper loses its LTS support very soon, you should really either, hold out and install hardy when it releases later this month, or install the beta now

you could also install gutsy, which is the current version right now, and alittle more proven in the field

---

### Post by Perfect Storm on 2008-04-15
Upgrade your Ubuntu for sure - alot of the stuff you want to compile needs newer libs (mostly).

---

### Post by reacocard on 2008-04-15
Dapper doesn't have new enough packages to handle the latest Exaile, you'll need to upgrade to a newer version of Ubuntu.

---


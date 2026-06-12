---
title: "Installing make"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by Hirashgeff on 2007-12-05
Im' using UBUNTU 
and I wanted To Ins tall make 3.8 
from terminal i went to make setup path   /Desktop/Install/make3.8/
and  typed ./configure
it worked properly  then i typed make 
the make *** error comes with following massage [IMG]F:\3d_breakout/Screenshot.png[/IMG]
1. "making all in po"
2 "Entering directory /Desktop/Install/make3.8/po"
3 "make[1]:*** no rule to make target 'all' .stop.
4"leaving directory /Desktop/Install/make3.8/po"
5" make[1]:*** [all-recursive] Error 1"
6 "leaving directory /Desktop/Install/make3.8 "
7"make:*** [all] error 2

---

### Post by AndyCooll on 2007-12-05
Possibly because you need certain apps installed in the first instance. From the command line the following should do the trick (I think it installs a version of make as part of the collection):

```
sudo apt-get build-essential
```

Or using a gui you could search for the above package in Add/Remove or Synaptic.

:cool:

---

### Post by Hirashgeff on 2007-12-05
> **AndyCooll said:**
> Possibly because you need certain apps installed in the first instance. From the command line the following should do the trick (I think it installs a version of make as part of the collection):

```
sudo apt-get build-essential
```

Or using a gui you could search for the above package in Add/Remove or Synaptic.

:cool:

Il try this
tahnk u

---


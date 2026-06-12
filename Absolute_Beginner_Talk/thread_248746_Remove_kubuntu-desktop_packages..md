---
title: "Remove kubuntu-desktop packages."
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by PingunZ on 2006-09-01
Hey, I installed the kubuntu-desktop package. ( using apt-get )
I didn't like kde ..
So how can I remove all kubuntu-desktop packages.
I mean all the packages that install when you install the kubuntu-desktop package.

Btw :: sudo apt-get remove kubuntu-desktop didn't work ;)

---

### Post by PPAAUULL on 2006-09-01
That should have worked. It worked for me.

---

### Post by PingunZ on 2006-09-01
Paul, Was all the Kubuntu gone ?
--> Usplash, Kde, ... everything 
with " sudo apt-get remove kubuntu-desktop "

---

### Post by aysiu on 2006-09-01
If you install it with *apt-get* then the command *sudo apt-get remove kubuntu-desktop* will, in fact, do nothing. Next time you want to try out software, use *aptitude* instead:
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

In the meantime, this may work for you:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by ajgreeny on 2006-09-01
The best way to do it is to 
1  Reinstall kubuntu-desktop with aptitude.
This will remember all the packages you have installed, and then
2  Uninstall kubuntu-desktop with aptitude, which will now uninstall everything you just reinstalled.

It is always worth using aptitude for metapackages like (k-x)ubuntu-desktop as if you just use apt-get as you did, all that is removed is the few kb of the kubuntu-desktop, not everything that came with it.

---

### Post by PingunZ on 2006-09-01
Aysiu, again : I Love You :)

---


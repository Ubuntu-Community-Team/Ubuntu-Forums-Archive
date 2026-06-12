---
title: "Problems installing a tarball"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by think13 on 2006-09-25
OK, I downloaded this tarball, I believe it is called (it happens to be xboard, a GUI for Gnuchess).  well, I cd'ed to its directory, read the readme (which basically said type ./configure and then make).

When I typed ./configure, it said it couldn't find gcc.  I looked in the synaptic package manager, and sure enough, I have gcc, the latest version. 

Help please?

---

### Post by lreyes6 on 2006-09-25
ok what you are doing is compiling software... you need more than only gcc... go to synaptic or via console with aptitude and install a package called **build-essential** then try to compile your tar ball

hope this helps

---

### Post by think13 on 2006-09-25
It helped, it started installing, but now it says that it requires x window system header files and libraries.  I am looking for them in the package manager.

---

### Post by bodhi.zazen on 2006-09-25
First enable your repositories.
```
sudo aptitude install build-essential kernel-headers-'uname-r' checkinstall
./configure
make
sudo checkinstall
```

---

### Post by aysiu on 2006-09-25
Why not install *xboard* through Synaptic? It's in the Universe repositories (Settings > Repositories > Check the Universe boxes > Reload)

---

### Post by think13 on 2006-09-25
OK, I found it now, Thank you!

---


---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by ZeroFive1 on 2008-02-25
So whenever I install something, I get this error:

E: nfs-common: subprocess post-installation script returned error exit status 127
E: nfs-kernel-server: dependency problems - leaving unconfigured

I also get this:

E: Sub-process /usr/bin/dpkg returned an error code (1)

I think everything works, but this really annoys me. Halp?

---

### Post by jan quark on 2008-02-26
try these commands 

just a guess perhaps they will help
```

sudo dpkg --configure -a
```

```
sudo apt-get -f install
```

---

### Post by ZeroFive1 on 2008-02-26
Same problem.

He're the whole thing:

Setting up nfs-common (1:1.1.1~git-20070709-3ubuntu1) ...
/usr/bin/ucf: line 351: getopt: command not found
dpkg: error processing nfs-common (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of nfs-kernel-server:
 nfs-kernel-server depends on nfs-common (>= 1:1.0.8-1); however:
  Package nfs-common is not configured yet.
dpkg: error processing nfs-kernel-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nfs-common
 nfs-kernel-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Seisen on 2008-02-26
Check to make sure that ```
util-linux
``` is installed then try ```
sudo dpkg --reconfigure -a
```

---

### Post by az on 2008-02-26
Try

sudo dpkg -r nfs-common 

and then sudo apt-get -f install

---

### Post by az on 2008-02-26
> **Seisen said:**
> Check to make sure that ```
util-linux
``` is installed then try ```
sudo dpkg --reconfigure -a
```

I agree, but how can you install a package when the package manager it tied into a knot?  nfs-common and nfs-kernel-server need to be removed first to get the package manager working again.

---

### Post by Anicka on 2008-02-26
Try:```
sudo dpkg --configure --force-configure-any -a
```

---

### Post by ZeroFive1 on 2008-02-26
Thanks a lot seisen! Seems that linux32 was the problem, and installing util-linux removed that for me. I guess that wasn't needed since I'm on a AMD64 computer!

---


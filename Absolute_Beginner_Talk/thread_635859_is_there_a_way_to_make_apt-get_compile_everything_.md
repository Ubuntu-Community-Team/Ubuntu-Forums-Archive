---
title: "is there a way to make apt-get compile everything from source code"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by cosmoshell on 2007-12-09
is there a way to make ubuntu compile everything from source code like gentoo does.

---

### Post by mcduck on 2007-12-09
Not really. You can use apt-get to download source codes and all dependencies, but it won't automatically compile them for you. Of course creating a script to do that shouldn't be too hard but Ubuntu/Debian really is more binary-oriented distribution and I highly doubt you would get any true benefits from compiling everything yourself.

---

### Post by zero-9376 on 2007-12-09
take a look at apt-build, in the repos but not installed by default

---

### Post by cosmoshell on 2007-12-09
apt-buld works like a charm. just reinstalled a couple programs and ther run a sec faster now. to bad it takes so long for it to compile everything

---

### Post by SOULRiDER on 2007-12-09
If you want to build everything from source you could use Gentoo. I run Gentoo but honestly, it doesnt run much faster that my Archlinux installaition. There is a speedup, yes, but its not too big and it gets sort of cancelled by how long it takes to compile some packages.

---

### Post by cosmoshell on 2007-12-09
im fine with ubuntu im not going to compile everything just what i use the most.

---

### Post by SOULRiDER on 2007-12-09
What also sucks is that you will have to install lots of -dev libraries just to compile one single program. IMHO just go for the binaries provided with the distro.

---

### Post by cosmoshell on 2007-12-09
> **SOULRiDER said:**
> What also sucks is that you will have to install lots of -dev libraries just to compile one single program. IMHO just go for the binaries provided with the distro.
are those -dev libraries uninstalled afterwords?

---


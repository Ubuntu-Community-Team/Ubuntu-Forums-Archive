---
title: "how to install latex"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by jinxjinx on 2006-10-30
when i type this: sudo apt-get install tetex-base tetex-bin tetex-extra
i get: Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package tetex-base

i have everything uncommented in my sources.list

whats up?

Thanks

---

### Post by Skia_42 on 2006-10-30
Open up synaptic and install latex from there. It will ensure that all the dependencies are filled.

---

### Post by jinxjinx on 2006-10-30
when i type latex into synaptic it cant find anything.

---

### Post by jinx099 on 2006-10-30
hello fellow jinx ;)

Did you run apt-get update after you enabled the extra repos?  Heres what I get when I search for the package you are looking for:

```
jinx@conroe:~$ apt-cache search tetex-base
linuxdoc-tools - SGML converters for the LinuxDoc DTD only.
tetex-base - Basic library files of teTeX
tetex-doc - The documentation component of the Debian teTeX packages
tetex-extra - Additional library files of teTeX
tex-common - Common infrastructure for using and building TeX in Debian
bnfc - Compiler front-end generator based on Labelled BNF

```

---

### Post by jinxjinx on 2006-10-30
umm. will that auto install updates? i really dont want to update my window manager because it will break some code im working on.

---

### Post by IYY on 2006-10-31
> umm. will that auto install updates? i really dont want to update my window manager because it will break some code im working on.

Before updating, it will tell you the packages it wants to update. If you are making changes to your window manager's source code, chances are it's a newer version that the one in the repos and it won't even be in the update list. 

If you really don't want to do this, just grab the tetex debs from here: [http://packages.ubuntu.com/dapper/](http://packages.ubuntu.com/dapper/)

---


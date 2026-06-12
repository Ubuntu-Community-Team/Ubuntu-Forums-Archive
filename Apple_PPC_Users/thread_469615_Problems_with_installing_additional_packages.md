---
title: "Problems with installing additional packages"
date: 2007-06-10
forum: Apple PPC Users
---

### Post by oh2345 on 2007-06-10
I installed ubuntu-7.04-desktop-powerpc.iso on a PowerMac G3 (it took me an hour to find that iso on the internet, because it is not listed or linked on [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) - please fix).

Now I need a lot of extra packages, mainly for  compiling X11 programs (libs, header-files...). When I click on "Add/Remove Application", it tries to download package information, but that always hangs at file 38/42.

Question: where can I find Ubuntu/PowerMac packages on the internet for manual installation?

---

### Post by ssam on 2007-06-10
you have trouble with add/remove, you can always try system->administration->Synaptic package manager. it is a bit more stable (though not quite as friendly).

to get individual packages from the web try [http://packages.ubuntu.com/](http://packages.ubuntu.com/) . this will be slow though, as you will need to get not just the package you want but any dependencies.

---

### Post by SycloneMedia on 2007-06-10
If you happen to know the exact names of the packages, the best way to get them is to use the terminal and aptitude (not apt-get):

```
sudo aptitude update
```

then...

```
sudo aptitude install (list your packages here with a space in between the names)
```

---


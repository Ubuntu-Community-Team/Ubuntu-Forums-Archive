---
title: "gsynaptics"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by Baelfael on 2007-06-10
Alright so I'm on GNOME and I want to install gsynaptics so i can configure my touchpad and turn off touch click, so I type:

```
sudo apt-get install gsynaptics'
```

and output with this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libkscan1 linux-headers-2.6.20-15-generic liblockdev1 latex-xft-fonts
  qca-tls koffice-data libjasper-runtime libmono-sqlite2.0-cil ocrad
  linux-headers-2.6.20-15 gtk-qt-engine qobex koffice-libs kitchensync
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  gsynaptics
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
3 not fully installed or removed.
Need to get 26.4kB of archives.
After unpacking 279kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  gsynaptics
Install these packages without verification [y/N]? y
Err http://ubuntusoftware.info edgy/all gsynaptics 0.9.9-1getdeb2
  404 Not Found
Failed to fetch http://ubuntusoftware.info/./gsynaptics_0.9.9-1getdeb2_i386.deb  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

What gives? Why can't it find the package? Is there another way to install gsynaptics? Is something not updated? (I've already tried installing it with Add/Remove and Synaptic Package Manager).

Help please?

---

### Post by Baelfael on 2007-06-10
Nevermind, figured it out on my own. Had to force feisty version on it in package manager...

---


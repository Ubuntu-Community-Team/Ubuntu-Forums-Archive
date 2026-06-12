---
title: "ubuntu:broken?"
date: 2005-12-11
forum: Absolute Beginner Talk
---

### Post by Jonah21 on 2005-12-11
I've been installing a number of apps and such via the console, but since this morning  I keep getting this error message for a number of apt-get operations:

W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

---

### Post by teaker1s on 2005-12-11
either repositories are down or you need to look a limitations in help and try that
my money is on  repositories

---

### Post by Jonah21 on 2005-12-11
Should I just wait then try and get the extra repositories again later?

---

### Post by linbetwin on 2005-12-11
If the repositories worked yesterday, they'll probably work tomorrow (or maybe even sooner).

---

### Post by jrib on 2005-12-11
Ubuntu backports are no longer on mirrormax.  You need to update your /etc/apt/sources.list: [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by Jonah21 on 2005-12-11
Cheers, worked like a charm.

---


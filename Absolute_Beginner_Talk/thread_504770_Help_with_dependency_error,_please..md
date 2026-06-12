---
title: "Help with dependency error, please."
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by wjhildreth on 2007-07-19
Hello all,

I am wanting to try a newer version of gpsdrive. I downloaded a deb called:

gpsdrive_2.10svn14843607_i386.deb

when I try to install it I get the following error:

Dependency is not satisfiable: mapnik-plugins.

I tried looking for mapnik using Synaptic package manager with no results. Can someone point me in the right direction?

Warm regards,

Joe Hildreth

---

### Post by Happy_Man on 2007-07-19
It may not be in the repos. But it is in the Debian package lists... here's a link to download: [http://packages.debian.org/unstable/libs/mapnik-plugins](http://packages.debian.org/unstable/libs/mapnik-plugins)

Just be sure to install it first.

---

### Post by Rocket2DMn on 2007-07-19
There is an unstable version available in a deb package at [http://packages.debian.org/unstable/libs/mapnik-plugins](http://packages.debian.org/unstable/libs/mapnik-plugins)
You can also check out [http://mapnik.org/documentation/install/](http://mapnik.org/documentation/install/)
Looks like you will have to build the package.

---

### Post by wjhildreth on 2007-07-19
Thanks, I will take a look.

Regards,

Joe

---

### Post by riven0 on 2007-07-19
Just a small warning that you may already know. Make sure you uninstall gpsdrive before installing anything else, or you'll keep on getting errors. > sudo apt-get autoremove gpsdrive ...or whatever the program is named

---

### Post by wjhildreth on 2007-07-19
Interesting, when I try to install the deb, I get a dependency for libc6 but libc6 is installed on the system.

Joe

---

### Post by wjhildreth on 2007-07-19
Thanks for the pointer riven0, I did not know that.

Joe

---

### Post by wjhildreth on 2007-07-19
It is turning into a dependency hell. I think given my level of expertise, I should leave it alone. At least until I learn more. Thanks for all your help.

Regards,

Joe

---


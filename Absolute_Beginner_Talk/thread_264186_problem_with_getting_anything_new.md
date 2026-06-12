---
title: "problem with getting anything new?"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by cryptidan on 2006-09-24
here's what happens, even with apt-get update (except longer)

root@Dayzeez:/home/dayzeez420# sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

---

### Post by cryptidan on 2006-09-24
anyone? please?

---

### Post by siacs on 2006-09-24
Third party repositories change or even disappear over time, especially with old releases. The first is definitely gone, the second has changed their directory structure, and the third is either gone or they only support Dapper now. That's just the way it is when you're using an old release and depend on third party repos. Remove those repos and you should be fine.

---

### Post by cryptidan on 2006-09-24
Ya gotta understand, I really don't know much, can this be fixed?  I tried to get dapper, but can't evn get that with this...

---

### Post by siacs on 2006-09-24
In Synaptic goto Settings > Repositories and untick the repositories that are giving you problems, then click on the reload button on the main menu.

---

### Post by bulldog on 2006-09-24
> **cryptidan said:**
> Ya gotta understand, I really don't know much, can this be fixed?  I tried to get dapper, but can't evn get that with this...

Better to download Dapper and do a fresh install.
When you have reasons to upgrade Breezy via the repo's,you should make a sources.list with the Dapper repo's in it.

Then try to do

sudo aptitude update

sudo aptitude dist-upgrade

and pray everything works afterward.

---


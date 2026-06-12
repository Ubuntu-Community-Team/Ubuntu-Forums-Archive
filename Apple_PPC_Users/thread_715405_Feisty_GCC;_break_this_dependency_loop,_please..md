---
title: "Feisty GCC; break this dependency loop, please."
date: 2008-03-04
forum: Apple PPC Users
---

### Post by franklynb on 2008-03-04
I'm trying to install gcc-4.1, which is completely missing from feisty repositories <in fact there is no working C compiler configuration!>. Using dpkg, I've run into this loop:

$ sudo dpkg --configure  libstdc++6-4.1-dev
dpkg: dependency problems prevent configuration of libstdc++6-4.1-dev:
** libstdc++6-4.1-dev depends on g++-4.1 (= 4.1.2-0ubuntu4)**; however:
  Package g++-4.1 is not configured yet.
dpkg: error processing libstdc++6-4.1-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libstdc++6-4.1-dev
$ sudo dpkg --configure g++-4.1
dpkg: dependency problems prevent configuration of g++-4.1:
 **g++-4.1 depends on libstdc++6-4.1-dev (= 4.1.2-0ubuntu4)**; however:
  Package libstdc++6-4.1-dev is not configured yet.
dpkg: error processing g++-4.1 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 g++-4.1
$

please suggest appropriate action.

thanks!

G4 Powerbook, Ubuntu 7.04

---

### Post by franklynb on 2008-03-04
dpkg --force-configure-any

---

### Post by linear on 2008-03-05
> **franklynb said:**
> I'm trying to install gcc-4.1, which is completely missing from feisty repositories <in fact there is no working C compiler configuration!>.

:confused: Huh? Do you mean [this]("http://packages.ubuntu.com/feisty/gcc") doesn't work? (By the way, it's usually recommended that you install the build-essential package, to be sure you get all the necessary parts.)

---


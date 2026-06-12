---
title: "ttf-opensymbol is screwing everything up"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by bump_ on 2007-08-25
Everytime I try to upgrade, I get a whole slew of error messages along with the updates

```
beast@command:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
13 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up ttf-opensymbol (2.2.0-1ubuntu4) ...
Updating fontconfig cache...
Bus error (core dumped)
dpkg: error processing ttf-opensymbol (--configure):
 subprocess post-installation script returned error exit status 135
dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on ttf-opensymbol; however:
  Package ttf-opensymbol is not configured yet.
dpkg: error processing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-impress depends on openoffice.org-draw (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-kde:
 openoffice.org-kde depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-kde (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-writer depends on python-uno (>= 2.2.0); however:
  Package python-uno is not configured yet.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-common:
 openoffice.org-common depends on openoffice.org-core (>> 2.2.0) | openoffice.org-core-experimental (>> 2.2.0); however:
  Package openoffice.org-core is not configured yet.
  Package openoffice.org-core-experimental is not installed.
dpkg: error processing openoffice.org-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common; however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-human:
 openoffice.org-style-human depends on openoffice.org-common (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-human (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-crystal:
 openoffice.org-style-crystal depends on openoffice.org-common (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-crystal (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ttf-opensymbol
 openoffice.org-core
 openoffice.org-calc
 openoffice.org-draw
 openoffice.org-impress
 openoffice.org-kde
 openoffice.org-math
 python-uno
 openoffice.org-writer
 openoffice.org-common
 openoffice.org-java-common
 openoffice.org-style-human
 openoffice.org-style-crystal
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I think openoffice.org-core depends on ttf-opensymbol and since it can't be configured, oppenoffice-core and the rest can't either. I tried taking a look at another post on these forums for the same problem, but it didn't really help.

---

### Post by bump_ on 2007-08-25
Sorry to sound impatient, but this is driving me nuts!

---

### Post by Maybe_Factor on 2008-02-07
please direct your attention to my post here: [http://ubuntuforums.org/showthread.php?p=4286725#post4286725](http://ubuntuforums.org/showthread.php?p=4286725#post4286725)

---


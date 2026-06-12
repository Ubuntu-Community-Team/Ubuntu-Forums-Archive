---
title: "[SOLVED] can't upgrade... broken packages.. :("
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by Kosimo on 2007-10-20
I'm trying to upgrade my system, but after sudo apt-get upgrade:

> $ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libaudacious5: Depends: libmcs1 but it is not installed
E: Unmet dependencies. Try using -f.


Then, I try sudo apt-get upgrade -f 

> $ sudo apt-get upgrade -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following NEW packages will be installed:
  libmcs1
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/13.1kB of archives.
After unpacking 86.0kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 124676 files and directories currently installed.)
Unpacking libmcs1 (from .../libmcs1_0.4.1-2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libmcs1_0.4.1-2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libmcs.so.1.0.0', which is also in package mcs
Errors were encountered while processing:
 /var/cache/apt/archives/libmcs1_0.4.1-2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I can't remove this /libmcs.so.1.0.0 witch is the one that seems to be broken.
Any help please?

I'm in gutsy by the way.

Thank yo in advance.

---

### Post by Kosimo on 2007-10-20
help pleasee!! :(

---

### Post by Sef on 2007-10-20
From the Terminal try this command:

```
sudo dpkg --configure -a
```

---

### Post by Kosimo on 2007-10-20
It found maybe the reason:

> ~$ sudo dpkg --configure -a
[sudo] password for cosimo:
dpkg: dependency problems prevent configuration of libaudacious5:
 libaudacious5 depends on libmcs1; however:
  Package libmcs1 is not installed.
dpkg: error processing libaudacious5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of audacious-plugins:
 audacious-plugins depends on libaudacious5; however:
  Package libaudacious5 is not configured yet.
dpkg: error processing audacious-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of audacious:
 audacious depends on libaudacious5; however:
  Package libaudacious5 is not configured yet.
 audacious depends on audacious-plugins (>= 1.3); however:
  Package audacious-plugins is not configured yet.
 audacious depends on audacious-plugins (<< 1.4); however:
  Package audacious-plugins is not configured yet.
dpkg: error processing audacious (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libaudacious5
 audacious-plugins
 audacious


I tried to install audacious 1.4beta from some deb I found in this forum.

But Audacious is uninstalled already from synaptic...

How can I uninstall this broken packages?

---

### Post by mikeyphi on 2007-10-20
Use this in a terminal:

sudo dpkg -i --force-overwrite /var/cache/apt/archives/libmcs1_0.4.1-2_i386.deb
sudo apt-get -f install

---

### Post by Kosimo on 2007-10-20
> **mikeyphi said:**
> Use this in a terminal:

sudo dpkg -i --force-overwrite /var/cache/apt/archives/libmcs1_0.4.1-2_i386.deb
sudo apt-get -f install

It works perfectly.
Thank you so much mate!

---


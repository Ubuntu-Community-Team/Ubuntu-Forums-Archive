---
title: "dvd::rip"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by eriefisher on 2006-02-01
Trying to down load dvd::rip. Is this still available or do I just have a sources list problem.

dan@ubuntubox:~$ sudo apt-get install dvdrip
Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  dvdrip: Depends: transcode (>= 2:0.6.14) but it is not going to be installed
          Depends: libgtk-perl but it is not installable
          Depends: libgtk-pixbuf-perl but it is not installable
          Depends: libevent-perl but it is not installable
          Depends: libintl-perl but it is not installable
E: Broken packages
dan@ubuntubox:~$

To start with I could not download transcode dependencies. Anyone else having problems with this.

eriefisher

---

### Post by DiscoKiller on 2006-02-01
i think this is simply a lack of repositories available to you, if u enter synaptic go to the proterties tab-->repositories-->settings and check the 'show disabled software sources' box. then back out of that and check every repo on the list you have in the software sources window. back out of that and click reload. then u can search for dvdrip in synaptic or i think u can add it with the 'Add Applications' function or just go on ahead with your command line approach....hope this works


DK

---


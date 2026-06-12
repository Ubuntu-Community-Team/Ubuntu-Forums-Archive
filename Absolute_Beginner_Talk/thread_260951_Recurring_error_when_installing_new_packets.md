---
title: "Recurring error when installing new packets"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by Humbug-swe on 2006-09-19
The following problems were found on your system:

E: clvm: subprocess post-installation script returned error exit status 3
E: redhat-cluster-suite: dependency problems - leaving unconfigured
E: system-config-cluster: dependency problems - leaving unconfigured

Happens once in a while when installing packages. Is this something i should be concerned with - and even if it isn't - how do i get rid of it?

(I've tried to post things from the terminal since there seems to be more info regaring the problem, but i can't seem to copy the text.

the last time i got these messages was when installing libxine-extracodecs

when looking in syslog I se one thing that is recurring: "Sep 19 22:09:52 localhost ccsd[3850]: Unable to connect to cluster infrastructure after 7260 seconds." - Could this have something to do with the problem?

---

### Post by Humbug-swe on 2006-09-19
Back again.

I've now tried to install from the terminal:

0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 391kB of archives.
After unpacking 1946kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe firestarter 1.0.3-1.1ubuntu4 [391kB]
Fetched 391kB in 1s (196kB/s)
Selecting previously deselected package firestarter.
(Reading database ... 101816 files and directories currently installed.)
Unpacking firestarter (from .../firestarter_1.0.3-1.1ubuntu4_i386.deb) ...
Setting up clvm (2.02.02-1ubuntu1) ...
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error processing clvm (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of redhat-cluster-suite:
 redhat-cluster-suite depends on clvm; however:
  Package clvm is not configured yet.
dpkg: error processing redhat-cluster-suite (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-cluster:
 system-config-cluster depends on redhat-cluster-suite; however:
  Package redhat-cluster-suite is not configured yet.
dpkg: error processing system-config-cluster (--configure):
 dependency problems - leaving unconfigured
Setting up firestarter (1.0.3-1.1ubuntu4) ...

Errors were encountered while processing:
 clvm
 redhat-cluster-suite
 system-config-cluster
E: Sub-process /usr/bin/dpkg returned an error code (1)


Hope this helps.

---

### Post by Humbug-swe on 2006-09-20
... and once more - back again.


I've deleted redhat-cluster-suite & system-config-cluster. I tried to delete clvm aswell, but I get an error.

I'm at work now, so I can't give the error message. I'll post it when i get back home.

---

### Post by Mapleman on 2006-09-23
I am having the same issue exactly, CLVM seems to be the root from what I can tell from the terminal feedback, but I can't open .rpm at all or install them due to this issue. I sent a bug report in two days ago though so a fix must be in the works, I was able to uninstall all three and replace with latest versions but nothing has changed ](*,)

---


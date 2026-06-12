---
title: "Installing Java"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by Corgylegs on 2007-10-09
> corgylegs@corgylegs-comp:~$ sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
sun-java6-plugin is already the newest version.
The following NEW packages will be installed
  sun-java6-fonts
0 upgraded, 1 newly installed, 0 to remove and 34 not upgraded.
3 not fully installed or removed.
Need to get 0B/1814B of archives.
After unpacking 115kB of additional disk space will be used.
Selecting previously deselected package sun-java6-fonts.
(Reading database ... 119710 files and directories currently installed.)
Unpacking sun-java6-fonts (from .../sun-java6-fonts_6-00-2ubuntu2_all.deb) ...
Setting up clvm (2.02.06-2ubuntu9) ...
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
Setting up sun-java6-fonts (6-00-2ubuntu2) ...
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for Headline-Regular, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for Gulim-Regular, defaulting to 0.

Errors were encountered while processing:
 clvm
 redhat-cluster-suite
 system-config-cluster
E: Sub-process /usr/bin/dpkg returned an error code (1)


can anyone explain whats gone wrong?

---

### Post by Frak on 2007-10-09
Are you running feisty or gutsy?

---

### Post by Corgylegs on 2007-10-09
ubuntu 7.04?

---

### Post by Corgylegs on 2007-10-09
bump?

---

### Post by Frak on 2007-10-09
Goto Add/Remove in Applications->Add/Remove
Enable All available
then search for Restricted Extras and install them. If it doesn't work, post back.

---


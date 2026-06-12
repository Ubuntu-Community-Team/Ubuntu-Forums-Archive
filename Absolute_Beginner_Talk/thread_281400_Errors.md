---
title: "Errors"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by Avinator on 2006-10-21
Hello, 

I am getting errors on updates and other items... I tried

~$ sudo apt-get -f install

Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up clvm (2.02.02-1ubuntu1) ...
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error processing clvm (--configure):
 subprocess post-installation script returned error exit status 3
Errors were encountered while processing:
 clvm
E: Sub-process /usr/bin/dpkg returned an error code (1)

Other Errors:


Errors were encountered while processing:
clvm
redhat-cluster-suite
system-config-cluster
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:
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
Errors were encountered while processing:
clvm
redhat-cluster-suitefile

system-config-cluster


Thanks again for your help

Cheers !

---

### Post by neorush on 2006-11-01
I had this same problem so I removed all the clvm.* scripts from '/var/lib/dpkg/info' then ran 'apt-get remove clvm'
it complained about not being able to find the clvm scripts and then removed it:

dpkg: serious warning: files list file for package 'clvm' missing, assuming package has no files currently installed.
Removing clvm ...

This solved the problem.  I haven't tried re-installing....

---


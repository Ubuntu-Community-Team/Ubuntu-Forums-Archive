---
title: "Application Error, Please help"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by likeawalrus55 on 2006-08-04
I have searched teh intarwebs for the answer to my error to no solution.  I have been running Ubuntu, and when trying to download an application, usually archived, I use the terminal to download directly from the site, extract, change directories and begin the install.  However, during this fourth step I am stopped by the same error:

clvmd could not connet to cluster manager
Consult syslog for more information
invoke-rc.d:initscript clvm, action "start" failed.
dpkg:error processing clvm (--configure):
  subprocess post-installation script returned error exit status 3
dpkg:dependecy problems prevent configuration of redhat-cluster-suite:
    redhat-cluster-suite depends on clvm; however:
      Package clvm is not configured yet.
dpkg:error processing redhat-cluster-suite (--configure):
  dependency problems, leave unconfigured
dpkg:dependecy problems prevent configuration of system-config-cluster:
    system-config-cluster depends on redhat-config-cluster; however:
      Package redhat-cluster-suite is not configured yet.
dpkg:error processing system-config-cluster (--configure):
  dependency problems, leave unconfigured
Errors were encountered while processing:
  clvm
  redhat-cluster-suite
  system-config-cluster


It is apparent that my problems are stemming from Ubuntu not being able to connect to the cluster manager.  I have tried many other solutions, but to no avail.  Please help...

---


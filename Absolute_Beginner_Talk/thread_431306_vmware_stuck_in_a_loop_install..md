---
title: "vmware stuck in a loop install."
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by buntuboob on 2007-05-02
After trying to install vmware player, all I get now from any package manager (dpkg, apt-get, snyaptic, automatix) is: E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

Once I run the command either as root or sudo, the vmware configure script begins to run and tries to setup vmware. 

Of course it errors every time and runs every time I try to update or install something. The instructions at the end of the attempt say to run /usr/bin/vmware-config.pl to try again. I have deleted this file hoping that it would not run anymore, but it continues to do so. 

Any ideas on how I can clear this?

---

### Post by jhansonxi on 2007-05-11
[https://bugs.launchpad.net/ubuntu/+source/vmware-player/+bug/57957/comments/8](https://bugs.launchpad.net/ubuntu/+source/vmware-player/+bug/57957/comments/8)

---


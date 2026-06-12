---
title: "Doc Books versus upgrading"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2006-06-12
Following ubuntu_demon's:

[http://www.ubuntuforums.org/showthread.php?t=185467](http://www.ubuntuforums.org/showthread.php?t=185467)

advising: "You should remove docbook-utils before upgrading." 

What has docbook-utils have to do with my Brother Model HL-1440 laser printer?

mark@lexington:~$ sudo apt-get remove docbook-utils
Reading package lists... Done
Building dependency tree... Done
Package docbook-utils is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 1047 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up hl1440lpr (1.1.2-1) ...
mkdir: cannot create directory `/var/spool/lpd/HL1440': No such file or directory
chown: cannot access `/var/spool/lpd/HL1440': No such file or directory
chgrp: cannot access `/var/spool/lpd/HL1440': No such file or directory
chmod: cannot access `/var/spool/lpd/HL1440': No such file or directory
/var/lib/dpkg/info/hl1440lpr.postinst: line 4: /etc/init.d/lpd: No such file or directory
dpkg: error processing hl1440lpr (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 hl1440lpr
E: Sub-process /usr/bin/dpkg returned an error code (1)

---


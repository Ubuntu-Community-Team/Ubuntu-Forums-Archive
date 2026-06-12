---
title: "Help installing Ruby"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by Chagui on 2008-03-14
I'm new to linux using ubunty 7.10.  I'm trying to install Ruby-1.8.6 with no success. I get this error:
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 mfc9700lpr
E: Sub-process /usr/bin/dpkg returned an error code (1)
E: Failed to process build dependencies

---

### Post by finer recliner on 2008-03-14
how are you trying to install ruby?

i recommend installing from the repositories:
```
sudo apt-get install ruby
```

---

### Post by Chagui on 2008-03-14
This is the information I got when installing from the repository:

sgalarza@sgalarza-desktop:~$ sudo apt-get install ruby
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  ruby1.8
Suggested packages:
  ruby1.8-examples rdoc1.8 ri1.8
The following NEW packages will be installed:
  ruby ruby1.8
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/258kB of archives.
After unpacking 426kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package ruby1.8.
(Reading database ... 99158 files and directories currently installed.)
Unpacking ruby1.8 (from .../ruby1.8_1.8.6.36-1ubuntu3_i386.deb) ...
Selecting previously deselected package ruby.
Unpacking ruby (from .../archives/ruby_1.8.2-1_all.deb) ...
Setting up mfc9700lpr (1.1.2-1) ...
mkdir: cannot create directory `/var/spool/lpd/MFC9700': No such file or directory
chown: cannot access `/var/spool/lpd/MFC9700': No such file or directory
chgrp: cannot access `/var/spool/lpd/MFC9700': No such file or directory
chmod: cannot access `/var/spool/lpd/MFC9700': No such file or directory
/var/lib/dpkg/info/mfc9700lpr.postinst: 4: /etc/init.d/lpd: not found
dpkg: error processing mfc9700lpr (--configure):
 subprocess post-installation script returned error exit status 127
Setting up ruby1.8 (1.8.6.36-1ubuntu3) ...
Setting up ruby (1.8.2-1) ...
Errors were encountered while processing:
 mfc9700lpr
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by SOULRiDER on 2008-03-14
Try these:
```
sudo aptitude update
sudo aptitude clean
sudo aptitude dist upgrade
```
and finally
```
sudo aptitude install ruby
```

---

### Post by Chagui on 2008-03-23
Thanks it worked!!! :)

---


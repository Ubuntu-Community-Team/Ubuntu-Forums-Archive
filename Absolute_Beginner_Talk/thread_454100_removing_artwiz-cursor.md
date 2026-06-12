---
title: "removing artwiz-cursor"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by alienexplorers on 2007-05-25
I am trying to remove artwiz-cursor and I get this message.

> terminator@terminator-desktop:~$ sudo aptitude purge artwiz-cursor
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be REMOVED:
  artwiz-cursor{p}
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 65.5kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 144936 files and directories currently installed.)
Removing artwiz-cursor ...
Removing `diversion of /usr/share/X11/fonts/misc/cursor.pcf.gz to /usr/share/X11/fonts/misc/cursor.pcf.gz-artwiz by artwiz-cursor'
update-alternatives: unable to make /usr/X11R6/lib/X11/icons/default/index.theme.dpkg-tmp a symlink to /etc/alternatives/x-cursor-theme: No such file or directory
dpkg: error processing artwiz-cursor (--purge):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 artwiz-cursor
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:


---

### Post by guitarmaniac on 2007-05-25
thats really weird.
probably wont help, but have you tried removing it with apt-get instead?

---

### Post by alienexplorers on 2007-05-25
Yes I have tried removing it via apt-get.  I get this error message.
> terminator@terminator-desktop:~$ sudo apt-get remove artwiz-cursor
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  artwiz-cursor
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 65.5kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 144936 files and directories currently installed.)
Removing artwiz-cursor ...
Removing `diversion of /usr/share/X11/fonts/misc/cursor.pcf.gz to /usr/share/X11/fonts/misc/cursor.pcf.gz-artwiz by artwiz-cursor'
update-alternatives: unable to make /usr/X11R6/lib/X11/icons/default/index.theme.dpkg-tmp a symlink to /etc/alternatives/x-cursor-theme: No such file or directory
dpkg: error processing artwiz-cursor (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 artwiz-cursor
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by alienexplorers on 2007-05-25
Bump...  I really want to get this problem fixed.

---

### Post by alienexplorers on 2007-05-25
Got this fixed.  A file was corrupt in the /usr/X11R6 directory.

---


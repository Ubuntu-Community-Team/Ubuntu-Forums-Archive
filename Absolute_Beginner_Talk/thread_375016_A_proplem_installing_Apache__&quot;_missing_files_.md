---
title: "A proplem installing Apache  &quot; missing files &quot; .."
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by almasry on 2007-03-03
I installed apache ,but there was some missing files , i tried updating and re-installing the missing files and using the command : > sudo apt-get update --fix-missing   but no way , i think i am using uncompleted  sources in my source list 
 
> almasry@almasry:~$ sudo apt-get install apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
apache2 is already the newest version.
The following packages were automatically installed and are no longer required:
  libdc1394-13 libxvidcore4 libjack0.100.0-0 libsqlite0 libxml++2.6c2a libsamplerate0 libgsm1 python-sqlite liblame0
  libfaac0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up egnome (0.cvs20020302-4) ...
Cannot find executable /usr/lib/smarteiffel/bin/selib2html
Cannot build HTML class documentation
dpkg: error processing egnome (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 egnome
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by almasry on 2007-03-03
I used " sudo apt-get autoremove "  to remove the uncompleted package , and the answer was :
> almasry@almasry:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdc1394-13 libxvidcore4 libjack0.100.0-0 libsqlite0 libxml++2.6c2a libsamplerate0 libgsm1 python-sqlite liblame0
  libfaac0
The following packages will be REMOVED
  libdc1394-13 libfaac0 libgsm1 libjack0.100.0-0 liblame0 libsamplerate0 libsqlite0 libxml++2.6c2a libxvidcore4
  python-sqlite
0 upgraded, 0 newly installed, 10 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 2966kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 115484 files and directories currently installed.)
Removing libdc1394-13 ...
Removing libfaac0 ...
Removing libgsm1 ...
Removing libjack0.100.0-0 ...
Removing liblame0 ...
Removing libsamplerate0 ...
Removing python-sqlite ...
Removing libsqlite0 ...
Removing libxml++2.6c2a ...
Removing libxvidcore4 ...
Setting up egnome (0.cvs20020302-4) ...
Cannot find executable /usr/lib/smarteiffel/bin/selib2html
Cannot build HTML class documentation
dpkg: error processing egnome (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 egnome
E: Sub-process /usr/bin/dpkg returned an error code (1)


---


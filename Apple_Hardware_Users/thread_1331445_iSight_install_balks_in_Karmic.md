---
title: "iSight install balks in Karmic"
date: 2009-11-19
forum: Apple Hardware Users
---

### Post by mdgill on 2009-11-19
I can't get isight-firmware-tools to install under 64-bit Karmic on a MacBook 4,1:

michael@michael-laptop:/media/MacOSX$ sudo apt-get purge isight-firmware-toolsReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  isight-firmware-tools*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 233kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 307684 files and directories currently installed.)
Removing isight-firmware-tools ...
Ignoring install-info called from maintainer script
The package isight-firmware-tools should be rebuild with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package isight-firmware-tools should be rebuild with new debhelper to get trigger support
Purging configuration files for isight-firmware-tools ...
Processing triggers for man-db ...
Processing triggers for install-info ...
install-info: warning: no info dir entry in `/usr/share/info/menu.info.gz'
Processing triggers for hal ...
Regenerating hal fdi cache ...
hal start/running, process 29104
michael@michael-laptop:/media/MacOSX$ sudo apt-get install isight-firmware-toolsReading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  isight-firmware-tools
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/34.5kB of archives.
After this operation, 233kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package isight-firmware-tools.
(Reading database ... 307667 files and directories currently installed.)
Unpacking isight-firmware-tools (from .../isight-firmware-tools_1.4.2-1_amd64.deb) ...
Processing triggers for hal ...
Regenerating hal fdi cache ...
hal start/running, process 29237
Processing triggers for install-info ...
install-info: warning: no info dir entry in `/usr/share/info/menu.info.gz'
Processing triggers for man-db ...
Setting up isight-firmware-tools (1.4.2-1) ...
dpkg: error processing isight-firmware-tools (--configure):
 subprocess installed post-installation script returned error exit status 134
Errors were encountered while processing:
 isight-firmware-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any other failures?  successes?

---

### Post by computer geek on 2010-02-26
I have the same problem, i wonder what is going on?

---

### Post by linuxopjemac on 2010-02-27
Does it matter if you remove/purge the package like this:

```
sudo apt-get --purge remove isight-firmware-tools
sudo apt-get install isight-firmware-tools
```

---

### Post by RockoTDF on 2010-03-07
I'm getting the exact same error.  

Tried the purge/reinstall stuff.  Didn't work.  Any more ideas?

---

### Post by albesan on 2010-03-15
Hey,

If you still have the MAC OSX partition make sure you have all the firmware updates and your MAC system up to date.
I was having the same problem, run the software update on the MAC side and it found a lot of updates that needed doing plus found some firmware updates on the Apple site.
After doing that I re-did the steps and it worked.

---

### Post by bkadoctaj on 2010-03-21
Check out this post:
[http://ubuntuforums.org/showthread.php?p=8832416#post8832416](http://ubuntuforums.org/showthread.php?p=8832416#post8832416)

---


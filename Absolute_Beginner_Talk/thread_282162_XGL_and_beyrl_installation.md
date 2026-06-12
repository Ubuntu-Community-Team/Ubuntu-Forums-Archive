---
title: "XGL and beyrl installation"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by Mr_Bond_UK on 2006-10-22
Could anyone give me a step by step guide to installing these two ive tried but with no sucess. Help!

---

### Post by Perfect Storm on 2006-10-22
[http://ubuntuforums.org/showthread.php?t=272104](http://ubuntuforums.org/showthread.php?t=272104)

---

### Post by Mr_Bond_UK on 2006-10-22
Did the set up as asked but there were a few problems i think. The termanal looked like this....

Fetched 19.0MB in 14m52s (21.3kB/s)
(Reading database ... 83807 files and directories currently installed.)
Preparing to replace libgl1-mesa-dri 6.4.1-0ubuntu8 (using .../libgl1-mesa-dri_6.5.1+cvs20060824_i386.deb) ...
Unpacking replacement libgl1-mesa-dri ...
Preparing to replace libgl1-mesa 6.4.1-0ubuntu8 (using .../libgl1-mesa_6.5.1+cvs20060824_i386.deb) ...
Unpacking replacement libgl1-mesa ...
Selecting previously deselected package beryl-core.
Unpacking beryl-core (from .../beryl-core_0.1.1-0ubuntu1_i386.deb) ...
Selecting previously deselected package beryl-plugins-data.
Unpacking beryl-plugins-data (from .../beryl-plugins-data_0.1.1-0ubuntu1_all.deb) ...
Selecting previously deselected package beryl-plugins.
Unpacking beryl-plugins (from .../beryl-plugins_0.1.1-0ubuntu1_i386.deb) ...
Selecting previously deselected package emerald.
Unpacking emerald (from .../emerald_0.1.1-0ubuntu1_i386.deb) ...
Selecting previously deselected package beryl-settings.
Unpacking beryl-settings (from .../beryl-settings_0.1.1-0ubuntu1_i386.deb) ...
Selecting previously deselected package beryl-manager.
Unpacking beryl-manager (from .../beryl-manager_0.1.1-0ubuntu2_i386.deb) ...
Selecting previously deselected package beryl.
Unpacking beryl (from .../beryl_0.1.1-0ubuntu1_i386.deb) ...
Selecting previously deselected package emerald-themes.
Unpacking emerald-themes (from .../emerald-themes_0.1.1-0ubuntu1_i386.deb) ...
Setting up clamav-base (0.88.4-1ubuntu1~dapper1) ...
chown: cannot access `/var/run/clamav': No such file or directory
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of clamav-freshclam:
 clamav-freshclam depends on clamav-base (= 0.88.4-1ubuntu1~dapper1); however:
  Package clamav-base is not configured yet.
dpkg: error processing clamav-freshclam (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of clamav:
 clamav depends on clamav-freshclam | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamav (--configure):
 dependency problems - leaving unconfigured
Setting up libgl1-mesa (6.5.1+cvs20060824) ...

Setting up libgl1-mesa-dri (6.5.1+cvs20060824) ...
Setting up beryl-core (0.1.1-0ubuntu1) ...
Setting up beryl-plugins-data (0.1.1-0ubuntu1) ...
Setting up beryl-plugins (0.1.1-0ubuntu1) ...
Setting up emerald (0.1.1-0ubuntu1) ...
***
* Updating MIME database in /usr/share/mime...
Wrote 478 strings at 20 - 27c4
Wrote aliases at 27c4 - 2970
Wrote parents at 2970 - 3330
Wrote literal globs at 3330 - 338c
Wrote suffix globs at 338c - 6784
Wrote full globs at 6784 - 67a8
Wrote magic at 67a8 - be2c
Wrote namespace list at be2c - be3c
***

Setting up beryl-settings (0.1.1-0ubuntu1) ...
Setting up beryl-manager (0.1.1-0ubuntu2) ...
Setting up beryl (0.1.1-0ubuntu1) ...
Setting up emerald-themes (0.1.1-0ubuntu1) ...
Errors were encountered while processing:
 clamav-base
 clamav-freshclam
 clamav
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up clamav-base (0.88.4-1ubuntu1~dapper1) ...
chown: cannot access `/var/run/clamav': No such file or directory
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of clamav-freshclam:
 clamav-freshclam depends on clamav-base (= 0.88.4-1ubuntu1~dapper1); however:
  Package clamav-base is not configured yet.
dpkg: error processing clamav-freshclam (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of clamav:
 clamav depends on clamav-freshclam | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamav (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 clamav-base
 clamav-freshclam
 clamav
 is that good?

---

### Post by bulldog on 2006-10-22
You have a problem with clamav not with Beryl or emerald.

---


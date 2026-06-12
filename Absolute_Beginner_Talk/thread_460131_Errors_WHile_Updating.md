---
title: "Errors WHile Updating"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by Supercross on 2007-05-31
I went to update my system because I was prompted and all of the updates downloaded fine but then when they were installing a lot of them experienced errors, stating dependency issues, as seen here:

```
E: capplets-data: subprocess post-installation script returned error exit status 139
E: gnome-control-center: dependency problems - leaving unconfigured
E: python2.5: subprocess post-installation script returned error exit status 139
E: python: dependency problems - leaving unconfigured
E: hwdb-client-common: dependency problems - leaving unconfigured
E: hwdb-client-gnome: dependency problems - leaving unconfigured
E: python-gdbm: dependency problems - leaving unconfigured
E: unattended-upgrades: dependency problems - leaving unconfigured
```

What do I need to allow these updates to install?

---

### Post by zvacet on 2007-05-31
```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by Supercross on 2007-05-31
I did that but it still doesn't work, I get the same errors in the console when it tries to reinstall the packages that failed before.  I get this message also:

```
(update-desktop-database:6815): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
```

---

### Post by Supercross on 2007-05-31
No one has a solution to this issue?

---

### Post by zvacet on 2007-06-13
[http://ubuntuforums.org/showthread.php?t=454759&highlight=segmentation]("http://ubuntuforums.org/showthread.php?t=454759&highlight=segmentation")

Ans sorry for late response.

---

### Post by Supercross on 2007-06-30
That didn't work. I still can barely update anything and I always gets this:

```
Setting up python2.5 (2.5.1-0ubuntu1) ...

(update-desktop-database:11114): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing python2.5 (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of python:
 python depends on python2.5 (>= 2.5.1); however:
  Package python2.5 is not configured yet.
dpkg: error processing python (--configure):
 dependency problems - leaving unconfigured
Setting up capplets-data (2.18.1-0ubuntu2.1) ...

(update-desktop-database:11131): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing capplets-data (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of gimp-python:
 gimp-python depends on python (>= 2.5); however:
  Package python is not configured yet.
 gimp-python depends on python (<< 2.6); however:
  Package python is not configured yet.
dpkg: error processing gimp-python (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gdbm:
 python-gdbm depends on python (<< 2.6); however:
  Package python is not configured yet.
 python-gdbm depends on python (>= 2.4); however:
  Package python is not configured yet.
dpkg: error processing python-gdbm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-app-install:
 gnome-app-install depends on python (>= 2.4); however:
  Package python is not configured yet.
 gnome-app-install depends on python-gdbm; however:
  Package python-gdbm is not configured yet.
dpkg: error processing gnome-app-install (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on capplets-data (>= 1:2.18); however:
  Package capplets-data is not configured yet.
 gnome-control-center depends on capplets-data (<< 1:2.19); however:
  Package capplets-data is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hwdb-client-common:
 hwdb-client-common depends on python; however:
  Package python is not configured yet.
dpkg: error processing hwdb-client-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hwdb-client-gnome:
 hwdb-client-gnome depends on hwdb-client-common (>= 0.6-0ubuntu23); however:
  Package hwdb-client-common is not configured yet.
dpkg: error processing hwdb-client-gnome (--configure):
 dependency problems - leaving unconfigured
Setting up python2.4 (2.4.4-2ubuntu7) ...

(update-desktop-database:11148): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)

```

---


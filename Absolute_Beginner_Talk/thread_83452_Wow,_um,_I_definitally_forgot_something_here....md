---
title: "Wow, um, I definitally forgot something here..."
date: 2005-10-28
forum: Absolute Beginner Talk
---

### Post by xequence on 2005-10-28
Well, I tried fedora core, and didnt like it. Now I am back in ubuntu, but I have a problem I think I had months ago when I just started:

> patrick@ubuntu:~$ sudo dpkg -i opera_8.50-20050916.6-shared-qt_en_etch_i386.deb
Selecting previously deselected package opera.
(Reading database ... 59183 files and directories currently installed.)
Unpacking opera (from opera_8.50-20050916.6-shared-qt_en_etch_i386.deb) ...
dpkg: dependency problems prevent configuration of opera:
 opera depends on libqt3-mt (>= 3.3.4) | libqt3c102-mt (>= 3.3.4); however:
  Package libqt3-mt is not installed.
  Package libqt3c102-mt is not installed.
dpkg: error processing opera (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 opera
patrick@ubuntu:~$



I am sure this is just some little stupid mistake by me, but ive been trying for awhile to get it working. I CANT believe this though, its so weird, using something for months and just now messing up on this.

---

### Post by stuporglue on 2005-10-28
> dpkg: dependency problems prevent configuration of opera:
opera depends on libqt3-mt (>= 3.3.4) | libqt3c102-mt (>= 3.3.4); however:
Package libqt3-mt is not installed.
Package libqt3c102-mt is not installed.

Have you tried to install those dependencies? ```

root@ubuntu:/home/stuporglue/# apt-cache search libqt3-mt
libqt3-mt - Qt GUI Library (Threaded runtime version), Version 3

```
It's in the repositories. Try installing it by running

$ sudo apt-get install libqt3-mt

Then, try the Opera install thing again.

---

### Post by darkmatter on 2005-10-28
> Package libqt3-mt is not installed.
Package libqt3c102-mt is not installed.

There is your problem. Install those libs and you'll be able to install opera.

---

### Post by xequence on 2005-10-28
Ok, thanks :) The same thing happened in fedora, but something to do with "local install" made it work ;)

---

### Post by Mustard on 2005-10-28
I was under the impression that those two versions of libqt conflict with each other.

---

### Post by xequence on 2005-10-29
I installed libqt3-mt and it automatically installed opera :)

---

### Post by kingsidy on 2005-10-30
THere is an easy solution. At the Opera website, download the package for Debian Etch. And do the dpkg -i *<package name>*. It worked for me. I ran into the same problem as you at the beginning and that is how I installed Opera 8.5.

---


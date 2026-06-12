---
title: "Error in Upgrade"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by rpainter on 2008-03-19
Not sure if this should go her or in the Hardy forum, but if it is wrong it will get moved.

As stated, I am running 8.04

I ran "sudo apt-get update", and then "sudo apt-get upgrade". It came back with the following:

```
The following packages have been kept back:
  insserv
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up python-wxgtk2.8 (2.8.7.1-0ubuntu2) ...
file does not exist: /usr/lib/python2.5/site-packages/wxaddons/__init__.py
file does not exist: /usr/lib/python2.5/site-packages/wxaddons/setup.py
file does not exist: /usr/lib/python2.5/site-packages/wxaddons/sized_controls.py
pycentral: pycentral pkginstall: error byte-compiling files (398)
pycentral pkginstall: error byte-compiling files (398)
dpkg: error processing python-wxgtk2.8 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 python-wxgtk2.8
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any idea how to fix this error? Or is it something to worry about?

---

### Post by ajmorris on 2008-03-19
yep, it belongs in the hardy sub forum, that is one of the many perks of running a beta linux :) I have the same problem on my hardy, im sure the issue will be rectified soon :)

---

### Post by overdrank on 2008-03-19
Hi and that is strange, I have no issues here :confused:

---


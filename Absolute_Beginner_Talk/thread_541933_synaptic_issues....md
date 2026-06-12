---
title: "synaptic issues..."
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by Blue_T0oth on 2007-09-03
after trying to install bitpim, whitch doesn't work quite right at the moment,...
the first time i tried installing it I got some wierd python-wxgtk2.6 error... don't member exact error right now, but the package manager hung and i had to reboot, got bitpim to install but with that and nething else i try to install now i get this error at the end of every installation i try

Setting up python-wxgtk2.6 (2.6.3.2.1.5ubuntu6) ...
Compiling /usr/lib/python2.5/site-packages/wx-2.6-gtk2-unicode/wx/lib/masked/timectrl.py ...
Sorry: TypeError: ('compile() expected string without null bytes',)
pycentral: pycentral pkginstall: error byte-compiling files (259)
pycentral pkginstall: error byte-compiling files (259)
dpkg: error processing python-wxgtk2.6 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 python-wxgtk2.6
E: Sub-process /usr/bin/dpkg returned an error code (1)

any sugestions??

---

### Post by diatribe on 2007-09-03
try sudo apt-get install -f

---

### Post by Blue_T0oth on 2007-09-03
just got this

E: Invalid operation install-f

ne other thoughts?

---

### Post by diatribe on 2007-09-03
you need to put a space between install and -f, sudo apt-get install -f

---

### Post by Blue_T0oth on 2007-09-03
E: Problem parsing dependency Depends
E: Error occurred while processing libavahi-common3 (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

not sure when this started... but trying to open synaptic i get this and it closes

---

### Post by diatribe on 2007-09-03
what version of ubuntu are you running

---

### Post by Blue_T0oth on 2007-09-03
get that same response using apt-get install -f in terminal aswell

---

### Post by Blue_T0oth on 2007-09-03
7.04 with all current updates

---

### Post by diatribe on 2007-09-03
try this site, it has a couple of fixes for people experiencing the same problem:

[http://www.linuxquestions.org/questions/showthread.php?t=155478](http://www.linuxquestions.org/questions/showthread.php?t=155478)

---

### Post by Blue_T0oth on 2007-09-03
that seems to have gotten me out of the hole a lill bit... now synap opens without errors, ran the install -f command and got this back

dpkg: parse error, in file `/var/lib/dpkg/available' near line 16680 package `update-notifier':
 `Depends' field, reference to `libgnomecanvas2-0': version contains ` '
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by diatribe on 2007-09-03
you need to edit this file:  `/var/lib/dpkg/available' around line 16680, that is where the problem lies.  looks like an invalid character is in that line

---


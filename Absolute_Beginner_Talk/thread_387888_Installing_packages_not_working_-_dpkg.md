---
title: "Installing packages not working - dpkg?"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by deadimp on 2007-03-18
For some reason, I'm no longer able to install debian packages using dpkg.
When using Synaptic to try and download fontforge:
```
(Reading database ... dpkg: error processing fontforge_0.0.20060703.1-1_i386.deb (--install):
 failed in buffer_read(fd): files list for package `gdb': Input/output error
Errors were encountered while processing:
 fontforge_0.0.20060703.1-1_i386.deb
Processing was halted because there were too many errors.
```
I've tried to use update-manager, but to no avail. I get a similar message on the first package it tries to install (I've already downloaded all of the packages).

(Had to recreate the commands in the terminal since I can't figure out how to copy the text in 'sub-termina' on the install window)

I remember there being something more about a lock file, and then ran into this error when using dselect:
```
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
```

Right now, I'm contemplating a reinstall of Ubuntu, since I've only had it on here for 2 months, and I haven't exactly customized it beyond replacement.

---

### Post by bruenig on 2007-03-18
> **deadimp said:**
> For some reason, I'm no longer able to install debian packages using dpkg.
When using Synaptic to try and download fontforge:
```
(Reading database ... dpkg: error processing fontforge_0.0.20060703.1-1_i386.deb (--install):
 failed in buffer_read(fd): files list for package `gdb': Input/output error
Errors were encountered while processing:
 fontforge_0.0.20060703.1-1_i386.deb
Processing was halted because there were too many errors.
```
I've tried to use update-manager, but to no avail. I get a similar message on the first package it tries to install (I've already downloaded all of the packages).

(Had to recreate the commands in the terminal since I can't figure out how to copy the text in 'sub-termina' on the install window)

I remember there being something more about a lock file, and then ran into this error when using dselect:
```
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
```

Right now, I'm contemplating a reinstall of Ubuntu, since I've only had it on here for 2 months, and I haven't exactly customized it beyond replacement.

The first problem could be an issue with that package. Try installing another deb and see if you get the same problem. The second error just means that you have more than one package manager open at once. So if you have the update-manger on and then try to use apt-get or something, you will get that.

---

### Post by user1397 on 2007-03-18
> **deadimp said:**
> For some reason, I'm no longer able to install debian packages using dpkg.
When using Synaptic to try and download fontforge:
```
(Reading database ... dpkg: error processing fontforge_0.0.20060703.1-1_i386.deb (--install):
 failed in buffer_read(fd): files list for package `gdb': Input/output error
Errors were encountered while processing:
 fontforge_0.0.20060703.1-1_i386.deb
Processing was halted because there were too many errors.
```I've tried to use update-manager, but to no avail. I get a similar message on the first package it tries to install (I've already downloaded all of the packages).

(Had to recreate the commands in the terminal since I can't figure out how to copy the text in 'sub-termina' on the install window)

I remember there being something more about a lock file, and then ran into this error when using dselect:
```
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
```Right now, I'm contemplating a reinstall of Ubuntu, since I've only had it on here for 2 months, and I haven't exactly customized it beyond replacement.are you running the 64 bit version of ubuntu?  that deb package seems to be an i386 package, not 64.

also the second error message, like bruenig said, that just means that you have 2 or more applications or instances of apt/aptitude running.  (for example, having the update-manager while having synaptic open, or having the add/remove application while using apt-get in the terminal).  You can only have one instance running at a time.

---

### Post by deadimp on 2007-03-19
Well, I decided to reinstall Ubuntu, or rather, install Xubuntu instead, just to get a feel of the differences and such, which is better suited.

Thanks for the help!

---


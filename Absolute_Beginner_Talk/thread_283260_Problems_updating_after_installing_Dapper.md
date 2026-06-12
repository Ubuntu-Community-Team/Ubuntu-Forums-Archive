---
title: "Problems updating after installing Dapper"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by geyerba on 2006-10-23
I finally got Dapper installed on my HP Laptop and managed to get the wireless going by disabling WEP.  However, I still have a little icon in the upper right corner which says "An error has occurred... " when I hover over it.  I try to fix the broken package by using synaptics and also from the command line.  However, this is what I get when I execute the following: sudo apt-get install -f


(Reading database ... 68697 files and directories currently installed.)
Unpacking slocate (from .../slocate_3.0.beta.r3-1_i386.deb) ...
Removing `diversion of /etc/cron.daily/find to /etc/cron.daily/find.notslocate by slocate'
dpkg-divert: rename involves overwriting `/etc/cron.daily/find' with
  different file `/etc/cron.daily/find.notslocate', not allowed
dpkg: error processing /cdrom//pool/main/s/slocate/slocate_3.0.beta.r3-1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /cdrom//pool/main/s/slocate/slocate_3.0.beta.r3-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any ideas at all?

Synaptic doesn't do any better.
Thanks for any help,
Ben

---

### Post by dmizer on 2006-10-24
use aptitude instead of apt-get.  it will give you choices on what to do, or more information on what is wrong and what to do about it.

looks like your broken package is slocate.

try this:
```
sudo aptitude update
sudo aptitude install -f slocate
```
let me know what that does.

---

### Post by geyerba on 2006-10-27
dmizer, thx for the feedback.  I tried what you suggested, but still have problems.  I'm wondering if it might be the cd?  I'll omit the results of the first command.  No problems there.  However, here's the error:

```
dad@ubuntu:~$ sudo aptitude install -f slocate
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be installed:
  slocate
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/30.1kB of archives. After unpacking 156kB will be used.
Writing extended state information... Done
(Reading database ... 68697 files and directories currently installed.)
Unpacking slocate (from .../slocate_3.0.beta.r3-1_i386.deb) ...
Removing `diversion of /etc/cron.daily/find to /etc/cron.daily/find.notslocate by slocate'
dpkg-divert: rename involves overwriting `/etc/cron.daily/find' with
  different file `/etc/cron.daily/find.notslocate', not allowed
dpkg: error processing /cdrom//pool/main/s/slocate/slocate_3.0.beta.r3-1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /cdrom//pool/main/s/slocate/slocate_3.0.beta.r3-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on slocate; however:
  Package slocate is not installed.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ubuntu-desktop

```

Any help is appreciated as always.

Ben

---

### Post by geyerba on 2006-10-27
I think I actually have a workable solution from another similar thread dealing with slocate.  Course, this is kinda a scary solution since I didn't really know what slocate does, so I was taking a bit of a chance.  Anyway, here it is:

```
sudo rm /etc/cron.daily/find
sudo dpkg-divert --rename --remove /etc/cron.daily/find
```

Now to upgrade to 6.10!

---


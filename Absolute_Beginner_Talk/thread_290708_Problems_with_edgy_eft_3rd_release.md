---
title: "Problems with edgy eft 3rd release"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by Norman Thom on 2006-11-01
I'm having some problems with Edgy Eft and would like to hear some solutions. Recently on my daily updates I get a warning that all updates may not be installed and a request to do a 'distribution update'.  I do it but should this be necessary?  Also I can't get a couple of programs working sp. Azureus. Then suddenly a couple of days ago it was suggested that I could not run Synaptic as I did not have a public key? 

Would it be possible to upgrade to the latest release ( the full release ) from this version to correct this and if so how?

Slainthe,

Norm

---

### Post by PriceChild on 2006-11-01
If you installed off of knot3,```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```Will get you to final.

After this try azureus again. If it still doesn't work, type "azureus" into a terminal and tell us what comes out.

---

### Post by Norman Thom on 2006-11-01
Thanks Price.  Seems like that solution did someting but here is part of th message I got:

Reading package lists... Done
W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
W: You may want to run apt-get update to correct these problems
ellysium@ellysium-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ellysium@ellysium-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  startup-tasks system-services ubuntu-minimal upstart upstart-compat-sysv
  upstart-logd
The following NEW packages will be installed:
  sysvinit
0 upgraded, 1 newly installed, 6 to remove and 0 not upgraded.
Need to get 109kB of archives.
After unpacking 438kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main sysvinit 2.86.ds1-14.1ubuntu16 [109kB]
Fetched 109kB in 0s (291kB/s)
(Reading database ... 174969 files and directories currently installed.)
Removing ubuntu-minimal ...
Removing startup-tasks ...
Removing system-services ...
Removing upstart-logd ...
Removing upstart-compat-sysv ...
Removing upstart ...
Selecting previously deselected package sysvinit.
(Reading database ... 174927 files and directories currently installed.)
Unpacking sysvinit (from .../sysvinit_2.86.ds1-14.1ubuntu16_i386.deb) ...
Setting up sysvinit (2.86.ds1-14.1ubuntu16) ...
init: timeout opening/writing control channel /dev/initctl

ellysium@ellysium-desktop:~$

---

### Post by John.Michael.Kane on 2006-11-01
Make sure you sources.list only has edgy repos.

Remove this from your sources list.
[http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: 

and try PriceChild method again. 

Clean install may be your best bet. back up your data your xorg config,and install that way.

---


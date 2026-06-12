---
title: "Error when trying to install ClamAV, AVScan and F-Prot"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by Duffadash on 2007-05-10
Just tried to install various anti-virus programs, but for some reason I got an error, not sure if I should ignore it or not, but here it is, any suggestions?:

```
E: clamav-base: subprocess post-installation script returned error exit status 1
E: clamav-freshclam: dependency problems - leaving unconfigured
E: avscan: dependency problems - leaving unconfigured
E: clamav: dependency problems - leaving unconfigured
E: clamav-daemon: dependency problems - leaving unconfigured
E: clamav-getfiles: dependency problems - leaving unconfigured
E: f-prot-installer: subprocess post-installation script returned error exit status 1
```

BTW, I'm running Feisty Ubuntu 7.04 with Gnome, and tried to install the packages using Synaptic Package Manager.

Edit:

Seems to do it with everything, Update Manager this time:
```
E: f-prot-installer: subprocess post-installation script returned error exit status 1
E: python2.5: subprocess post-installation script killed by signal (Interrupt)
E: python: dependency problems - leaving unconfigured
E: update-manager-core: dependency problems - leaving unconfigured
E: python-gdbm: dependency problems - leaving unconfigured
E: gnome-app-install: dependency problems - leaving unconfigured
E: hwdb-client-common: dependency problems - leaving unconfigured
E: hwdb-client-gnome: dependency problems - leaving unconfigured
E: unattended-upgrades: dependency problems - leaving unconfigured
E: update-manager: dependency problems - leaving unconfigured
```

---

### Post by phansiizwe on 2007-05-10
Please open Synaptic and in the bottom left, press the button labeled 'Custom Filters'. Then select 'Broken' on the left (above the buttons). Are there any broken packages listed there?

---

### Post by Duffadash on 2007-05-10
Nope, no broken packages.

---

### Post by Najand on 2007-05-10
Have you enabled the "Universe" and "Multiverse" repositories? Have you tried to reloas the packages list (or "apt-get update") before trying to install?

---

### Post by phansiizwe on 2007-05-10
I just tried installing clamav and it returned an error for me as well.

Some more info below...

I will try to install again, specifically selecting clamav-base as well.

```
Preconfiguring packages ...
Selecting previously deselected package libgmp3c2.
(Reading database ... 94303 files and directories currently installed.)
Unpacking libgmp3c2 (from .../libgmp3c2_2%3a4.2.1+dfsg-4build1_i386.deb) ...
Selecting previously deselected package libclamav2.
Unpacking libclamav2 (from .../libclamav2_0.90.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package clamav-base.
Unpacking clamav-base (from .../clamav-base_0.90.2-0ubuntu1_all.deb) ...
Selecting previously deselected package clamav-freshclam.
Unpacking clamav-freshclam (from .../clamav-freshclam_0.90.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package clamav.
Unpacking clamav (from .../clamav_0.90.2-0ubuntu1_i386.deb) ...
Setting up libgmp3c2 (4.2.1+dfsg-4build1) ...

Setting up libclamav2 (0.90.2-0ubuntu1) ...

Setting up clamav-base (0.90.2-0ubuntu1) ...
Adding system user `clamav' (UID 110) ...
Adding new group `clamav' (GID 119) ...
Adding new user `clamav' (UID 110) with group `clamav' ...
Not creating home directory `/var/lib/clamav'.
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of clamav-freshclam:
 clamav-freshclam depends on clamav-base (>= 0.90.2-0ubuntu1); however:
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
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up clamav-base (0.90.2-0ubuntu1) ...

Setting up clamav-freshclam (0.90.2-0ubuntu1) ...
 * Starting ClamAV virus database updater freshclam
   ...done.

Setting up clamav (0.90.2-0ubuntu1) ...


```

---

### Post by Najand on 2007-05-10
Seems there are some packages (dependencies) are not updated. Please wait and try to update tomorrow again.

---

### Post by phansiizwe on 2007-05-10
This bug was reported on launchpad a pretty long while ago...

[https://bugs.launchpad.net/ubuntu/+source/clamav/+bug/39853](https://bugs.launchpad.net/ubuntu/+source/clamav/+bug/39853)

---

### Post by Najand on 2007-05-10
Anyway, you don't need any antivirus softwares unless you have ubuntu as your server and you want to protect windows machines in your network.
[http://ubuntuforums.org/showthread.php?t=5875](http://ubuntuforums.org/showthread.php?t=5875)

---

### Post by Duffadash on 2007-05-10
I know, I was just told that some of the windows executables I'd downloaded for a reind contained some viruses or something and wanted to check them myself.
I'll try to play around with it again tomorrow or something. Now, sleep.

---

### Post by BadSquishy on 2007-05-12
At first I ran into this same exact problem.  Unfortunately I was unable to copy the text of the failure as phansiizwe did because I was using cygwin and ssh to work on the Ubuntu box from a Windows box.  The dpkg errors looked exactly the same, but I do not know if it was attempting to install version 0.90.2 of clamav when it failed as it is for phansiizwe (I'm using Ubuntu Server Edition 6.06 LTS).  

Well, after it failed I logged off of ssh and rebooted the machine into Gentoo so I could copy and paste text from gnome terminal.  I ssh'd back into the Ubuntu Server 6.06 machine and ran the following command to removed all of the packages that had been installed on the failed attempt.
```

dave@tester:~$ sudo aptitude purge clamav

```
Then (this is about an hour after I first saw the failed install) I re-installed with aptitude so I could copy and paste my version of the error into this thread (and a bug report if need be) and it didn't throw any errors! Here's the output:
```

dave@tester:~$ sudo aptitude install clamav
Reading package lists... Done
Building dependency tree... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  arj clamav-base clamav-freshclam debconf-utils libclamav1 libcurl3 libgmp3c2 libidn11 ucf unzoo 
The following packages have been kept back:
  linux-image-server 
The following NEW packages will be installed:
  arj clamav clamav-base clamav-freshclam debconf-utils libclamav1 libcurl3 libgmp3c2 libidn11 ucf unzoo 
0 packages upgraded, 11 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/7297kB of archives. After unpacking 9355kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Preconfiguring packages ...
Selecting previously deselected package arj.
(Reading database ... 16614 files and directories currently installed.)
Unpacking arj (from .../arj_3.10.22-2_i386.deb) ...
Selecting previously deselected package libidn11.
Unpacking libidn11 (from .../libidn11_0.5.18-1_i386.deb) ...
Selecting previously deselected package libcurl3.
Unpacking libcurl3 (from .../libcurl3_7.15.1-1ubuntu2_i386.deb) ...
Selecting previously deselected package libgmp3c2.
Unpacking libgmp3c2 (from .../libgmp3c2_4.1.4-11ubuntu2_i386.deb) ...
Selecting previously deselected package libclamav1.
Unpacking libclamav1 (from .../libclamav1_0.88.4-1ubuntu1~dapper1_i386.deb) ...
Selecting previously deselected package ucf.
Unpacking ucf (from .../main/u/ucf/ucf_2.004_all.deb) ...
Moving old data out of the way
Selecting previously deselected package clamav-base.
Unpacking clamav-base (from .../clamav-base_0.88.4-1ubuntu1~dapper1_all.deb) ...
Selecting previously deselected package clamav-freshclam.
Unpacking clamav-freshclam (from .../clamav-freshclam_0.88.4-1ubuntu1~dapper1_i386.deb) ...
Selecting previously deselected package clamav.
Unpacking clamav (from .../clamav_0.88.4-1ubuntu1~dapper1_i386.deb) ...
Selecting previously deselected package debconf-utils.
Unpacking debconf-utils (from .../debconf-utils_1.4.72ubuntu9_all.deb) ...
Selecting previously deselected package unzoo.
Unpacking unzoo (from .../archives/unzoo_4.4-4_i386.deb) ...
Setting up arj (3.10.22-2) ...
Setting up libidn11 (0.5.18-1) ...

Setting up libcurl3 (7.15.1-1ubuntu2) ...

Setting up libgmp3c2 (4.1.4-11ubuntu2) ...

Setting up libclamav1 (0.88.4-1ubuntu1~dapper1) ...

Setting up ucf (2.004) ...

Setting up clamav-base (0.88.4-1ubuntu1~dapper1) ...
Replacing config file /etc/clamav/clamd.conf with new version

Setting up clamav-freshclam (0.88.4-1ubuntu1~dapper1) ...
 * Starting ClamAV virus database updater freshclam                                                                                                   [ ok ] 

Setting up clamav (0.88.4-1ubuntu1~dapper1) ...
Setting up debconf-utils (1.4.72ubuntu9) ...

Setting up unzoo (4.4-4) ...
dave@tester:~$

```

It appears to have properly installed clamav 0.88.4
Well, we'll see if the test rig virus scanning works before I role it out at the office.  

Regards,

---

### Post by terabite on 2007-05-14
Try to configure the packages again. I had a similar problem. I configured the packages again. Its working fine now.

```

sudo dpkg --configure -a

```

---


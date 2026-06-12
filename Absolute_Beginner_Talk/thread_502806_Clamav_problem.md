---
title: "Clamav problem"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by corowakid on 2007-07-17
I downloaded and installed (at least I thought I did!) via Add/Remove programs. I keep getting an error message whenever I download updates as follows:

E: clamav-base: subprocess post-installation script returned error exit status 1

E: clamav-freshclam: dependency problems-leaving unconfigured

Can anyone enlighten me as to what has gone wrong, and more importantly, how to fix things? I'm prepared to lost Clamav, but again, I don't know how to do it. When I go to Add/Remove programs and search for Clamav I get a blank.

I'd appreciate any help. Thanks

---

### Post by corowakid on 2007-07-17
well I followed a process from another post about this subject, and here's what I got:

barrie@barrie:~$ sudo apt-get remove clamav base
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package clamav is not installed, so not removed
Note, selecting base-files instead of base
The following packages will be REMOVED:
  base-files bash foomatic-db-engine foomatic-db-hpijs foomatic-filters
  libnss-mdns ubuntu-desktop ubuntu-minimal
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  base-files bash
0 upgraded, 0 newly installed, 8 to remove and 3 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 9187kB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?] Yes, do as I say!
(Reading database ... 105798 files and directories currently installed.)
Removing ubuntu-minimal ...
Removing ubuntu-desktop ...
Removing libnss-mdns ...
Checking NSS setup...
Removing foomatic-db-hpijs ...
Removing foomatic-db-engine ...
Removing foomatic-filters ...
dpkg - warning, overriding problem because --force enabled:
 This is an essential package - it should not be removed.
Removing bash ...
dpkg - warning, overriding problem because --force enabled:
 This is an essential package - it should not be removed.
Removing base-files ...
dpkg - warning: while removing base-files, unable to remove directory `/var/lock': Device or resource busy - directory may be a mount point ?
dpkg - warning: while removing base-files, unable to remove directory `/proc': Device or resource busy - directory may be a mount point ?
dpkg - warning: while removing base-files, unable to remove directory `/home': Device or resource busy - directory may be a mount point ?
Setting up clamav-base (0.90.2-0ubuntu1.2) ...
chown: cannot access `/var/run/clamav': No such file or directory
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of clamav-freshclam:
 clamav-freshclam depends on clamav-base (>= 0.90.2-0ubuntu1.2); however:
  Package clamav-base is not configured yet.
dpkg: error processing clamav-freshclam (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 clamav-base

From all this, can anyone suggest what I've done wrong, and how to fix it. I do know that I didn't use the apt-get install process, which is probably the cause of the problem (?). Thanks for any advice.

---

### Post by bcom on 2007-07-17
The easiest way to install ClamAV is to do it through System - Administration - Synaptic package manager.  Make sure you have the proper repository enabled, i.e., Community-maintained Open software (universe).

Alternatively, you can do this using Terminal (assuming you have enabled the aforementioned repository):

Open up a Terminal Session
Because you have already had some problems, type: sudo apt-get -f install
Next, type: sudo apt-get install clamav; this command should install the command-line version of clamAV.

---


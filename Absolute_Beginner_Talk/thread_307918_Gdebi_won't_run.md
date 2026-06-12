---
title: "Gdebi won't run"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by usersock on 2006-11-27
This started out as a different problem, but I think python is my main problem.

I've been having problems running several applications. Each error message included "python2.4-minimal" 

*example: E: python2.4-minimal: subprocess post-installation script returned error exit status 139*

After installing Ubuntu 6.6 and running the updates there was an error for python2.4-minimal. I used the following code hoping it would rerun the update manager (I cant get it to run from the system menu or terminal).

```
sudo dpkg --configure -a

sudo apt-get clean

sudo apt-get dist-upgrade
```

It didn't seem to fix the python problem.

> 
:~$ sudo dpkg --configure -a
Password:
Setting up python2.4-minimal (2.4.3-0ubuntu6) ...
Compiling python modules in /usr/lib/python2.4 ...
/var/lib/dpkg/info/python2.4-minimal.postinst: line 8:  6534 Segmentation fault      /usr/bin/python2.4 /usr/lib/python2.4/compileall.py -q $i
dpkg: error processing python2.4-minimal (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of python2.4:
 python2.4 depends on python2.4-minimal (= 2.4.3-0ubuntu6); however:
  Package python2.4-minimal is not configured yet.
dpkg: error processing python2.4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python2.4-gdbm:
 python2.4-gdbm depends on python2.4 (= 2.4.3-0ubuntu6); however:
  Package python2.4 is not configured yet.
dpkg: error processing python2.4-gdbm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python2.4-tk:
 python2.4-tk depends on python2.4 (= 2.4.3-0ubuntu6); however:
  Package python2.4 is not configured yet.
dpkg: error processing python2.4-tk (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python2.4-minimal
 python2.4
 python2.4-gdbm
 python2.4-tk
:~$ sudo apt-get clean
:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-image-2.6.15-27-386 linux-restricted-modules-2.6.15-27-386
The following packages will be upgraded:
  bind9-host cpio dnsutils dselect firefox firefox-gnome-support gdb hal
  hal-device-manager info libavahi-client3 libavahi-common-data
  libavahi-common3 libavahi-glib1 libbind9-0 libdns21 libgnutls12
  libhal-storage1 libhal1 libisc11 libisccc0 libisccfg1 libkrb53 liblwres9
  libmagick9 libmusicbrainz4c2a libmysqlclient15off libnspr4 libnss3
  libpng12-0 libpq4 libwmf0.2-7 libxfont1 linux-386 linux-image-2.6.15-26-386
  linux-image-386 linux-restricted-modules-2.6.15-26-386
  linux-restricted-modules-386 linux-restricted-modules-common mysql-common
  openssh-client openssl python2.4-examples ssh-askpass-gnome xinit
  xserver-xorg-core
46 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 83.9MB of archives.
After unpacking 84.5MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libgnutls12 1.2.9-2ubuntu1.1 [373kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main cpio 2.6-10ubuntu0.2 [94.0kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main dselect 1.13.11ubuntu7 [117kB]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libisc11 1:9.3.2-2ubuntu1.1 [172kB]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libdns21 1:9.3.2-2ubuntu1.1 [478kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libhal1 0.5.7-1ubuntu18.2 [158kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libisccc0 1:9.3.2-2ubuntu1.1 [90.4kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libisccfg1 1:9.3.2-2ubuntu1.1 [102kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libbind9-0 1:9.3.2-2ubuntu1.1 [91.0kB]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main liblwres9 1:9.3.2-2ubuntu1.1 [107kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main bind9-host 1:9.3.2-2ubuntu1.1 [108kB]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main dnsutils 1:9.3.2-2ubuntu1.1 [175kB]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main hal 0.5.7-1ubuntu18.2 [336kB]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main info 4.8-4ubuntu0.1 [214kB]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libkrb53 1.4.3-5ubuntu0.1 [380kB]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main openssh-client 1:4.2p1-7ubuntu3.1 [537kB]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main firefox-gnome-support 1.5.dfsg+1.5.0.8-0ubuntu0.6.06 [75.1kB]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libpng12-0 1.2.8rel-5ubuntu0.1 [111kB]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libnspr4 2:1.firefox1.5.dfsg+1.5.0.8-0ubuntu0.6.06 [147kB]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libnss3 2:1.firefox1.5.dfsg+1.5.0.8-0ubuntu0.6.06 [670kB]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main hal-device-manager 0.5.7-1ubuntu18.2 [215kB]
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main firefox 1.5.dfsg+1.5.0.8-0ubuntu0.6.06 [7932kB]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main libhal-storage1 0.5.7-1ubuntu18.2 [159kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main xserver-xorg-core 1:1.0.2-0ubuntu10.4 [3531kB]
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main gdb 6.4-1ubuntu5.1 [2701kB]
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libavahi-common-data 0.6.10-0ubuntu3.2 [17.6kB]
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libavahi-common3 0.6.10-0ubuntu3.2 [32.7kB]
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libavahi-client3 0.6.10-0ubuntu3.2 [37.6kB]
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libavahi-glib1 0.6.10-0ubuntu3.2 [19.8kB]
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libmagick9 6:6.2.4.5-0.6ubuntu0.3 [1247kB]
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libmusicbrainz4c2a 2.1.2-2ubuntu3.1 [85.8kB]
Get:32 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main mysql-common 5.0.22-0ubuntu6.06.2 [39.4kB]
Get:33 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libmysqlclient15off 5.0.22-0ubuntu6.06.2 [1382kB]
Get:34 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libpq4 8.1.4-0ubuntu1.1 [199kB]
Get:35 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libwmf0.2-7 0.2.8.3-3.1ubuntu0.1 [167kB]
Get:36 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libxfont1 1:1.0.0-0ubuntu3.2 [216kB]
Get:37 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main linux-image-2.6.15-27-386 2.6.15-27.48 [21.7MB]
Get:38 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main linux-image-386 2.6.15.25 [23.4kB]
Get:39 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted linux-restricted-modules-common 2.6.15.12-1 [18.0kB]
Get:40 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted linux-restricted-modules-2.6.15-27-386 2.6.15.12-1 [8139kB]
Get:41 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted linux-restricted-modules-386 2.6.15.25 [23.4kB]
Get:42 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted linux-386 2.6.15.25 [23.4kB]
Get:43 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main linux-image-2.6.15-26-386 2.6.15-26.47 [21.7MB]
Get:44 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted linux-restricted-modules-2.6.15-26-386 2.6.15.11-4 [8138kB]
Get:45 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main openssl 0.9.8a-7ubuntu0.3 [976kB]
Get:46 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main python2.4-examples 2.4.3-0ubuntu6 [587kB]
Get:47 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main ssh-askpass-gnome 1:4.2p1-7ubuntu3.1 [86.5kB]
Get:48 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main xinit 1.0.1-0ubuntu3.1 [26.8kB]
Fetched 83.9MB in 1m40s (838kB/s)
Extracting templates from packages: 100%
Setting up python2.4-minimal (2.4.3-0ubuntu6) ...
Compiling python modules in /usr/lib/python2.4 ...
/var/lib/dpkg/info/python2.4-minimal.postinst: line 8:  6649 Segmentation fault      /usr/bin/python2.4 /usr/lib/python2.4/compileall.py -q $i
dpkg: error processing python2.4-minimal (--configure):
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 python2.4-minimal
E: Sub-process /usr/bin/dpkg returned an error code (1)


---


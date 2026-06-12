---
title: "Bug in Totem 1.1.1/Totem-Xine 1.1.1"
date: 2005-08-14
forum: Bug Reports / Support
---

### Post by Kyral on 2005-08-14
Since Totem 1.1.3 wasn't working, I uninstalled it and reinstalled. However, when I try to install Totem-Xine, I get this

 ```
kyral@ArcadianUbuntu:~$ aptI totem-xine
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  totem-xine
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1031kB of archives.
After unpacking 3879kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  totem-xine
Install these packages without verification [y/N]? y

Preconfiguring packages ...
(Reading database ... 86660 files and directories currently installed.)
Unpacking totem-xine (from .../totem-xine_1.1.1-0ubuntu3~5.04ubp1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/totem-xine_1.1.1-0ubuntu3~5.04ubp1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libtotem-plparser.so.0', which is also in package libtotem-plparser0
Errors were encountered while processing:
 /var/cache/apt/archives/totem-xine_1.1.1-0ubuntu3~5.04ubp1_i386.deb
Running prelink, please wait...
E: Sub-process /usr/bin/dpkg returned an error code (1)

``` 

Anyone know what it up?

---

### Post by Darrena on 2005-08-20
[QUOTE=Kyral]Since Totem 1.1.3 wasn't working, I uninstalled it and reinstalled. However, when I try to install Totem-Xine, I get this

 ```
kyral@ArcadianUbuntu:~$ aptI totem-xine
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  totem-xine
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1031kB of archives.
After unpacking 3879kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  totem-xine
Install these packages without verification [y/N]? y

Preconfiguring packages ...
(Reading database ... 86660 files and directories currently installed.)
Unpacking totem-xine (from .../totem-xine_1.1.1-0ubuntu3~5.04ubp1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/totem-xine_1.1.1-0ubuntu3~5.04ubp1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libtotem-plparser.so.0', which is also in package libtotem-plparser0
Errors were encountered while processing:
 /var/cache/apt/archives/totem-xine_1.1.1-0ubuntu3~5.04ubp1_i386.deb
Running prelink, please wait...
E: Sub-process /usr/bin/dpkg returned an error code (1)

``` 

Anyone know what it up?[/QUOTE]
 It looks like you have a newer version of libtotem-plparserdev that does not match the totem version you are using, search in synaptic for it remove it and reinstall the latest version.  I don't think you need that package for totem anyway so you may be able to remove it completely.

---


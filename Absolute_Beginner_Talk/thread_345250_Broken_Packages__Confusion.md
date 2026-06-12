---
title: "Broken Packages  Confusion"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by marx2k on 2007-01-24
So I was playing around with DCLib and installed an alien'd version of it... now here is my problem:
```

marx2k@Commodore-64:~/Desktop$ sudo aptitude install valknut
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  libdc0c2 
The following NEW packages will be installed:
  libdc0c2 valknut 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 1135kB of archives. After unpacking 3801kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 http://archive.ubuntu.com edgy/universe libdc0c2 0.3.7-3 [251kB]
Get:2 http://archive.ubuntu.com edgy/universe valknut 0.3.7-2.1ubuntu1 [884kB]
Fetched 1135kB in 2s (403kB/s)  
(Reading database ... 125979 files and directories currently installed.)
Unpacking libdc0c2 (from .../libdc0c2_0.3.7-3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libdc0c2_0.3.7-3_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libdc.so.0.0.1', which is also in package dclib
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Selecting previously deselected package valknut.
Unpacking valknut (from .../valknut_0.3.7-2.1ubuntu1_i386.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libdc0c2_0.3.7-3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of valknut:
 valknut depends on libdc0c2 (<< 0.3.7-99); however:
  Package libdc0c2 is not installed.
 valknut depends on libdc0c2 (>= 0.3.7-0); however:
  Package libdc0c2 is not installed.
dpkg: error processing valknut (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 valknut

```

Ok.. so lets try removing dclib...

```

marx2k@Commodore-64:~/Desktop$ sudo aptitude remove dclib
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  valknut 
The following packages will be REMOVED:
  dclib 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 1942kB will be freed.
The following packages have unmet dependencies:
  valknut: Depends: libdc0c2 (< 0.3.7-99) but it is not installable
           Depends: libdc0c2 (>= 0.3.7-0) but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
libdc0c2 [0.3.7-3 (edgy, now)]

Score is -19

Accept this solution? [Y/n/q/?] y
The following NEW packages will be automatically installed:
  libdc0c2 
The following NEW packages will be installed:
  libdc0c2 
The following packages will be REMOVED:
  dclib 
0 packages upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B/251kB of archives. After unpacking 1253kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 126106 files and directories currently installed.)
Unpacking libdc0c2 (from .../libdc0c2_0.3.7-3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libdc0c2_0.3.7-3_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libdc.so.0.0.1', which is also in package dclib
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libdc0c2_0.3.7-3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of valknut:
 valknut depends on libdc0c2 (<< 0.3.7-99); however:
  Package libdc0c2 is not installed.
 valknut depends on libdc0c2 (>= 0.3.7-0); however:
  Package libdc0c2 is not installed.
dpkg: error processing valknut (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 valknut

```
:confused: 
Ok so let's try the other option...
```

Accept this solution? [Y/n/q/?] n
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
valknut

Score is -301

Accept this solution? [Y/n/q/?] y

The following packages will be automatically REMOVED:
  valknut 
The following packages will be REMOVED:
  dclib valknut 
0 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 5054kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 126105 files and directories currently installed.)
Removing valknut ...
Removing dclib ...

```

Ok, so... so far so good, right?

So now lets try installing valknut again...
```

marx2k@Commodore-64:~/Desktop$ sudo aptitude install valknut
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  libdc0c2 
The following NEW packages will be installed:
  libdc0c2 valknut 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1135kB of archives. After unpacking 3801kB will be used.
Do you want to continue? [Y/n/?] y

Writing extended state information... Done
(Reading database ... 125964 files and directories currently installed.)
Unpacking libdc0c2 (from .../libdc0c2_0.3.7-3_i386.deb) ...
Selecting previously deselected package valknut.
Unpacking valknut (from .../valknut_0.3.7-2.1ubuntu1_i386.deb) ...
Setting up libdc0c2 (0.3.7-3) ...

Setting up valknut (0.3.7-2.1ubuntu1) ...

marx2k@Commodore-64:~/Desktop$ 

```

And it works.  So.... can someone tell me exactly what happened here?

---


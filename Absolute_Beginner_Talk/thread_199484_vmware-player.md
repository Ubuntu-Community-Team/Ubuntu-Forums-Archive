---
title: "vmware-player"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by OrganicPanda on 2006-06-18
hey all ( again i find myself posting in this forum because i dont know where else to post ).

I am trying to install vmware via apt-get and all i'm getting is:

```

panda@panda-desktop:~$ sudo apt-get install vmware-player
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed
  vmware-player
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/11.8MB of archives.
After unpacking 32.0MB of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 84885 files and directories currently installed.)
Unpacking vmware-player (from .../vmware-player_1.0.1-4_i386.deb) ...
 license could not be presented; aborting
dpkg: error processing /var/cache/apt/archives/vmware-player_1.0.1-4_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
***
* Updating MIME database in /usr/share/mime...
Wrote 477 strings at 20 - 27a8
Wrote aliases at 27a8 - 2954
Wrote parents at 2954 - 3304
Wrote literal globs at 3304 - 3360
Wrote suffix globs at 3360 - 6728
Wrote full globs at 6728 - 674c
Wrote magic at 674c - bd98
Wrote namespace list at bd98 - bda8
***
Errors were encountered while processing:
 /var/cache/apt/archives/vmware-player_1.0.1-4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
panda@panda-desktop:~$        

```

any ideas?

---

### Post by OrganicPanda on 2006-06-20
bumpidy bump bump, sorry but installing something via apt should be simple

---


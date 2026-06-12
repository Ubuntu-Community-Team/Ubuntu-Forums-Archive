---
title: "System updates won't install"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by phoenix23 on 2007-10-14
This compiz update has been in my update box for a couple of weeks now. It will never install, and from the description, it doesn't look like it even is anything.

What do I do?

---

### Post by [S|G] on 2007-10-15
Can you try installing it on the command line and posting the output here? To do that , open a terminal and type:
```
$sudo apt-get install compiz-core
```

---

### Post by phoenix23 on 2007-10-15
Thanks for the response

> stephen@stephen-desktop:~$ sudo apt-get install compiz-core
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  vmware-player-kernel-modules-2.6.20-16 python-kiwi libmpeg3hv libnspr4-0d
  libaften0 libamrnb0 libguicast libfuse2 libx264-54 libevent-rpc-perl
  python-feedparser libxml1 anyevent-perl libmozjs0d python-setuptools
  libquicktimehv libboost-python1.33.1
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  compiz-core
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/188kB of archives.
After unpacking 0B of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  compiz-core
Install these packages without verification [y/N]? y
(Reading database ... 138798 files and directories currently installed.)
Preparing to replace compiz-core 1:0.5.2+git20070918-0ubuntu5~ppa1 (using .../compiz-core_1%3a0.5.2+git20070918-0ubuntu5~ppa1_i386.deb) ...
Unpacking replacement compiz-core ...
Setting up compiz-core (0.5.2+git20070918-0ubuntu5~ppa1) ...
stephen@stephen-desktop:~$ 


---

### Post by [S|G] on 2007-10-17
From your message it seems that compiz-core wasn't being installed because some sort of problem with the package signature (maybe missing repository keys?) but I take you installed it when you ran apt-get manually.

---


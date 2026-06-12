---
title: "failed update and broken packages"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by asternyx on 2007-07-21
I just installed Ubuntu (6.06) then upgraded to 7.04. During the process I think I did something wrong (there was a configuration in terminal -- a blue background -- talking about MD and Raid arrays etc).

I accidentally cancelled this and the dist-upgrade failed, now there is a dependancy error and broken packages.

terminal output from using "sudo apt-get install -f"

> asternyx@toplap:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  belocs-locales-bin: Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20 is installed
  lib32gcc1: Depends: libc6-i386 (>= 2.3.6-7) but 2.3.6-0ubuntu20 is installed
  lib32z1: Depends: libc6-i386 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20 is installed
  python-support: Depends: python (>= 2.4.3-10) but 2.4.2-0ubuntu3 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies


Any help would be much appreciated.

---

### Post by forestpixie on 2007-07-21
If I have read the man page correctly 

```

sudo dpkg -C
```

this will according to the man page
              Searches for packages that have been installed only partially on
              your  system. dpkg will suggest what to do with them to get them
              working.

---


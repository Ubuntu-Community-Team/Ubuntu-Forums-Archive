---
title: "I can`t update linux kernel"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by GoranI on 2007-09-11
[B]When I tried to update linux kernel on Ubuntu 7.04 (with WUBI)
i get this error:[/B]
"The following packages will be upgraded:
  linux-image-2.6.20-16-generic
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/23,8MB of archives.
After unpacking 8192B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 111822 files and directories currently installed.)
Preparing to replace linux-image-2.6.20-16-generic 2.6.20-16.29 (using .../linux-image-2.6.20-16-generic_2.6.20-16.31_i386.deb) ...
The directory /lib/modules/2.6.20-16-generic still exists. Continuing as directed.
Done.
Unpacking replacement linux-image-2.6.20-16-generic ...
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.20-16-generic_2.6.20-16.31_i386.deb (--unpack):
 unable to make backup link of `./boot/config-2.6.20-16-generic' before installing new version: Operation not permitted
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.20-16-generic_2.6.20-16.31_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)"
WHAT TO DO ??

---

### Post by mlentink on 2007-09-11
Did you use the update manager?
If not, what did you use to upgrade the kernel?
It seems you have a permissions problem, since you weren't able to backup your boot configuration.

---

### Post by snifer on 2007-09-11
It looks like it's a wubi problem: [http://ubuntuforums.org/showthread.php?t=477074](http://ubuntuforums.org/showthread.php?t=477074)
You can try using this tip: [http://ubuntuforums.org/showpost.php?p=1090468&postcount=12](http://ubuntuforums.org/showpost.php?p=1090468&postcount=12)

---


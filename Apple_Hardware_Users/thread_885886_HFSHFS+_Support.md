---
title: "HFS/HFS+ Support"
date: 2008-08-10
forum: Apple Hardware Users
---

### Post by deamon_knight on 2008-08-10
What if any packaged do I have to install to have proper HFS/HFS+ read support. As I understand it, HFS+ write support isn't reliable, adn I seem to be able to read HFS/HFS+ volumes with a base install (Using Xubuntu 8.04), but there are a number of packages in the repositories that talk about providing HFS/HFS+ support:

hfsplus (ubuntu supported)
hfsprogs
hfsutils (ubuntu supported)
hfsutils-tcltk

Should I install any or all of these? Or None?

Thanks

---

### Post by cyberdork33 on 2008-08-10
you can install hfsplus, but if it works currently, there is no need to install anything.

---

### Post by deamon_knight on 2008-08-11
I guess the question is, what if any are the limitations of the default settings, and what do these packages provide?

---

### Post by cyberdork33 on 2008-08-11
> **deamon_knight said:**
> I guess the question is, what if any are the limitations of the default settings, and what do these packages provide?

You are limited to read-only unless you disable journaling. 

The progs are items that will let you do fsck on hfs+ and such, but I wouldn't recommend using them.
[http://packages.ubuntu.com/hardy/hfsprogs](http://packages.ubuntu.com/hardy/hfsprogs)

utils is apparently some commandline tools for reading / writing to HFS+ volumes.
[http://packages.ubuntu.com/hardy/hfsutils](http://packages.ubuntu.com/hardy/hfsutils)

and the -tcltk package is some GUI interfaces for the previously mentioned utilities.
[http://packages.ubuntu.com/hardy/hfsutils-tcltk](http://packages.ubuntu.com/hardy/hfsutils-tcltk)

hfsplus appears to be a library that provides access to hfs+... so it might be required by something like gparted in order to manipulate hfs+.
[http://packages.ubuntu.com/hardy/hfsplus](http://packages.ubuntu.com/hardy/hfsplus)

However, the driver for hfs+ is part of the kernel, so there is no need for other packages in order to "access" hfs+ partitions.

---

### Post by deamon_knight on 2008-08-12
Thanks Cyber

---


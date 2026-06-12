---
title: "Broken Package"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by Matt Nichols on 2007-05-28
I am attempting to install the LiVES package from [www.getdeb.net](www.getdeb.net) for Feisty, but I am having some significant difficulties. I run the .deb file, and it tells me I have broken dependencies. So I go into the terminal and type

```
sudo apt-get install -f
```

to fix. But I get this, and it still doesn't work.

```
matt@matt-ubuntu:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  python-alsaaudio libzzip-0-12 python2.4-dev apache2-utils libneon26
  linux-headers-2.6.20-15-generic libqt4-qt3support libapr1 libqt4-core
  libsqlite0 apache2-mpm-prefork libsvn1 kdesvn-kio-plugins librpcsecgss2
  apache2.2-common libqt4-gui libqt4-sql linux-headers-2.6.20-15 libsvnqt3
  libpq4 pychecker libaprutil1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libmjpegtools0
The following NEW packages will be installed:
  libmjpegtools0
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
15 not fully installed or removed.
Need to get 0B/209kB of archives.
After unpacking 537kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 135093 files and directories currently installed.)
Unpacking libmjpegtools0 (from .../libmjpegtools0_1%3a1.8.0-0.4_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libmjpegtools0_1%3a1.8.0-0.4_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libmjpegutils-1.8.so.0.0.0', which is also in package libmjpegtools0c2a
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libmjpegtools0_1%3a1.8.0-0.4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
matt@matt-ubuntu:~$ 
```

Any ideas? I need to fix this before I can install anything, it seems. Any help would be greatly appreciated, thanks.

---

### Post by dstew on 2007-05-28
It seems your package is trying to overwrite the file libmjpegutils-1.8.so.0.0.0 that was previously installed by the Feisty-specific package libmjpegtools0c2a with its own, and apt-get detected this. It is trying to protect the integrity of your system.

Are you sure you have the Feisty-specific package from  [this link]("http://www.getdeb.net/release.php?id=558")? The name is  lives_0.9.8.4-0~getdeb1_i386.deb

---

### Post by Matt Nichols on 2007-05-29
I tried that link (I think I was using it before, too), to the same results. Any way I can delete the thing it is trying to overwrite, or is that a bad idea? Thanks.

---

### Post by Matt Nichols on 2007-05-29
I think that libmjpegtools0 and libmjpegtools0c2a cannot be installed in parallel because they share something (libmjpegutils-1.8.so.0.0.0) which one tries to overwrite, but is not allowed to. These are both needed (aparently) by lives, and also perhaps Cinelerra, which I could not get to work earlier. Is there a way around this?

---

### Post by dstew on 2007-05-29
I can't tell you with any confidence that libmjpegtools0 and libmjpegtools0c2a are equivalent. If you really want to go ahead, you can remove the libmjpegtools0c2a package (apt-get remove libmjpegtools0c2a) and try to install the LiVES package. If it installs, OK, but maybe down the road you will find some other application needs to have the libmjpegtools0c2a package. It is an experiment you might want to try.

---


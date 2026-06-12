---
title: "Software index is broken"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by damonjablons on 2008-02-18
I'm getting this error because I tried to install AWN Curves and something went awry.

Now I have this error.  I tried running: sudo apt-get install -f

and I get this output:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libawn-bzr
The following NEW packages will be installed:
  libawn-bzr
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 64.0kB of archives.
After unpacking 180kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://download.tuxfamily.org gutsy/avant-window-navigator libawn-bzr 0.2.0-bzr158-1 [64.0kB]
Fetched 64.0kB in 0s (124kB/s)
(Reading database ... 98457 files and directories currently installed.)
Unpacking libawn-bzr (from .../libawn-bzr_0.2.0-bzr158-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libawn-bzr_0.2.0-bzr158-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libawn.so.0.0.1', which is also in package libawn0
Errors were encountered while processing:
 /var/cache/apt/archives/libawn-bzr_0.2.0-bzr158-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Thanks in advance for the help!

---

### Post by spiderbatdad on 2008-02-18
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---


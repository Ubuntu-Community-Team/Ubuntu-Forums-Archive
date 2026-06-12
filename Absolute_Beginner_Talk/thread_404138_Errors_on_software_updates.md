---
title: "Errors on software updates"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by chris.olsen on 2007-04-08
I keep getting prompted to update libmjpegtools, but always get an error when trying to do so.  I have tried to uninstall the library, and re-install it, but I can't uninstall it without uninstalling all the programs that use them.  

Here is the error that I get when trying to run the update:
E: /var/cache/apt/archives/libmjpegtools0_1%3a1.8.0-0.3sarge1_i386.deb: trying to overwrite `/usr/lib/libmjpegutils-1.8.so.0.0.0', which is also in package libmjpegtools0c2a

---

### Post by moffa on 2007-04-08
To repair an installation try
```
 sudo apt-get install -f 
```

---

### Post by chris.olsen on 2007-04-22
Sorry for the late reply back.

It first seemed to work, but after running the next update it was there again.  I have tried to uninstall the items, but when I do that it tries to uninstall a number of other programs, so I quickly cancel it before any damage is done.

---

### Post by Fraoch on 2007-05-11
The exact same issue has cropped up here.

I think there's some sort of conflict with the DVD codecs Automatix installs.

What do I do?  Uninstall the codecs through Automatix, correct this problem using apt-get install -f, then reinstall the codecs?

---

### Post by ricardisimo on 2007-06-19
Same here, with the twist that Synaptic thinks that transcode is the broken dependency, but the truth is that I can remove, install, reinstall, do anything I like with transcode. What I cannot touch at all is libmjpegtools0c2a. Here's some standard output:
```
~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libmjpegtools0c2a
The following NEW packages will be installed:
  libmjpegtools0c2a
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/218kB of archives.
After unpacking 549kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 188971 files and directories currently installed.)
Unpacking libmjpegtools0c2a (from .../libmjpegtools0c2a_1%3a1.8.0-0.2ubuntu3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libmjpegtools0c2a_1%3a1.8.0-0.2ubuntu3_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libmjpegutils-1.8.so.0.0.0', which is also in package libmjpegtools0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libmjpegtools0c2a_1%3a1.8.0-0.2ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Update Manager will not work until this is resolved... which is problematic, but I'm not a programmer, so I'm not going to question the wisdom of this. Any help at all will be appreciated.

---

### Post by ricardisimo on 2007-06-19
Resolved:
```
sudo dpkg -P --force-depends libmjpegtools0 && sudo apt-get install -f
```
Thank you to Daniel Chen for this.

---


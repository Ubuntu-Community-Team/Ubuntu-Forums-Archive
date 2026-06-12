---
title: "Cannot install kdenlive (actually mlt and mlt++)"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by Mr. Miner on 2007-05-18
So I go to apt-get install kdenlive and the process hangs up on unpacking mlt_cvs20070101.deb.

```
Unpacking mlt (from .../mlt_0.2.1-1+3v1ubuntu0_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/mlt_0.2.1-1+3v1ubuntu0_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libmlt.so.0.2.2', which is also in package libmlt0.2.2
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/mlt_0.2.1-1+3v1ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Now I can't apt-get remove kdenlive...or mlt...or mlt++ due to unmet dependencies.  I try 
```
sudo apt-get -f install
```
and get this
```
croberts@NEFERTITI:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  mlt
The following NEW packages will be installed:
  mlt
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
2 not fully installed or removed.
Need to get 0B/3335kB of archives.
After unpacking 7975kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  mlt
Install these packages without verification [y/N]? y
(Reading database ... 112000 files and directories currently installed.)
Unpacking mlt (from .../mlt_0.2.1-1+3v1ubuntu0_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/mlt_0.2.1-1+3v1ubuntu0_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libmlt.so.0.2.2', which is also in package libmlt0.2.2
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/mlt_0.2.1-1+3v1ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any thoughts?

---

### Post by Egils on 2007-05-24
I don't have a lot of experience with apt-based errors, but I have run into problems before trying to install kdenlive from debian repositories. 

Have you tried removing the broken packages in Synaptic yet? To do this you would open synaptic, click on the "Custom Filters" in the bottom lefthand corner, select "broken" from left panel and then remove the packages that appear in the main panel. Then you would do a reload from within synaptic, or apt-get update, and maybe try again.

It's possible that the packages you are trying to install are in conflict something else - did you try to install any of the packages for kdenlive from source, or have you added any repositories for kdenlive other than Treviño's? I didn't have any problems installing kdenlive from the Treviño repository on a fresh Fiesty (i386) install.

---


---
title: "Clamav elp"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by geezerone on 2007-02-21
Hi

I have clamav 88.4 installed but wanted to update to 90. I downloaded the package to my local desktop and ran ./configure  and make install which went ok but had two versions running and clamtk only ran 88.4 not version 90. I uninstalled clam apps via synaptic and get this:

```
$ whereis freshclam
freshclam: /usr/bin/freshclam /usr/bin/X11/freshclam /usr/local/bin/freshclam /u sr/local/etc/freshclam.conf /usr/share/man/man1/freshclam.1.gz
```

Have I installed the new version in the wrong place as freshclam wouldn't work and still doesn't?

Also how would I go about getting clamtk to work with version 90 or failing that uninstalling version 90?

TIA

** edit ** I tried make distclean to remove files but still have some clam files left in the following place:

/usr/local/bin$ ls -l
total 564
-rwxr-xr-x 1 root root   1032 2007-02-19 22:57 clamav-config
-rwxr-xr-x 1 root root  45710 2007-02-19 22:57 clamconf
-rwxr-xr-x 1 root root  78148 2007-02-19 22:57 clamdscan
-rwxr-xr-x 1 root root 114108 2007-02-19 22:57 clamscan
-rwxr-xr-x 1 root root 154011 2007-02-19 22:57 freshclam
-rwxr-xr-x 1 root root 155331 2007-02-19 22:57 sigtool

---

### Post by geezerone on 2007-02-21
Anyone can assist please?? :)

---


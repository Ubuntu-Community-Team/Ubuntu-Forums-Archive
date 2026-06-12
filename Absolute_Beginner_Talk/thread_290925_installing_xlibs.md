---
title: "installing xlibs"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by bduenskie on 2006-11-01
I'm trying to get ColdFusion running on my ubuntu box.  It's telling me I need to install xlibs to get the graphing service working.

So I go to install the xlibs and this is what I get:

dpkg -i xlibs_6.8.2-10.4_all.deb(Reading database ... 23982 files and directories currently installed.)
Preparing to replace xlibs 6.8.2-10.4 (using xlibs_6.8.2-10.4_all.deb) ...
Unpacking replacement xlibs ...
dpkg: dependency problems prevent configuration of xlibs:
 xlibs depends on libice6; however:
  Package libice6 is not installed.
 xlibs depends on libsm6; however:
  Package libsm6 is not installed.
 xlibs depends on libxi6; however:
  Package libxi6 is not installed.
 xlibs depends on libxmu6; however:
  Package libxmu6 is not installed.
 xlibs depends on libxmuu1; however:
  Package libxmuu1 is not installed.
 xlibs depends on libxp6; however:
  Package libxp6 is not installed.
 xlibs depends on libxrandr2; however:
  Package libxrandr2 is not installed.
 xlibs depends on libxt6; however:
  Package libxt6 is not installed.
 xlibs depends on libxtrap6; however:
  Package libxtrap6 is not installed.
 xlibs depends on libxtst6; however:
  Package libxtst6 is not installed.
 xlibs depends on xlibs-data; however:
  Package xlibs-data is not installed.
dpkg: error processing xlibs (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xlibs

I'm a total newb so I'm not sure where to begin.

---

### Post by po0f on 2006-11-01
bduenskie,

You're going to have to install all the packages that are not installed.  I did a couple of searches on [packages.ubuntu.com](http://packages.ubuntu.com/) and got a couple of hits for some of the packages you're missing.  I don't know if all of them are in the repos or not.  Try running this command from a terminal:
```
sudo aptitude install libice6 libsm6 libxi6 libxmu6 libxmuu1 libxp6 libxrandr2 libxt6 libxtrap6 libxtst6 xlibs-data
```

By the way, how are you trying to install xlibs?  Via Synaptic or something else?

---

### Post by bduenskie on 2006-11-01
Worked like a charm, you are the man!

Thank you!

---


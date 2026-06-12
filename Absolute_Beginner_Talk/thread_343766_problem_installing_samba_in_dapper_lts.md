---
title: "problem installing samba in dapper lts"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by Horza on 2007-01-21
What would cause an attempt to install samba to an updated (also not updated) but otherwise pristine dapper 6.06 lts with apt-get to produce this failure msg:

***********8

Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  samba: Depends: samba-common (= 3.0.22-1ubuntu4) but 3.0.22-1ubuntu3.1 is to be installed
         Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20 is to be installed
         Depends: libgnutls13 (>= 1.4.0-0) but it is not installable
         Depends: libpopt0 (>= 1.10) but 1.7-5 is to be installed
E: Broken packages

***********

Thanks.

---

### Post by Horza on 2007-01-22
Problem was, I had earlier tried to install something from an Edgy APTonCD repository, which appears to have messed things up pretty badly.  Reinstalled Dapper, updated, & then samba & smbfs both installed cleanly.

---


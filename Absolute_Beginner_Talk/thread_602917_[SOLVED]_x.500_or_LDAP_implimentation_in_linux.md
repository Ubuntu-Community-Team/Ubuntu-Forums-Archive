---
title: "[SOLVED] x.500 or LDAP implimentation in linux?"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by mister_lister on 2007-11-04
Does linux use x.500 or LDAP for network directory information? Windows has Active Directory, Novell (at least the old novell) had NOS implimentations of x.500 and LDAP. What does LINUX do? Do the standards apply?

---

### Post by daengbo on 2007-11-04
Linux has several implementations of LDAP. 

OpenLDAP is probably the most common, but is notoriously difficult to get running. If you are a beginner with this, I suggest using an eBox server as that is the closest thing to out-of-the-box you'll get for OpenLDAP. You'll need to install [SLAPd]("apt:slapd") on Ubuntu to get it.

The Fedora Directory Server (FDS) is another offering. From the name, you can guess it's from Red Hat. You'll likely end up compiling from source for this one, though there may be a repository.

Good luck.

---


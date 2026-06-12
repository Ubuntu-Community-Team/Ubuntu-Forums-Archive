---
title: "Cant install libnss-ldap, libpam-ldap"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by whitmad on 2007-05-15
I'm looking at replacing Fedora with Ubuntu on all the machines on my network - I've got one trial client set up, problem is I can't set up ldap authentication - libnss-ldap doesn't appear in ths Synaptic package list, nor does libpam-ldap. No luck with aptitude or apt-get either.  This is a vanilla install of 6.10 desktop with only the minimal config necessary to connect to the internet through my network.

I'm probably missing something pretty basic - any suggestions gratefully received.

David

---

### Post by chamberlain2006 on 2007-05-15
You've got to enable the repositories in your /etc/apt/sources.list file.  Uncommenting all of the lines should do it.

---

### Post by annda on 2007-05-15
that's right: a quick search on packages.ubuntu.com shows that you need the universe repository.

---

### Post by whitmad on 2007-05-15
Did the trick, once I reloaded in Synaptic. Thanks

---

### Post by paljas on 2007-05-16
Remains (for me) the question as to why this is in universe. I'm also looking into replacing redhat like clients (centos) with ubuntu systems. So now i am installing those packages and editing a few files. Why isn't this in the standard system? With fedora/RHEL one can insert to ldap server and distinguished name at install time.

I can't find anything about ldap in preseeded installs. Is it just me who is surprised about this?

---

### Post by BrendanM on 2007-11-04
Fedora/RHEL is intended to be used on business systems. Ubuntu is much more geared at the home desktop user. Most home desktop users don't have an LDAP server. That probably explains the descrepency.

---


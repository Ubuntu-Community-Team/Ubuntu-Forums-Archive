---
title: "Question About Updating Feisty"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by cygnis1 on 2007-10-18
I am looking forward to upgrading to Gutsy, but want to update Feisty first.  I did a sudo apt-get update in the terminal but some of the components were not available or were missing.  this is the message on the terminal after the system was 'updated' :

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz)  302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz)  302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz)  302 Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

My question is this:  Do I need to get these components (and how?) or can I upgrade to Gutsy as my system is currently?
Thanks,
 Cygnis1

---

### Post by Lord_Dicranius on 2007-10-18
I'd say you should be able to upgrade the system as it is.  You shouldn't need to update the "feisty stuff" first.  It should detect the software versions and update as needed.

**EDIT**
You also might want to uncheck those (or comment them out) while upgrading.

---

### Post by cygnis1 on 2007-10-18
I tried to update to 7.10 and got a message which stated:that I needed some packages.  Here are the items that are needed.

[http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz:) 302 Found
[http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz:) 302 Found
[http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz:) 302 Found
[http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz:) 302 Found

How do I get these and where?
Thanks
Cygnis1

---

### Post by FredB on 2007-10-18
> **cygnis1 said:**
> I tried to update to 7.10 and got a message which stated:that I needed some packages.  Here are the items that are needed.

[http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz:) 302 Found
[http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz:) 302 Found
[http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz:) 302 Found
[http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz:](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz:) 302 Found

How do I get these and where?
Thanks
Cygnis1

Two possibilities.

1) Unactivate these repositories (via synaptic) or commenting them (adding a #) in /etc/apt/sources.list

2) modify  /etc/apt/sources.list by replacing feisty by gutsy.

---

### Post by cygnis1 on 2007-10-18
How do I undo these packages in Synaptic?  I can't find them.

---

### Post by asafm on 2007-10-18
I did this commenting solutions and it worked.
Thanks!

---

### Post by cygnis1 on 2007-10-18
what is commenting solutions?  How and where do you do it?
Cygnis1

---


---
title: "multiuniverse fails after upgrate to edgy"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by alfgr on 2007-02-04
Hi 

After upgrading to edgy, it seems I can no longer update multiuniverse packages. I keep getting the message "Could not download all repository indexes" and 

[http://security.ubuntu.com/ubuntu/dists/edgy-security/Release:](http://security.ubuntu.com/ubuntu/dists/edgy-security/Release:) Unable to find expected entry  multiuniverse/binary-i386/Packages in Meta-index file (malformed Release file?)
[http://no.archive.ubuntu.com/ubuntu/dists/edgy/Release:](http://no.archive.ubuntu.com/ubuntu/dists/edgy/Release:) Unable to find expected entry  multiuniverse/binary-i386/Packages in Meta-index file (malformed Release file?)
[http://no.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release:](http://no.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release:) Unable to find expected entry  multiuniverse/binary-i386/Packages in Meta-index file (malformed Release file?)
[http://no.archive.ubuntu.com/ubuntu/dists/edgy-backports/Release:](http://no.archive.ubuntu.com/ubuntu/dists/edgy-backports/Release:) Unable to find expected entry  multiuniverse/binary-i386/Packages in Meta-index file (malformed Release file?)
[http://packages.freecontrib.org/ubuntu/plf/dists/edgy-plf/free/binary-i386/Packages.gz:](http://packages.freecontrib.org/ubuntu/plf/dists/edgy-plf/free/binary-i386/Packages.gz:) 404 Not Found
[http://packages.freecontrib.org/ubuntu/plf/dists/edgy-plf/non-free/binary-i386/Packages.gz:](http://packages.freecontrib.org/ubuntu/plf/dists/edgy-plf/non-free/binary-i386/Packages.gz:) 404 Not Found

when using the update manager. Is something wrong with my sources.list? (see below)

alfgr@trofast:~$ more /etc/apt/sources.list
## Regular ubuntu repositories
deb [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) edgy main restricted universe multiuniverse
deb [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiuniverse
deb [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiuniverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiuniverse

##Penguin Liberation front stuff
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) edgy-plf free non-free

## Canonical Commercial Repository (Opera,Real Player10.. etc)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

I would appreciate any help

---

### Post by taurus on 2007-02-04
Edit /etc/fstab and remove the **no.** from your repos and place a # in front of this repo,  deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf).  Save the changes and then run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by kwaanens on 2007-02-04
> **taurus said:**
> Edit /etc/fstab and remove the **no.** from your repos

"no" works great. That's the Norwegian mirrors.
However, it's not called "multiuniverse", but "multiverse". Change that and it will work

---

### Post by alfgr on 2007-02-04
thanks! Must check my reading skills. I was certain it was multiuniverse..

---


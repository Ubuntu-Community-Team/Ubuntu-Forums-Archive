---
title: "Stuck in installer"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by Justgeek on 2008-01-04
When ever i do a sudo apt-get update  or anything else concerning an install i get this

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status

---

### Post by taurus on 2008-01-04
Could be something wrong with your /etc/apt/sources.list?  Can you open a terminal and post it here?

```
cat /etc/apt/sources.list
```

---

### Post by Justgeek on 2008-01-04
> # Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) feisty main restricted 
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) feisty-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) feisty universe multiverse 
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe multiverse


Should be fine

---


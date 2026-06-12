---
title: "Update Manager Issue-Newb Alert!!"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by ehbien on 2007-10-26
I am a very recent (3 weeks) convert to Ubuntu.  Installed Feisty from the live CD w/ no problem.  But I seem to be having difficulty installing updates via the update manager.  I have 145 updates ready to install, but I receive the following error message:

E: /var/cache/apt/archives/bsdutils_1%3a2.12r-17ubuntu2.1_i386.deb: files list file for package `xeyes' is missing final newline

Could you please advise me, in newb terms, of how i should proceed? Thanks in advance.

---

### Post by yabbies on 2007-10-26
missing some files from xeyes
try reinstalling xeyes to see if that fixes your problem

either from system>admin>synaptic package

and search for xeyes
uninstall
close synaptic &
open a terminal and type

```
sudo apt-get clean
```

open synaptic and reinstall xeyes

---

### Post by charleseddy on 2008-01-15
This usually happens after filesystem corruption, when fsck removes or changes things that corrupt dpkg/info. This solution should work:

1. sudo gedit /var/lib/dpkg/status
2. Delete the section for xeyes.
3. sudo mv /var/lib/dpkg/info /var/lib/dpkg/info_old
4. sudo mkdir /var/lib/dpkg/info
5. sudo apt-get update
6. sudo apt-get -f install

I apologize for the late response.

---


---
title: "Ubuntu (gutsy) borked - Broken Pipe? Help please!"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by al4ie on 2008-01-14
Im trying to fix my installation, most recently trying: spt-get install fix --broken

and I am getting this at the end of the terminal window:

"dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kde-icons-oxygen_4%3a4.0.0-0ubuntu1~gutsy1_all.deb
 /var/cache/apt/archives/kdebase-runtime-data_4%3a4.0.0-0ubuntu1~gutsy1_all.deb
 /var/cache/apt/archives/kdebase-runtime-bin-kde4_4%3a4.0.0-0ubuntu1~gutsy1_i386.deb
 /var/cache/apt/archives/kdebase-runtime_4%3a4.0.0-0ubuntu1~gutsy1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
alfie@Alfies:~$ "

Has anyone seen this/Can help?

Thanks in advance, yours, 

frustrated Alfie.

---

### Post by dstew on 2008-01-14
Try```
sudo apt-get update
sudo apt-get install --fix-broken
```

---


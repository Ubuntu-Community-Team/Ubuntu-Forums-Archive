---
title: "Bandwidth monitor tool for kubuntu?"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by dynamethod on 2008-02-12
Hey im after a BM for Kubuntu 7.10, i tried to install, i actually need it asap, but im struggling to find anything decent out there, i tried bmon(lol), but i need something so that i can see weekly/monthly reports of my usage(im on wireless, ralink device) help much needed and appreicated

---

### Post by dynamethod on 2008-02-12
Oh btw, can someone please explain wtf this means cause im getting kinda irrate trying to fiddle with this now...

[http://paste.ubuntu-nl.org/55675/](http://paste.ubuntu-nl.org/55675/)

thanks

---

### Post by emarkd on 2008-02-12
Not sure on this, but it seems like a bad config file?  Have you had that installed before and are trying to reinstall it?  If so, try purging it first:

```
sudo apt-get remove --purge bandwidthd
```

then try installing it again.  I tried installing it here and it installs fine.  Maybe that helps.

---

### Post by dynamethod on 2008-02-12
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgd2-noxpm
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bandwidthd*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 201kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing bandwidthd (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 bandwidthd
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by dynamethod on 2008-02-12
im being told from someone helping me in freenode that my package manager is stuffed, how could i restore it?


EDIT solved the deb problem, now back to searching for a bandwidth monitor tool any suggestions welcomed, i need something that will start at boot and monitor my ul/dl traffic and let me view how much im using each week and month, thanks

---

### Post by emarkd on 2008-02-12
So a couple of things to try:

```
sudo apt-get install -f
```

should fix broken packages, and

```
sudo apt-get check
```

runs a check on the database

Maybe one of these will straighten it out.

---

### Post by dynamethod on 2008-02-12
yup i got everything sorted now, using knemo, its very good

---


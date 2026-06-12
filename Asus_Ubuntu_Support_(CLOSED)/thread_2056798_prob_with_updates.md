---
title: "prob with updates"
date: 2012-09-12
forum: Asus Ubuntu Support (CLOSED)
---

### Post by timetest on 2012-09-12
any ideas why I cant check for updates 

i get the message E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.

thanks

---

### Post by dargaud on 2012-09-12
Had this a few days ago as well. Fixed with this:
```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

```

---


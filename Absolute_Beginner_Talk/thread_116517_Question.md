---
title: "Question"
date: 2006-01-12
forum: Absolute Beginner Talk
---

### Post by nkingcade on 2006-01-12
Is there an easy way to aquire the various libraries that are sometimes needed for  tarballs that are downloaded? For instance, I downloaded a tar file and ran ./configure to check it. ./configure found I needed two libraries. I did not know where to begin looking. Is there a procedure or should I begin my search at sourceforge.net or some place like that?

Neal

---

### Post by 23meg on 2006-01-12
You should install them from the repositories if possible. Mind that the package names can sometimes be different than what the makefile says though. Which libraries are they?

---

### Post by nkingcade on 2006-01-12
The packages are "zlib" and "zlib-devel". 

Neal

---

### Post by 23meg on 2006-01-13
See if they're in the repositories with ```
apt-cache search zlib
apt cache search zlib-devel
```or by doing a package name search in Synaptic. If they are, install them with ```
sudo apt-get install package_name
```

---


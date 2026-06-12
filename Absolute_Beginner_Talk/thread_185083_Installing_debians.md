---
title: "Installing debians"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by DesignerX on 2006-05-31
Hi, 

How can I install a .deb file ?

Thanks.

---

### Post by Perfect Storm on 2006-05-31
First you might check if the package is availble thtrough synaptic package manager ( System tab ---> Adminstration ---> Synaptic), also setup your sourcelist for more applications etc.: [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

If it isn't there - 

```
cd /where/the/.deb/package/is
sudo dpkg -i XXXXXXXXXX.deb
```

In dapper you just double click it.

---

### Post by Simian on 2006-05-31
If the deb file has been downloaded to you home directory is that where it will be installed by default, or do deb files know where they have to be installed them self?

---

### Post by Perfect Storm on 2006-05-31
It know (well programmed) to know where it should put the files, so you don't need to worry about it :)

---

### Post by mostwanted on 2006-05-31
A debian file is a virtual file-system which mimics a typical unix file-system. The files are simply copied to the real destinations from the virtual directories in the package when you install it.

---


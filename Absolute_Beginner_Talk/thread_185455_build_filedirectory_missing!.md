---
title: "build file/directory missing!?"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by spier on 2006-05-31
Just got dapper installed  from alternate cd and everything seems OK but my laptop Fn keys.

Well, trying to install sony_acpi module from [http://download.berlios.de/fsfn/sony_acpi.tar.gz](http://download.berlios.de/fsfn/sony_acpi.tar.gz), it complains about  a missing file in dapper,  but worked with  breezy.

```
make: *** /lib/modules/2.6.15-23-386/build: No such file or directory.  Stop.

```

Sure I`m missing something...

Thanks in advance

---

### Post by catlett on 2006-05-31
Can't really tell what is going on so I'll start with the basics, sorry if you already know this but I figured I'd try and see if it helps.
Did you install buil-essential before you started to compile? You need this package to compile from source.```
 sudo apt-get install build-essential
```
Second did you scroll through synaptic package manager and see if that module was there in the repositories?

---

### Post by gingermark on 2006-05-31
You will need "build-essential" at a minimum. You can get that from the repositories. It wasn't on the Breezy install CD either, but I guess you must have forgotten you installed it last time! :)
EDIT: Too slow.

---

### Post by az on 2006-05-31
[QUOTE=gingermark]You will need "build-essential" at a minimum. You can get that from the repositories. It wasn't on the Breezy install CD either, but I guess you must have forgotten you installed it last time! :)
EDIT: Too slow.[/QUOTE]

build-essential is on both the Desktop cd and the alternate cd.  It was on the install cd for breezy, too.

As well you need to install the linux-headers package (which matches your kernel)  That too is on the cd.

The Desktop cd's repository is useable once you install.  It contains a handful of useful packages for those who need to build their network drivers and such.  Just instert the live cd again once you are at the desktop, after you have installed it to hard disk.  You will get a window asking if you want to add the packages on the cd to your repos.

---


---
title: "fakeroot"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by Ranganaths on 2007-01-24
hi people,

            I  am installing the java1.6 on my ubuntu. I have .bin file. I need to install so i used the following commands
chmod +x {downloaded_file_name}.bin-> this will work fine.

fakeroot make-jpkg {downloaded_file_name}.bin
The above command will give error as follows
/usr/bin/fakeroot: line 150: make-jpkg: command not found

please let me know how to create .deb package and install the java 1.6

Thank you
Regards

---

### Post by jvc26 on 2007-01-24
I followed this guide from mlind:
> 
Well it doesn't seem to. I'll attach a debdiff to get sun-java6 support for java-package.


To get current java-package, you must add multiverse source repository in /etc/apt/sources.list
Code:

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty multiverse

Then patch and build java-package
Code:

mkdir /tmp/java-package cd /tmp/java-package apt-get source java-package cd java-package-0.28 patch -p1 < /path/to/java-package_sun-java6.patch sudo aptitude install debhelper debian/rules binary sudo dpkg -i ../java-package_0.28ubuntu1_all.deb

Build java6 binaries
Code:

sudo aptitude install fakeroot fakeroot make-jpkg jdk-6-linux-i586.bin

/edit
I forgot to attach already patched .deb
/edit2
patch was missing j2re install and remove scripts

[http://ubuntuforums.org/showthread.php?t=316980&page=2](http://ubuntuforums.org/showthread.php?t=316980&page=2)
(see the link for the attachments he posted.

Il

---

### Post by Ranganaths on 2007-01-24
when i tried to put that code in that sources.list it says its read only and i cant change it.. 
 donno wht to do.. how come its  a big problem to install simple things here?

---

### Post by energiya on 2007-01-24
> **Ranganaths said:**
> hi people,

            I  am installing the java1.6 on my ubuntu. I have .bin file. I need to install so i used the following commands
chmod +x {downloaded_file_name}.bin-> this will work fine.

fakeroot make-jpkg {downloaded_file_name}.bin
The above command will give error as follows
/usr/bin/fakeroot: line 150: make-jpkg: command not found

please let me know how to create .deb package and install the java 1.6

Thank you
Regards

Shouldn't it be 
```

fakeroot **make-kpkg** {downloaded_file_name}.bin

``` ?

EDIT: Sorry, it's jpkg ... kernel compiling still hounts me

---

### Post by aznranndydraman on 2007-02-09
hey, I don't know if you still need this, but make-jpkg seems to be from the java-package, so do:
```
sudo apt-get install java-package
``` and it'll work

---

### Post by energiya on 2007-02-10
Or after
```

chmod a+x file.bin

```
try
```

./file.bin
**or**
sh file.bin

```
this is the way to install java runtime. Hope this helps (if you still need it).

---


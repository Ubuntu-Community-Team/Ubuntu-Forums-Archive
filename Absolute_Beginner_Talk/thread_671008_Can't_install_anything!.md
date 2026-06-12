---
title: "Can't install anything!"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by thesqudge on 2008-01-18
when ever I use the code ```
./configure
``` and then I get this...

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking how to create a ustar tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... none
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

```

If I try to use the code ```
make
``` it will say command not found. 

What am I doing wrong? If it helps, I'm running Ubuntu 6.06 on parallels on Mac OS X.

---

### Post by Sef on 2008-01-18
Open the terminal (Applications > Accessories > Terminal)

then type in ```
sudo apt-get update
```

then type in ```
sudo apt-get install build-essential
```

You will need the disk that you installed your Ubuntu from as it is downloaded from that disk.

---

### Post by thesqudge on 2008-01-18
ok i'll try

---

### Post by thesqudge on 2008-01-18
ok when i put the first code in i got:
```
Get:1 http://ca.archive.ubuntu.com dapper Release.gpg [189B]
Get:2 http://ca.archive.ubuntu.com dapper-updates Release.gpg [191B]
Hit http://ca.archive.ubuntu.com dapper Release
Hit http://ca.archive.ubuntu.com dapper-updates Release
Hit http://ca.archive.ubuntu.com dapper/main Packages
Hit http://ca.archive.ubuntu.com dapper/restricted Packages
Hit http://ca.archive.ubuntu.com dapper/main Sources
Hit http://ca.archive.ubuntu.com dapper/restricted Sources
Hit http://ca.archive.ubuntu.com dapper-updates/main Packages
Hit http://ca.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://ca.archive.ubuntu.com dapper-updates/main Sources
Hit http://ca.archive.ubuntu.com dapper-updates/restricted Sources
Get:3 http://security.ubuntu.com dapper-security Release.gpg [191B]
Hit http://security.ubuntu.com dapper-security Release
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Fetched 3B in 1s (2B/s)
Reading package lists... Done
```

then with the second one i got:
```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package build-essentail
```

i tried installing the software i originaly wanted to install and it didn't work again. i have the .iso file being read as a disk but does it need to be read in the E drive or something? what did i do wrong now?

---

### Post by aJayRoo on 2008-01-18
Just a typo it should be:
```
sudo apt-get install build-essential
```

---

### Post by kvonb on 2008-01-18
-

---

### Post by Sef on 2008-01-18
Thanks for catching that Aj.

---

### Post by thesqudge on 2008-01-18
Thanks Sef It worked perfectly! haha I can't believe a couple of codes fixed my major (to me it's major) problem, lol I'm such a n00b. Anyways thanks! :)

---


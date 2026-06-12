---
title: "Installing Wine"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by C!pheR on 2006-06-14
Hi guys,

I'm tring to install Wine version 0.9.15.  I'm following the onscreen instructions here: [http://appdb.winehq.com/appview.php?versionId=4031](http://appdb.winehq.com/appview.php?versionId=4031)

I've got down to the ./configure instruction.  This is what I get:

./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... gcc -m32
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

config.log doesn't seem to shed any light (not that I'd understand!).  Anyone able to tell me where I'm going wrong please?

---

### Post by Jagot on 2006-06-14
Have you installed the build-essential package?  Is there any reaon you're not installing the version from the repos?

---

### Post by C!pheR on 2006-06-14
I tried to find wine from the repositories but it didn't find anything.

---

### Post by Jagot on 2006-06-14
Wine is in the universe repository.  Read this if you don't know how to enable it:

[http://psychocats.net/ubuntu/sources.php](http://psychocats.net/ubuntu/sources.php)

---

### Post by C!pheR on 2006-06-14
I've followed those instructions but I'm still unable to find wine.  I'm going to upgrade to 6.06, perhaps that will help?

---

### Post by Jagot on 2006-06-14
Well, Wine should be available in the 5.10 repos anyway, but it's always worth using the latest version of the operating system.

---

### Post by C!pheR on 2006-06-14
Ok, I'll give that a go and see what happens :)  Thanks for your help!

---

### Post by C!pheR on 2006-06-14
Well I've upgraded to 6.06 LTS and still no Wine...

---

### Post by Jagot on 2006-06-14
Ok- you haven't enabled the universe repo correctly - have you followed the link I posted before again now?

---

### Post by C!pheR on 2006-06-14
Yes I did, still no dice.

I've now downloaded and installed Bison and Flex. C compiler still can't compile the source for Wine. I haven't yet tried to compile anything else (mainly coz I've no idea what else I can try to compile!).  Any thoughts?

---

### Post by C!pheR on 2006-06-14
EDIT:  I think I've just fixed my own problem.  

sudo apt-get install ia32-libs ia32-libs-dev ia32-libs-gtk
./compile

---

### Post by Jagot on 2006-06-14
I have the universe repo enabled and this is the result when I try to install Wine:

```
jagot@ubuntu:~$ sudo aptitude install -s wine
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be installed:
  wine
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 8785kB of archives. After unpacking 41.4MB will be used.
Would download/install/remove packages.
```

The repositories are not enabled correctly.  My souurces.list is as follows:

```
jagot@ubuntu:~$ cat /etc/apt/sources.list
#
# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted


# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiversedeb-src http://gb.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse


deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu/ dapper-security universe main restricted multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
```

Are you sure yours looks the same as this?

Also, have you installed build-essential again?  You won't be able to compile anything without it.

---

### Post by C!pheR on 2006-06-14
Yes, I installed build-essential first of all, should have mentioned that.  Still, downloading the ia32-libs seems to have done the trick.  :)

---

### Post by Jagot on 2006-06-14
[QUOTE=C!pheR]Yes, I installed build-essential first of all, should have mentioned that.  Still, downloading the ia32-libs seems to have done the trick.  :)[/QUOTE]

OK, groovy.  Glad you've got it sorted.

---

### Post by C!pheR on 2006-06-14
Ok, now that I've managed to configure Wine it pops up with an error saying:

```
*** Warning: FreeType is missing.
*** Fonts will not be built. Dialog text may be invisible or unaligned.

```

I've been to the Synaptic Package Manager and installed everything called FreeType.

```

FreeType-tools
FreeType2
libfreetype6
libfreetype6-dev
```

I've then reconfigured and get the same error.

Should I be doing something differently?

---


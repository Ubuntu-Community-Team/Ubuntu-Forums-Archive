---
title: "Please help me what does this mean??"
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by OuTcRy on 2006-04-14
i cannot start amarok and another programs anymore after i installed libstdc

the error is

apt-cache: /lib/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib/libstdc++.so.6)
apt-cache: /lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)


i downloaded and install glib and gcc but i cannot handle it!

---

### Post by fdoving on 2006-04-14
Can you run:
```

apt-get update;apt-get -f install

```

Or does it die with the same error? 

- Frode

---

### Post by OuTcRy on 2006-04-14
apt-get -f install
apt-get: /lib/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib/libstdc++.so.6)
apt-get: /lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)


the same error...

i cannot run amarok, kpackage,opera, etc... anymore...

---

### Post by fdoving on 2006-04-14
You should mount the CD, find the glibc package, and use dpkg to install it from the CD. The problem you have is caused by a wrong version of glibc.

mount CD.
find glibc package.

dpkg --force-downgrade -i /path/to/glibc-something.deb


- Frode

---

### Post by towsonu2003 on 2006-04-14
is this dapper (testing, 6.06) or breezy (stable, 5.04)?

how did you install libstdc and gcc? if in Breezy-> via synaptic/apt-get, remove them (completely), make sure there are no references to dapper in your /etc/apt/sources.list, reload (left upper corner in synaptic) and install them again (be careful not to remove important stuff in the same time though). hopefully it will fix things... if you compiled it from source, I'm clueless...

---

### Post by OuTcRy on 2006-04-15
mine is breezy 5.10...
and i installed libstdc from debian pacckages by "dpkg -i"
i tried to remove by enterin dpkg -r but i cannot. it says 
libsd..... is not installed.... but if it is not installed why libstdc++.so.6 requires gcc or glibc? i installed these three times or more....

---

### Post by towsonu2003 on 2006-04-15
try removing it using synaptic. for search keyword, use libstdc++ and use "search name" option. while removing, select to "remove completely". while reinstalling, use synaptic again rather than dpkg. 

I'm hoping that while installing from scratch, synaptic will take care of the dependency hell.

---

### Post by OuTcRy on 2006-04-16
thanks but my synaptics is not working anymore too :(((((((

the same error.....

i can only run firefox and some standart ubuntu programs :(((

---

### Post by OuTcRy on 2006-04-16
thanks but my synaptics is not working anymore too :(((((((

the same error.....

i can only run firefox and some standart ubuntu programs :(((

---

### Post by towsonu2003 on 2006-04-16
Your apt-get wasn't working - my bad... Note that from now on, I am _not_ sure what I'm talking about... 

But first things first: **backup your files now** (this, I am very sure about) now, right now, before doing anything else...

copying from the above post, try this:
insert and mount your install CD.
find libstdc++6 package

dpkg --force-downgrade -i /path/to/libstdc++6-something.deb 

also do as fdoving says:
find glibc in the same CD

dpkg --force-downgrade -i /path/to/glibc-something.deb

still not fixing? try it with gcc as well. 

if you can't find them in the cd, browse to packages.ubuntu.com and search and download there. If it complains about missing dependencies, go to that web site and search, download, and install those dependencies (with dpkg -i /path/to/blabla-numbers.deb) than try installing again. 

While dealing with dpkg, copy paste your errors here if you can't fix them. may be we can make sense of them? 

I will be completely clueless if this doesn't work either... I never fell in a dependency hell, especially one that broke apt-get. If you get no replies here in a couple of days, try posting a new thread with
-section: desktop help
-title: "dependency hell: libstdc++"
-text: 
* do not forget to note that your apt-get and synaptic are broken, along with any other broken packages (amarok, opera, etc). 
* note there that you installed libstdc from debian packages by "dpkg -i"
* copy paste the error messages you get as well. 

Important note: try to use apt-get to install packages... dpkg is a low-level tool that doesnot check dependencies (except for erroring them out).

---

### Post by OuTcRy on 2006-04-16
dpkg --force-downgrade /media/cdrom0/pool/main/g/libstdc++6_4.0.1-4ubuntu9_i386.deb
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

if i write dpkg --force...... dpkg says this....

---

### Post by towsonu2003 on 2006-04-16
> **OuTcRy]dpkg --force-downgrade /media/cdrom0/pool/main/g/libstdc++6_4.0.1-4ubuntu9_i386.deb
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*] said:**
> .

if i write dpkg --force...... dpkg says this....
I think you forgot the -i in there: dpkg --force-downgrade **-i** /path/to/libstdc++6-something.deb

more info: --force-bla is an option, -i is an action (install). It's telling you that it needs to do an action. the syntax is
(sudo) dpkg option action <package name>
<package name> may not be required depending on action.

---

### Post by OuTcRy on 2006-04-16
ok :) i forgot -i 

i found all the directories and i installed all the files in these directories with this command...

but when i write amarok to see what is wrong on terminal, the same thing happens...

---

### Post by OuTcRy on 2006-04-16
i installed from
/media/cdrom0/pool/main/g/gcc-4.0 (libstd++ is also here)
/media/cdrom0/pool/main/g/gcc-defaults
/media/cdrom0/pool/main/g/glibc

---

### Post by OuTcRy on 2006-04-16
sudo dpkg -i libstdc++2.10-dev_2.95.4-22_i386.deb
(Reading database ... 95130 files and directories currently installed.)
Preparing to replace libstdc++2.10-dev 1:2.95.4-22 (using libstdc++2.10-dev_2.95.4-22_i386.deb) ...
Unpacking replacement libstdc++2.10-dev ...
dpkg: dependency problems prevent configuration of libstdc++2.10-dev:
 libstdc++2.10-dev depends on g++-2.95 (>= 1:2.95.4); however:
  Package g++-2.95 is not installed.
dpkg: error processing libstdc++2.10-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:

---

### Post by OuTcRy on 2006-04-16
and when i want to install g++ 2.95 it depends on libstdc also....

sudo dpkg -i g++-2.95_2.95.4-22_i386.deb
Selecting previously deselected package g++-2.95.
(Reading database ... 95190 files and directories currently installed.)
Unpacking g++-2.95 (from g++-2.95_2.95.4-22_i386.deb) ...
dpkg: dependency problems prevent configuration of g++-2.95:
 g++-2.95 depends on libstdc++2.10-dev (>= 1:2.95.4); however:
  Package libstdc++2.10-dev is not configured yet.
dpkg: error processing g++-2.95 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 g++-2.95

---

### Post by OuTcRy on 2006-04-16
and i want to configure that....

udo dpkg --configure -a
dpkg: dependency problems prevent configuration of dopewars:
 dopewars depends on libcairo2 (>= 1.0.2-2); however:
  Version of libcairo2 on system is 1.0.2-0ubuntu1.1.
 dopewars depends on libglib2.0-0 (>= 2.8.5); however:
  Version of libglib2.0-0 on system is 2.8.3-0ubuntu1.
 dopewars depends on libpango1.0-0 (>= 1.10.2); however:
  Version of libpango1.0-0 on system is 1.10.1-0ubuntu1.
 dopewars depends on libxrender1 (>= 1:0.9.0.2); however:
  Version of libxrender1 on system is 1:0.9.0-1.
dpkg: error processing dopewars (--configure):
 dependency problems - leaving unconfigured
Setting up libstdc++2.10-dev (2.95.4-22) ...

Setting up g++-2.95 (2.95.4-22) ...

Errors were encountered while processing:
 dopewars

dopewars????? how can i uninstall it...
maybe this can be a solution

---

### Post by htinn on 2006-04-16
Next step: sudo apt-get -f install

---

### Post by OuTcRy on 2006-04-16
sudo apt-get -f install
apt-get: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib/libstdc++.so.6)
apt-get: /lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

---

### Post by towsonu2003 on 2006-04-16
> **OuTcRy]sudo dpkg -i libstdc++2.10-dev_2.95.4-22_i386.deb
(Reading database ... 95130 files and directories currently installed.)
Preparing to replace libstdc++2.10-dev 1:2.95.4-22 (using libstdc++2.10-dev_2.95.4-22_i386.deb) ...
Unpacking replacement libstdc++2.10-dev ...
dpkg: dependency problems prevent configuration of libstdc++2.10-dev:
 libstdc++2.10-dev depends on g++-2.95 (>= 1:2.95.4) said:**
> 

[QUOTE=OuTcRy]and when i want to install g++ 2.95 it depends on libstdc also....

sudo dpkg -i g++-2.95_2.95.4-22_i386.deb
Selecting previously deselected package g++-2.95.
(Reading database ... 95190 files and directories currently installed.)
Unpacking g++-2.95 (from g++-2.95_2.95.4-22_i386.deb) ...
dpkg: dependency problems prevent configuration of g++-2.95:
 g++-2.95 depends on libstdc++2.10-dev (>= 1:2.95.4); however:
  Package libstdc++2.10-dev is not configured yet.
dpkg: error processing g++-2.95 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 g++-2.95
try giving both in the same line? I doubt it will work but...
```

sudo dpkg --purge dopewars #if that doesn't work, try sudo dpkg -r dopewars
sudo dpkg --force-depends -i /path/to/g++-2.95_2.95.4-22_i386.deb 
sudo dpkg --force-depends -i /path/to/libstdc++2.10-dev_2.95.4-22_i386.deb
sudo dpkg --configure -a
```
dopewars is just a game. 

I have to say that this has an extremely high probability of doping/borking your installation for good... Also, read the warnings it spits and try to fix them afterwards (like installing unmet dependencies and configuring all, as per above). 

according to the man page of dpkg (man dpkg), --force-depends changes errors into warnings, hence installing packages of which dependencies are not met etc. this, combined with my ignorance of this issue, increases the chances that your installation will go borked... 

Note to others: OP's apt-get is broken as well.

Note to OP: maybe you should instead open a new thread with title saying "dependency hell" to attract those who know about dependency hells...

---

### Post by htinn on 2006-04-16
I think I'd do a clean reinstall if I ever broke apt-get on my system.

---


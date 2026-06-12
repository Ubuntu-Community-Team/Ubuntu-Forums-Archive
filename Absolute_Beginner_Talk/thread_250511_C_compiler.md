---
title: "C compiler"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by hc2995 on 2006-09-04
Ok im an EX Windows XP user and finally deleted my WINXP partition to user linux. Its a great OS but heres the problem: i cant install anything! when i do ./configure i get " no acceptable C compiler found in $PATH"

for example i v got apache 2.2.3 on the desktop so:
i type:
cd /home/howard/Desktop/httpd-2.2.3
then:
./configure
and i get:

checking for chosen layout... Apache
checking for working mkdir -p... yes
checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
checking target system type... i686-pc-linux-gnuoldld

Configuring Apache Portable Runtime library ...

checking for APR... reconfig
configuring package in srclib/apr now
checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
checking target system type... i686-pc-linux-gnuoldld
Configuring APR library
Platform: i686-pc-linux-gnuoldld
checking for working mkdir -p... yes
APR Version: 1.2.7
checking for chosen layout... apr
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
configure failed for srclib/apr

so what do i do now?

---

### Post by monktbd on 2006-09-04
you need to install the c compiler environment with
> 
sudo apt-get install build-essentials

if you just want to install some software then it is better to take a look at synaptic and repositories first :).

if you really want to compile then you should maybe also have a look at checkinstall. this makes it easier to uninstall it after.

---

### Post by hc2995 on 2006-09-04
ok i typed sudo apt-get install build-essentials and got this:

Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package build-essentials

---

### Post by cantormath on 2006-09-04
> **hc2995 said:**
> ok i typed sudo apt-get install build-essentials and got this:

Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package build-essentials

I think you might have to add the universe repo.
then 
sudo apt-get update
then.....
sudo apt-get install ....whatever.

---

### Post by monktbd on 2006-09-04
> sudo apt-get install build-essential

i think i made a typo there... sorry :)

---

### Post by hc2995 on 2006-09-04
ok after i type that i get:

howard@DELL:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Fetched 3B in 0s (3B/s)
Reading package lists... Done

its a bunch of links.... which one to i click?

---

### Post by hc2995 on 2006-09-04
> **monktbd said:**
> i think i made a typo there... sorry :)


lol lemme try the new one then :D

---

### Post by hc2995 on 2006-09-04
ok then sudo apt-get install build-essential works it updating now :D

EDIT: i ran ./configure again and its worked im goina go read the rest of the documentation for apache thnx to all that helped :D

---

### Post by monktbd on 2006-09-04
Is there a special reason why you want to compile apache instead of using the ready made .deb package in the repositories?

---

### Post by rohan! on 2006-09-04
Just to make that clear, Ubuntu has a package manager called apt that downloads and installs programs. it takes care of dependencies, means that a program can be updated, and is faster than compiling from source.

if you want to install apache then you can just go into synaptic package manager (i think it's in system>admin menu in ubuntu) and find the package in there and install.

another way would be to do it from the terminal by typing
```
sudo apt-get install apache
```
you replace apache in this case with the name of any other package you want to install

to update your system you type
```
sudo apt-get update
sudo apt-get dist-upgrade
```
and hey presto, your system is updated.

---

### Post by hc2995 on 2006-09-05
i did sudo apt-get install apache and this is what i got:

howard@DELL:~$ sudo apt-get install apache
Reading package lists... Done
Building dependency tree... Done
Package apache is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package apache has no installation candidate


any help?

---

### Post by hc2995 on 2006-09-05
Bump Please Help!

---

### Post by monktbd on 2006-09-06
please read in wiki.ubuntu.com about synaptic, installing software and repositories.
knowing these basics will save you a LOT of headaches when it comes to installing programs.

compiling can always come later if you need bleeding edge programs or programs not available in the repositories.

[https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html](https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

to find apache you need to enable extra repositories.
everything you need you will find at the above links.

---


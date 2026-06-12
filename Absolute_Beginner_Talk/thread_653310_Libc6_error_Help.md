---
title: "Libc6 error Help"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by Vamp381 on 2007-12-29
When I want to install New Version of Amsn I get Error

```
Error: Dependency is not satisfiable: Libc6
```

---

### Post by RomeReactor on 2007-12-29
Hi. Libc6 should already be installed in your system; how are you trying to install amsn, from the repositories or downloaded from a website? try running this from the terminal:
```
locate libc6
```
and please post the output.

---

### Post by Vamp381 on 2007-12-29
```
pavle@pavlee:~$ locate libc6
/var/lib/dpkg/info/libc6-i686.list
/var/lib/dpkg/info/libc6.list
/var/lib/dpkg/info/libc6.shlibs
/var/lib/dpkg/info/libc6.preinst
/var/lib/dpkg/info/libc6.md5sums
/var/lib/dpkg/info/libc6.conffiles
/var/lib/dpkg/info/libc6-dev.md5sums
/var/lib/dpkg/info/libc6-i686.postinst
/var/lib/dpkg/info/libc6-i686.postrm
/var/lib/dpkg/info/libc6-i686.shlibs
/var/lib/dpkg/info/libc6-i686.preinst
/var/lib/dpkg/info/libc6.postrm
/var/lib/dpkg/info/libc6.postinst
/var/lib/dpkg/info/libc6-i686.md5sums
/var/lib/dpkg/info/libc6-dev.list
/usr/lib/libapt-inst-libc6.4-6.so.1.1.0
/usr/lib/libapt-inst-libc6.4-6.so.1.1
/usr/lib/libapt-pkg-libc6.4-6.so.3.53
/usr/lib/libapt-pkg-libc6.4-6.so.3.53.0
/usr/share/doc/libc6-dev
/usr/share/doc/libc6-dev/changelog.Debian.gz
/usr/share/doc/libc6-dev/copyright
/usr/share/doc/libc6-i686
/usr/share/doc/libc6-i686/changelog.Debian.gz
/usr/share/doc/libc6-i686/log-test-i686-linux-i686.gz
/usr/share/doc/libc6-i686/copyright
/usr/share/doc/libc6
/usr/share/doc/libc6/NEWS.gz
/usr/share/doc/libc6/CONFORMANCE.gz
/usr/share/doc/libc6/FAQ.gz
/usr/share/doc/libc6/changelog.Debian.gz
/usr/share/doc/libc6/README.linuxthreads.gz
/usr/share/doc/libc6/ChangeLog.linuxthreads.gz
/usr/share/doc/libc6/BUGS
/usr/share/doc/libc6/log-test-i486-linux-gnu-libc.gz
/usr/share/doc/libc6/README.hesiod.gz
/usr/share/doc/libc6/changelog.gz
/usr/share/doc/libc6/TODO
/usr/share/doc/libc6/README.Debian.gz
/usr/share/doc/libc6/NAMESPACE
/usr/share/doc/libc6/NOTES.gz
/usr/share/doc/libc6/PROJECTS.gz
/usr/share/doc/libc6/README.gz
/usr/share/doc/libc6/copyright

```

I download it from:

```
http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=amsn&searchon=names&version=all&release=all&exact=1
```

---

### Post by RomeReactor on 2007-12-29
Do you have internet connection on your Feisty system? you can install amsn from the repositories by looking for it in Add/Remove or Synaptic; or from the command line:
```
sudo apt-get update
```
then
```
sudo apt-get install amsn
```

Also, please post your sources.list:
```
cat /etc/apt/sources.list
```

---

### Post by Vamp381 on 2007-12-30
Source List:

```
pavle@pavlee:~$ cat /etc/apt/sources.list
# deb http://www.getautomatix.com/apt feisty main

#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt feisty main
deb-src http://download.tuxfamily.org/syzygy42/ feisty avant-window-navigator

deb http://gandalfn.club.fr/ubuntu edgy dev

deb http://download.tuxfamily.org/syzygy42/ feisty avant-window-navigator



deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse #Added by software-properties

deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted universe multiverse #Added by software-properties

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse #Added by software-properties

deb-src http://archive.ubuntu.com/ubuntu feisty main restricted universe multiverse #Added by software-properties
deb http://archive.ubuntu.com/ubuntu feisty main restricted universe multiverse
#AUTOMATIX REPOS END
deb http://archive.ubuntustudio.org/ubuntustudio feisty main
deb http://hendrik.kaju.pri.ee/ubuntu feisty screenlets
deb http://packages.dfreer.org feisty main
deb http://repository.debuntu.org/ feisty multiverse
deb-src http://repository.debuntu.org/ feisty multiverse


deb http://ppa.dogfood.launchpad.net/amaranth/ubuntu feisty main
deb http://ppa.launchpad.net/amaranth/ubuntu feisty main

# LG3D repsoitories
deb http://javadesktop.org/lg3d/debian stable contrib
deb http://www.kiberpipa.org/~muzzol/cinelerra/feisty-i386/ ./

deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy





```


Btw i have one version of Amsn installed (some old) and when i enter Amsn now its say.
"Newer version 0.97 avaliable for download".

---


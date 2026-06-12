---
title: "Help with installing RaLink 2561 drivers!!!!"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by Koech on 2006-05-16
I have been trying to install RaLink drivers only to end at the 'make all' command. I get a msg: 
questa@Questa:~/RT61_Linux_STA_Drv1.0.4.0/Module$ make all
bash: make: command not found
What is the way forward.
Please help.

---

### Post by Matze on 2006-05-16
Please install the "build-essential" package with synaptics!

---

### Post by tonyr on 2006-05-16
Find out if **make** is installed:
```

ls -l /usr/bin/make
or just
/usr/bin/make

```
It it isn't, install package **build-essential** and try again.

---

### Post by nalmeth on 2006-05-16
sudo apt-get install build-essential

---

### Post by Koech on 2006-05-16
This is what I got:

questa@Questa:~$ ls -l /usr/bin/make
ls: /usr/bin/make: No such file or directory
questa@Questa:~$ /usr/bin/make
bash: /usr/bin/make: No such file or directory
questa@Questa:~$ sudo apt-get install build-essential
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
questa@Questa:~$

Is there a way out?

---

### Post by Matze on 2006-05-16
Hm...please let only one package-manager run at the same time!
Close every window, you've opened!
Then open a terminal and type:

```
sudo apt-get update
```

Then:
```
sudo apt-get install build-essential
```

---

### Post by Koech on 2006-05-16
I think ther's sth I am doing wrong. I got this:

questa@Questa:~$ sudo apt-get update
Errhttp://au.archive.ubuntu.com dapper Release.gpg
  Temporary failure resolving ‘au.archive.ubuntu.com’
Errhttp://au.archive.ubuntu.com dapper-updates Release.gpg
  Temporary failure resolving ‘au.archive.ubuntu.com’
Errhttp://security.ubuntu.com dapper-security Release.gpg
  Temporary failure resolving ‘security.ubuntu.com’
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Temporary failure resolving ‘au.archive.ubuntu.com’
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Temporary failure resolving ‘au.archive.ubuntu.com’
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Temporary failure resolving ‘security.ubuntu.com’
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
questa@Questa:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  binutils cpp cpp-4.0 dpkg-dev g++ g++-4.0 gcc gcc-4.0 libc6 libc6-dev
  libc6-i686 libstdc++6-4.0-dev linux-kernel-headers make
Suggested packages:
  binutils-doc cpp-doc gcc-4.0-locales debian-keyring gcc-4.0-doc lib64stdc++6
  manpages-dev autoconf automake1.9 libtool flex bison gcc-doc libc6-dev-amd64
  lib64gcc1 glibc-doc libstdc++6-4.0-doc stl-manual
Recommended packages:
  libmudflap0-dev
The following NEW packages will be installed
  binutils build-essential cpp cpp-4.0 dpkg-dev g++ g++-4.0 gcc gcc-4.0
  libc6-dev libstdc++6-4.0-dev linux-kernel-headers make
The following packages will be upgraded:
  libc6 libc6-i686
2 upgraded, 13 newly installed, 0 to remove and 318 not upgraded.
Need to get 12.0MB/17.7MB of archives.
After unpacking 47.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Errhttp://au.archive.ubuntu.com dapper/main binutils 2.16.1cvs20060117-1ubuntu2
  Temporary failure resolving ‘au.archive.ubuntu.com’
Errhttp://au.archive.ubuntu.com dapper/main linux-kernel-headers 2.6.11.2-0ubuntu17
  Temporary failure resolving ‘au.archive.ubuntu.com’
Errhttp://au.archive.ubuntu.com dapper/main libc6-dev 2.3.6-0ubuntu18
  Temporary failure resolving ‘au.archive.ubuntu.com’
Errhttp://au.archive.ubuntu.com dapper/main cpp-4.0 4.0.3-1ubuntu5
  Temporary failure resolving ‘au.archive.ubuntu.com’
Errhttp://au.archive.ubuntu.com dapper/main cpp 4:4.0.3-1
  Temporary failure resolving ‘au.archive.ubuntu.com’
Errhttp://au.archive.ubuntu.com dapper/main gcc-4.0 4.0.3-1ubuntu5
  Temporary failure resolving ‘au.archive.ubuntu.com’
Errhttp://au.archive.ubuntu.com dapper/main gcc 4:4.0.3-1
  Temporary failure resolving ‘au.archive.ubuntu.com’
Errhttp://au.archive.ubuntu.com dapper/main libstdc++6-4.0-dev 4.0.3-1ubuntu5
  Temporary failure resolving ‘au.archive.ubuntu.com’
Errhttp://au.archive.ubuntu.com dapper/main g++-4.0 4.0.3-1ubuntu5
  Temporary failure resolving ‘au.archive.ubuntu.com’
Errhttp://au.archive.ubuntu.com dapper/main g++ 4:4.0.3-1
  Temporary failure resolving ‘au.archive.ubuntu.com’
Errhttp://au.archive.ubuntu.com dapper/main make 3.80+3.81.b4-1
  Temporary failure resolving ‘au.archive.ubuntu.com’
Errhttp://au.archive.ubuntu.com dapper/main dpkg-dev 1.13.11ubuntu6
  Temporary failure resolving ‘au.archive.ubuntu.com’
Errhttp://au.archive.ubuntu.com dapper/main build-essential 11.1
  Temporary failure resolving ‘au.archive.ubuntu.com’
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/b/binutils/binutils_2.16.1cvs20060117-1ubuntu2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/b/binutils/binutils_2.16.1cvs20060117-1ubuntu2_i386.deb)  Temporary failure resolving ‘au.archive.ubuntu.com’
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/l/linux-kernel-headers/linux-kernel-headers_2.6.11.2-0ubuntu17_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/l/linux-kernel-headers/linux-kernel-headers_2.6.11.2-0ubuntu17_i386.deb)  Temporary failure resolving ‘au.archive.ubuntu.com’
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.3.6-0ubuntu18_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.3.6-0ubuntu18_i386.deb)  Temporary failure resolving ‘au.archive.ubuntu.com’
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.0/cpp-4.0_4.0.3-1ubuntu5_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.0/cpp-4.0_4.0.3-1ubuntu5_i386.deb)  Temporary failure resolving ‘au.archive.ubuntu.com’
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/cpp_4.0.3-1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/cpp_4.0.3-1_i386.deb)  Temporary failure resolving ‘au.archive.ubuntu.com’
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.0/gcc-4.0_4.0.3-1ubuntu5_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.0/gcc-4.0_4.0.3-1ubuntu5_i386.deb)  Temporary failure resolving ‘au.archive.ubuntu.com’
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/gcc_4.0.3-1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/gcc_4.0.3-1_i386.deb)  Temporary failure resolving ‘au.archive.ubuntu.com’
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.0/libstdc++6-4.0-dev_4.0.3-1ubuntu5_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.0/libstdc++6-4.0-dev_4.0.3-1ubuntu5_i386.deb)  Temporary failure resolving ‘au.archive.ubuntu.com’
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.0/g++-4.0_4.0.3-1ubuntu5_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.0/g++-4.0_4.0.3-1ubuntu5_i386.deb)  Temporary failure resolving ‘au.archive.ubuntu.com’
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/g++_4.0.3-1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/g++_4.0.3-1_i386.deb)  Temporary failure resolving ‘au.archive.ubuntu.com’
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/m/make/make_3.80+3.81.b4-1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/m/make/make_3.80+3.81.b4-1_i386.deb)  Temporary failure resolving ‘au.archive.ubuntu.com’
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.13.11ubuntu6_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.13.11ubuntu6_all.deb)  Temporary failure resolving ‘au.archive.ubuntu.com’
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_11.1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_11.1_i386.deb)  Temporary failure resolving ‘au.archive.ubuntu.com’
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
questa@Questa:~$

---

### Post by Koech on 2006-05-16
I think ther's sth I am doing wrong. I got this:

questa@Questa:~$ sudo apt-get update
Errhttp://au.archive.ubuntu.com dapper Release.gpg
  Temporary failure resolving ‘au.archive.ubuntu.com’
Errhttp://au.archive.ubuntu.com dapper-updates Release.gpg
  Temporary failure resolving ‘au.archive.ubuntu.com’
Errhttp://security.ubuntu.com dapper-security Release.gpg
  Temporary failure resolving ‘security.ubuntu.com’
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Temporary failure resolving ‘au.archive.ubuntu.com’
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Temporary failure resolving ‘au.archive.ubuntu.com’
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Temporary failure resolving ‘security.ubuntu.com’
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
questa@Questa:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  binutils cpp cpp-4.0 dpkg-dev g++ g++-4.0 gcc gcc-4.0 libc6 libc6-dev
  libc6-i686 libstdc++6-4.0-dev linux-kernel-headers make
Suggested packages:
  binutils-doc cpp-doc gcc-4.0-locales debian-keyring gcc-4.0-doc lib64stdc++6
  manpages-dev autoconf automake1.9 libtool flex bison gcc-doc libc6-dev-amd64
  lib64gcc1 glibc-doc libstdc++6-4.0-doc stl-manual
Recommended packages:
  libmudflap0-dev
The following NEW packages will be installed
  binutils build-essential cpp cpp-4.0 dpkg-dev g++ g++-4.0 gcc gcc-4.0
  libc6-dev libstdc++6-4.0-dev linux-kernel-headers make
The following packages will be upgraded:
  libc6 libc6-i686
2 upgraded, 13 newly installed, 0 to remove and 318 not upgraded.
Need to get 12.0MB/17.7MB of archives.
After unpacking 47.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Errhttp://au.archive.ubuntu.com dapper/main binutils 2.16.1cvs20060117-1ubuntu2
  Temporary failure resolving ‘au.archive.ubuntu.com’
Errhttp://au.archive.ubuntu.com dapper/main linux-kernel-headers 2.6.11.2-0ubuntu17
  Temporary failure resolving ‘au.archive.ubuntu.com’
Errhttp://au.archive.ubuntu.com dapper/main libc6-dev 2.3.6-0ubuntu18
  Temporary failure resolving ‘au.archive.ubuntu.com’
Errhttp://au.archive.ubuntu.com dapper/main cpp-4.0 4.0.3-1ubuntu5
  Temporary failure resolving ‘au.archive.ubuntu.com’
Errhttp://au.archive.ubuntu.com dapper/main cpp 4:4.0.3-1
  Temporary failure resolving ‘au.archive.ubuntu.com’
Errhttp://au.archive.ubuntu.com dapper/main gcc-4.0 4.0.3-1ubuntu5
  Temporary failure resolving ‘au.archive.ubuntu.com’
Errhttp://au.archive.ubuntu.com dapper/main gcc 4:4.0.3-1
  Temporary failure resolving ‘au.archive.ubuntu.com’
Errhttp://au.archive.ubuntu.com dapper/main libstdc++6-4.0-dev 4.0.3-1ubuntu5
  Temporary failure resolving ‘au.archive.ubuntu.com’
Errhttp://au.archive.ubuntu.com dapper/main g++-4.0 4.0.3-1ubuntu5
  Temporary failure resolving ‘au.archive.ubuntu.com’
Errhttp://au.archive.ubuntu.com dapper/main g++ 4:4.0.3-1
  Temporary failure resolving ‘au.archive.ubuntu.com’
Errhttp://au.archive.ubuntu.com dapper/main make 3.80+3.81.b4-1
  Temporary failure resolving ‘au.archive.ubuntu.com’
Errhttp://au.archive.ubuntu.com dapper/main dpkg-dev 1.13.11ubuntu6
  Temporary failure resolving ‘au.archive.ubuntu.com’
Errhttp://au.archive.ubuntu.com dapper/main build-essential 11.1
  Temporary failure resolving ‘au.archive.ubuntu.com’
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/b/binutils/binutils_2.16.1cvs20060117-1ubuntu2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/b/binutils/binutils_2.16.1cvs20060117-1ubuntu2_i386.deb)  Temporary failure resolving ‘au.archive.ubuntu.com’
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/l/linux-kernel-headers/linux-kernel-headers_2.6.11.2-0ubuntu17_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/l/linux-kernel-headers/linux-kernel-headers_2.6.11.2-0ubuntu17_i386.deb)  Temporary failure resolving ‘au.archive.ubuntu.com’
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.3.6-0ubuntu18_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.3.6-0ubuntu18_i386.deb)  Temporary failure resolving ‘au.archive.ubuntu.com’
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.0/cpp-4.0_4.0.3-1ubuntu5_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.0/cpp-4.0_4.0.3-1ubuntu5_i386.deb)  Temporary failure resolving ‘au.archive.ubuntu.com’
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/cpp_4.0.3-1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/cpp_4.0.3-1_i386.deb)  Temporary failure resolving ‘au.archive.ubuntu.com’
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.0/gcc-4.0_4.0.3-1ubuntu5_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.0/gcc-4.0_4.0.3-1ubuntu5_i386.deb)  Temporary failure resolving ‘au.archive.ubuntu.com’
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/gcc_4.0.3-1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/gcc_4.0.3-1_i386.deb)  Temporary failure resolving ‘au.archive.ubuntu.com’
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.0/libstdc++6-4.0-dev_4.0.3-1ubuntu5_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.0/libstdc++6-4.0-dev_4.0.3-1ubuntu5_i386.deb)  Temporary failure resolving ‘au.archive.ubuntu.com’
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.0/g++-4.0_4.0.3-1ubuntu5_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.0/g++-4.0_4.0.3-1ubuntu5_i386.deb)  Temporary failure resolving ‘au.archive.ubuntu.com’
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/g++_4.0.3-1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/g++_4.0.3-1_i386.deb)  Temporary failure resolving ‘au.archive.ubuntu.com’
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/m/make/make_3.80+3.81.b4-1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/m/make/make_3.80+3.81.b4-1_i386.deb)  Temporary failure resolving ‘au.archive.ubuntu.com’
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.13.11ubuntu6_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.13.11ubuntu6_all.deb)  Temporary failure resolving ‘au.archive.ubuntu.com’
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_11.1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_11.1_i386.deb)  Temporary failure resolving ‘au.archive.ubuntu.com’
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
questa@Questa:~$

---

### Post by Matze on 2006-05-16
Hm...looks like au.archive.ubuntu.com is down!
Could you please your sources.list?
You find it in /etc/apt/sources.list!

---

### Post by Koech on 2006-05-16
From sources.list:

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by Matze on 2006-05-16
Ok, please try the following:

Chance all "au" in the URL's to "us".
After that, do again a "sudo apt-get update"...
Anymore errors?

---

### Post by Koech on 2006-05-16
I've managed to get my way thro using synaptics

---

### Post by Matze on 2006-05-16
Ah, ok...then the "au" servers seem to be up again... :-)

---

### Post by Koech on 2006-05-16
I think I'll manage. However i tried changingau. to us. but no permissions..blah..blah..
But I'm grateful for I now have a general idea of what to do.
Cheers!:D

---

### Post by Matze on 2006-05-16
No Prob :)

To solve the permission problem:
In a terminal type:
```
gksu gedit /etc/apt/sources.list
```

Good luck with installing the WLAN-Drivers!
And read the included README and Installnotes...It helped me very much to install these drivers!

---

### Post by Koech on 2006-05-16
Thanks again man!:-D

---


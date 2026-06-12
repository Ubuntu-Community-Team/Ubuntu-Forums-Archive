---
title: "apt-get update  and apt-get install build-essential gives errors, help!"
date: 2006-05-06
forum: Absolute Beginner Talk
---

### Post by ajb on 2006-05-06
So basically, I get errors when I run sudo apt-get update, and errors when I run apt-get install build-essential.  What should I do?  I have no idea what any of this means.  I'm running breezy...




[I]aaron@MR-SPOCK:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
Get:4 [ftp://ftp.real-time.com](ftp://ftp.real-time.com) breezy Release.gpg
Ign [ftp://ftp.real-time.com](ftp://ftp.real-time.com) breezy Release.gpg
Get:5 [ftp://ftp.real-time.com](ftp://ftp.real-time.com) breezy Release
Ign [ftp://ftp.real-time.com](ftp://ftp.real-time.com) breezy Release
Get:6 [ftp://ftp.real-time.com](ftp://ftp.real-time.com) breezy/custom Packages
Ign [ftp://ftp.real-time.com](ftp://ftp.real-time.com) breezy/custom Packages
Get:7 [ftp://ftp.real-time.com](ftp://ftp.real-time.com) breezy/custom Sources
Ign [ftp://ftp.real-time.com](ftp://ftp.real-time.com) breezy/custom Sources
Get:8 [ftp://ftp.real-time.com](ftp://ftp.real-time.com) breezy/custom Packages
Err [ftp://ftp.real-time.com](ftp://ftp.real-time.com) breezy/custom Packages
  Unable to fetch file, server said '/linux/real-time-debpool/dists/breezy/custo m/binary-i386/Packages.gz: No such file or directory  '
Get:9 [ftp://ftp.real-time.com](ftp://ftp.real-time.com) breezy/custom Sources
Err [ftp://ftp.real-time.com](ftp://ftp.real-time.com) breezy/custom Sources
  Unable to fetch file, server said '/linux/real-time-debpool/dists/breezy/custo m/source/Sources.gz: No such file or directory  '
Fetched 3B in 13s (0B/s)
Failed to fetch [ftp://ftp.real-time.com/linux/real-time-debpool/dists/breezy/cus](ftp://ftp.real-time.com/linux/real-time-debpool/dists/breezy/cus) tom/binary-i386/Packages.gz  Unable to fetch file, server said '/linux/real-time -debpool/dists/breezy/custom/binary-i386/Packages.gz: No such file or directory  '
Failed to fetch [ftp://ftp.real-time.com/linux/real-time-debpool/dists/breezy/cus](ftp://ftp.real-time.com/linux/real-time-debpool/dists/breezy/cus) tom/source/Sources.gz  Unable to fetch file, server said '/linux/real-time-debpo ol/dists/breezy/custom/source/Sources.gz: No such file or directory  '
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?
aaron@MR-SPOCK:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
Get:4 [ftp://ftp.real-time.com](ftp://ftp.real-time.com) breezy Release.gpg
Ign [ftp://ftp.real-time.com](ftp://ftp.real-time.com) breezy Release.gpg
Get:5 [ftp://ftp.real-time.com](ftp://ftp.real-time.com) breezy Release
Ign [ftp://ftp.real-time.com](ftp://ftp.real-time.com) breezy Release
Get:6 [ftp://ftp.real-time.com](ftp://ftp.real-time.com) breezy/custom Packages
Ign [ftp://ftp.real-time.com](ftp://ftp.real-time.com) breezy/custom Packages
Get:7 [ftp://ftp.real-time.com](ftp://ftp.real-time.com) breezy/custom Sources
Ign [ftp://ftp.real-time.com](ftp://ftp.real-time.com) breezy/custom Sources
99% [Packages gzip 0] [Query]                                       14.5kB/s 0s
gzip: stdin: unexpected end of file
Err [ftp://ftp.real-time.com](ftp://ftp.real-time.com) breezy/custom Packages
  Sub-process gzip returned an error code (1)
99% [Sources gzip 0]                                                14.5kB/s 0s
gzip: stdin: unexpected end of file
Err [ftp://ftp.real-time.com](ftp://ftp.real-time.com) breezy/custom Sources
  Sub-process gzip returned an error code (1)
Fetched 3B in 11s (0B/s)
Failed to fetch [ftp://ftp.real-time.com/linux/real-time-debpool/dists/breezy/cus](ftp://ftp.real-time.com/linux/real-time-debpool/dists/breezy/cus) tom/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch [ftp://ftp.real-time.com/linux/real-time-debpool/dists/breezy/cus](ftp://ftp.real-time.com/linux/real-time-debpool/dists/breezy/cus) tom/source/Sources.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used  instead.
aaron@MR-SPOCK:~$ sudo apt-get install build-essentials
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [ftp://ftp.real-time.com](ftp://ftp.real-time.com) breezy/custom Packa ges (/var/lib/apt/lists/ftp.real-time.com_linux_real-time-debpool_dists_breezy_c ustom_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package build-essentials
aaron@MR-SPOCK:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  binutils dpkg-dev g++ g++-4.0 gcc gcc-4.0 libc6-dev libstdc++6-4.0-dev
  linux-kernel-headers make
Suggested packages:
  binutils-doc debian-keyring gcc-4.0-doc lib64stdc++6 manpages-dev autoconf
  automake1.9 libtool flex bison gcc-doc gcc-4.0-locales libc6-dev-amd64
  lib64gcc1 glibc-doc libstdc++6-4.0-doc stl-manual
Recommended packages:
  libmudflap0-dev
The following NEW packages will be installed:
  binutils build-essential dpkg-dev g++ g++-4.0 gcc gcc-4.0 libc6-dev
  libstdc++6-4.0-dev linux-kernel-headers make
0 upgraded, 11 newly installed, 0 to remove and 0 not upgraded.
Need to get 2792kB/10.2MB of archives.
After unpacking 41.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main libc6-dev 2.3.5-1ubuntu12 .5.10.1 [2792kB]
Fetched 2792kB in 16s (171kB/s)
W: Couldn't stat source package list [ftp://ftp.real-time.com](ftp://ftp.real-time.com) breezy/custom Packa ges (/var/lib/apt/lists/ftp.real-time.com_linux_real-time-debpool_dists_breezy_c ustom_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.real-time.com](ftp://ftp.real-time.com) breezy/custom Packa ges (/var/lib/apt/lists/ftp.real-time.com_linux_real-time-debpool_dists_breezy_c ustom_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.real-time.com](ftp://ftp.real-time.com) breezy/custom Packa ges (/var/lib/apt/lists/ftp.real-time.com_linux_real-time-debpool_dists_breezy_c ustom_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.real-time.com](ftp://ftp.real-time.com) breezy/custom Packa ges (/var/lib/apt/lists/ftp.real-time.com_linux_real-time-debpool_dists_breezy_c ustom_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.real-time.com](ftp://ftp.real-time.com) breezy/custom Packa ges (/var/lib/apt/lists/ftp.real-time.com_linux_real-time-debpool_dists_breezy_c ustom_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.real-time.com](ftp://ftp.real-time.com) breezy/custom Packa ges (/var/lib/apt/lists/ftp.real-time.com_linux_real-time-debpool_dists_breezy_c ustom_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.real-time.com](ftp://ftp.real-time.com) breezy/custom Packa ges (/var/lib/apt/lists/ftp.real-time.com_linux_real-time-debpool_dists_breezy_c ustom_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.real-time.com](ftp://ftp.real-time.com) breezy/custom Packa ges (/var/lib/apt/lists/ftp.real-time.com_linux_real-time-debpool_dists_breezy_c ustom_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.real-time.com](ftp://ftp.real-time.com) breezy/custom Packa ges (/var/lib/apt/lists/ftp.real-time.com_linux_real-time-debpool_dists_breezy_c ustom_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.real-time.com](ftp://ftp.real-time.com) breezy/custom Packa ges (/var/lib/apt/lists/ftp.real-time.com_linux_real-time-debpool_dists_breezy_c ustom_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.real-time.com](ftp://ftp.real-time.com) breezy/custom Packa ges (/var/lib/apt/lists/ftp.real-time.com_linux_real-time-debpool_dists_breezy_c ustom_binary-i386_Packages) - stat (2 No such file or directory)

Preconfiguring packages ...
Selecting previously deselected package binutils.
(Reading database ... 61341 files and directories currently installed.)
Unpacking binutils (from .../binutils_2.16.1-2ubuntu6_i386.deb) ...
Selecting previously deselected package linux-kernel-headers.
Unpacking linux-kernel-headers (from .../linux-kernel-headers_2.6.11.2-0ubuntu13 _i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.3.5-1ubuntu12.5.10.1_i386.deb) ...
Selecting previously deselected package gcc-4.0.
Unpacking gcc-4.0 (from .../gcc-4.0_4.0.1-4ubuntu9_i386.deb) ...
Selecting previously deselected package gcc.
Unpacking gcc (from .../gcc_4%3a4.0.1-3_i386.deb) ...
Selecting previously deselected package libstdc++6-4.0-dev.
Unpacking libstdc++6-4.0-dev (from .../libstdc++6-4.0-dev_4.0.1-4ubuntu9_i386.de b) ...
Selecting previously deselected package g++-4.0.
Unpacking g++-4.0 (from .../g++-4.0_4.0.1-4ubuntu9_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.0.1-3_i386.deb) ...
Selecting previously deselected package make.
Unpacking make (from .../archives/make_3.80-9_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.13.10ubuntu4_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.1_i386.deb) ...
Setting up binutils (2.16.1-2ubuntu6) ...

Setting up linux-kernel-headers (2.6.11.2-0ubuntu13) ...
Setting up libc6-dev (2.3.5-1ubuntu12.5.10.1) ...
Setting up gcc-4.0 (4.0.1-4ubuntu9) ...
Setting up gcc (4.0.1-3) ...

Setting up make (3.80-9) ...

Setting up dpkg-dev (1.13.10ubuntu4) ...
Setting up libstdc++6-4.0-dev (4.0.1-4ubuntu9) ...
Setting up g++-4.0 (4.0.1-4ubuntu9) ...
Setting up g++ (4.0.1-3) ...

Setting up build-essential (11.1) ...
W: Couldn't stat source package list [ftp://ftp.real-time.com](ftp://ftp.real-time.com) breezy/custom Packa ges (/var/lib/apt/lists/ftp.real-time.com_linux_real-time-debpool_dists_breezy_c ustom_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
aaron@MR-SPOCK:~$


[/I]

---

### Post by linear on 2006-05-06
In sources.list, comment out all lines containing "ftp.real-time.com". The problem is with that one repository - do you have a reason to include it?. It looks like everything else was OK.

---

### Post by Sef on 2006-05-06
To comment out a line just put # before the line.

Example:

#/var/lib/apt/lists/ftp.real-time.com_linux_real-time-debpool_dists_breezy_c ustom_binary-i386_Packages

That line won't be read now.

---

### Post by johnc4510 on 2006-05-06
correct

---

### Post by Qrk on 2006-05-07
Also, you cannot use apt-get from the terminal while you have synaptic or another package manager open. It looked like there was an error message in that mess from that issue too.

---


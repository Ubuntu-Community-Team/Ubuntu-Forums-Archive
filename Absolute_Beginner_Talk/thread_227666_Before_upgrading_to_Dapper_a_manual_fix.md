---
title: "Before upgrading to Dapper a manual fix"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2006-08-02
I have learned that I need to make a new partition on the hard disk for the /home directory. Following the instruction at:

[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

sudo aptitude update && sudo aptitude install gparted

the terminal responded as follows:

"The following packages will be upgraded:
  binutils cpp-4.0 g++-4.0 gcc-4.0 gcc-4.0-base gettext java-common
  java-gcj-compat libasound2 libcairo2 libfreetype6 libgcc1
  libgconfmm-2.6-1c2 libglib2.0-0 libglib2.0-data libglib2.0-dev
  libpango1.0-0 libpango1.0-common libstdc++6 libstdc++6-4.0-dev
20 packages upgraded, 13 newly installed, 15 to remove and 884 not upgraded.
Need to get 0B of archives. After unpacking 21.4MB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Error!
E: I wasn't able to locate file for the hl1440lpr package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?
mark@lexington:~$"

Please tell me how to "manually fix" and what package to fix and where and how to find this file or package.

---

### Post by kriding on 2006-08-02
Try the command again, but ensure you have no other instances of synaptic or adept running, as this line:

> 
E: Couldn't lock list directory..are you root?


suggests that you have your package manager running.

---

### Post by Mark_in_Hollywood on 2006-08-02
OK, the computer was shut down (all night). This morning I fired it up and did as you suggested and got the same result. I am pasting some of what flashed by in the Terminal screen below:

mark@lexington:~$ sudo aptitude update && sudo aptitude install gparted
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done

[many lines of text removed]

20 packages upgraded, 13 newly installed, 15 to remove and 884 not upgraded.
Need to get 0B of archives. After unpacking 21.4MB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Error!
E: I wasn't able to locate file for the hl1440lpr package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?
mark@lexington:~$

---

### Post by [S|G] on 2006-08-02
You could try to use apt-get:
```

sudo apt-get update;sudo apt-get install -f; sudo apt-get install gparted

```

---

### Post by [S|G] on 2006-08-02
double post sorry... btw, it seems that I'm double-posting every time. Any problems with the forum or is it my browser?

---

### Post by confused57 on 2006-08-02
Are you running the commands from the LiveCD to install gparted, as suggested in the psychocats.net link?  Maybe you already know this, but you can't do any partitioning on a mounted drive(partition?), I'm definitely no partitioning expert..  This probably isn't your problem, but thought I'd mention it.

---

### Post by Mark_in_Hollywood on 2006-08-02
> **'[S|G] said:**
> You could try to use apt-get:
```

sudo apt-get update;sudo apt-get install -f; sudo apt-get install gparted

```

What follows below is the result of sudo-ing your command sequence above. Please note that several times a failure occurs, and I'm pasting them immediately below to help wade through the damage:

gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
  Sub-process gzip returned an error code (1)
**and**
E: Some index files failed to download, they have been ignored, or old ones used instead.
**and**
Removing hl1440lpr ...
/var/lib/dpkg/info/hl1440lpr.postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: error processing hl1440lpr (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 hl1440lpr
E: Sub-process /usr/bin/dpkg returned an error code (1)
**and**
Removing hl1440lpr ...
/var/lib/dpkg/info/hl1440lpr.postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: error processing hl1440lpr (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 hl1440lpr
E: Sub-process /usr/bin/dpkg returned an error code (1)

Let me know what you think, please.
[B]
Entire lines, below:[/B]


mark@lexington:~$ sudo apt-get update;sudo apt-get install -f; sudo apt-get install gparted
Password:
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release [30.9kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages [65.1kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources [44.9kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources [336kB]
99% [8 Sources gzip 0] [Waiting for headers]                         5217B/s 0s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
  Sub-process gzip returned an error code (1)
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [30.9kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [44.2kB]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages [4275B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources [11.0kB]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources [974B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [10.6kB]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages [2041B]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources [1290B]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources [521B]
Fetched 247kB in 53s (4620B/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  hl1440lpr
0 upgraded, 0 newly installed, 1 to remove and 904 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 86155 files and directories currently installed.)
Removing hl1440lpr ...
/var/lib/dpkg/info/hl1440lpr.postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: error processing hl1440lpr (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 hl1440lpr
E: Sub-process /usr/bin/dpkg returned an error code (1)
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  binutils cpp-4.0 g++-4.0 gcc-4.0 gcc-4.0-base gcj-4.1-base gettext gij-4.1
  java-common java-gcj-compat libasound2 libcairo2 libfreetype6 libgcc1
  libgcj7 libgcj7-jar libgconfmm-2.6-1c2 libglib2.0-0 libglib2.0-data
  libglib2.0-dev libglibmm-2.4-1c2a libgtkmm-2.4-1c2a libpango1.0-0
  libpango1.0-common libparted1.6-13 libsigc++-2.0-0c2a libstdc++6
  libstdc++6-4.0-dev
Suggested packages:
  binutils-doc gcc-4.0-locales gcc-4.0-doc lib64stdc++6 libc6-dev-amd64
  lib64gcc1 cvs gettext-doc gcj-4.1 libgcj7-awt equivs libasound2-plugins
  libfreetype6-dev lib32gcj7-dbg libglib2.0-doc ttf-thryomanes
  libparted1.6-dev libparted1.6-i18n libstdc++6-4.0-doc stl-manual
Recommended packages:
  libmudflap0-dev curl ntfsprogs hfsutils libgcj7-src libgcj6-src
The following packages will be REMOVED:
  gij-4.0 hardware-monitor hl1440lpr libgcj6 libgcj6-common libglademm-2.4-1c2
  libglibmm-2.4-1c2 libgnome-vfsmm-2.6-1c2 libgnomecanvasmm-2.6-1c2
  libgnomemm-2.6-1c2 libgnomeuimm-2.6-1c2 libgtkmm-2.4-1c2 libsigc++-2.0-0c2
The following NEW packages will be installed:
  gcj-4.1-base gij-4.1 gparted libgcj7 libgcj7-jar libglibmm-2.4-1c2a
  libgtkmm-2.4-1c2a libparted1.6-13 libsigc++-2.0-0c2a
The following packages will be upgraded:
  binutils cpp-4.0 g++-4.0 gcc-4.0 gcc-4.0-base gettext java-common
  java-gcj-compat libasound2 libcairo2 libfreetype6 libgcc1 libgconfmm-2.6-1c2
  libglib2.0-0 libglib2.0-data libglib2.0-dev libpango1.0-0 libpango1.0-common
  libstdc++6 libstdc++6-4.0-dev
20 upgraded, 9 newly installed, 13 to remove and 884 not upgraded.
1 not fully installed or removed.
Need to get 0B/25.3MB of archives.
After unpacking 1524kB disk space will be freed.
Do you want to continue [Y/n]? Y
Media change: please insert the disc labeled
 'Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)'
in the drive '/cdrom/' and press enter


Preconfiguring packages ...
(Reading database ... 86155 files and directories currently installed.)
Removing hl1440lpr ...
/var/lib/dpkg/info/hl1440lpr.postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: error processing hl1440lpr (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 hl1440lpr
E: Sub-process /usr/bin/dpkg returned an error code (1)
mark@lexington:~$

---

### Post by Mark_in_Hollywood on 2006-08-04
Success!

mark@lexington:~$ sudo chmod +x /etc/init.d/lpd
Password:
mark@lexington:~$ sudo chmod +x /etc/init.d/lpd
mark@lexington:~$ sudo touch /etc/init.d/lpd
mark@lexington:~$ dpkg --remove hl1440lpr
dpkg: requested operation requires superuser privilege
mark@lexington:~$ sudo dpkg --remove hl1440lpr
(Reading database ... 86155 files and directories currently installed.)
Removing hl1440lpr 

This removed hl1440lpr and after that I used Application/Add Applications to add GParted.

Again, thanks everyone involved.

---


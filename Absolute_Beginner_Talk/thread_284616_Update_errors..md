---
title: "Update errors."
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by user007 on 2006-10-25
> 
Cannot install all available updates

Some updates require the removal of further software. Use the function "Mark All Upgrades" of the package manager "Synaptic" or run "sudo apt-get dist-upgrade" in a terminal to update your system completely.

the following updates will be skipped:

libfaac0
libmp4v2-0



I try to follow the advice it suggests but it does not seem to work.  Howcan i get rid of this?

---

### Post by taurus on 2006-10-25
From a terminal, Applications -> Accessories -> Terminal, run these two commands and if there is an error, paste it here exactly as it appears on your screen!

```

sudo aptitude update
sudo aptitude dist-upgrade

```

---

### Post by user007 on 2006-10-25
> **taurus said:**
> From a terminal, Applications -> Accessories -> Terminal, run these two commands and if there is an error, paste it here exactly as it appears on your screen!

```

sudo aptitude update
sudo aptitude dist-upgrade

```

Hello. It seemed to work okay but after doing it I still get the same error.

Here is the output:

> 
david@david-desktop:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:5 [http://apt.cerkinfo.be](http://apt.cerkinfo.be) unstable Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release.gpg
Hit [http://apt.cerkinfo.be](http://apt.cerkinfo.be) unstable Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://apt.cerkinfo.be](http://apt.cerkinfo.be) unstable/main Packages
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Hit [http://apt.cerkinfo.be](http://apt.cerkinfo.be) unstable/contrib Packages
Hit [http://apt.cerkinfo.be](http://apt.cerkinfo.be) unstable/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://apt.cerkinfo.be](http://apt.cerkinfo.be) unstable/contrib Sources
Fetched 5B in 1s (4B/s)
Reading package lists... Done
david@david-desktop:~$ sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  libfaac0 libmp4v2-0
2 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 319kB of archives. After unpacking 60.4kB will be used.
The following packages have unmet dependencies:
  libmp4v2-0: Depends: libc6 (>= 2.3.6-6) but 2.3.6-0ubuntu20 is installed.
              Depends: libgcc1 (>= 1:4.1.1-12) but 1:4.0.3-1ubuntu5 is installed.
              Depends: libstdc++6 (>= 4.1.1-12) but 4.0.3-1ubuntu5 is installed.  libfaac0: Depends: libc6 (>= 2.3.6-6) but 2.3.6-0ubuntu20 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
libfaac0 [1.24+20041018-0.2 (now)]

Downgrade the following packages:
libmp4v2-0 [1:1.4.1-1 (now) -> 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3 (dapper)]

Score is -90

Accept this solution? [Y/n/q/?] Y
The following packages will be DOWNGRADED:
  libmp4v2-0
The following packages have been kept back:
  libfaac0
0 packages upgraded, 0 newly installed, 1 downgraded, 0 to remove and 1 not upgraded.
Need to get 214kB of archives. After unpacking 1024B will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse libmp4v2-0 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3 [214kB]
Fetched 214kB in 1s (141kB/s)
dpkg - warning: downgrading libmp4v2-0 from 1:1.4.1-1 to 0:2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3.
(Reading database ... 92133 files and directories currently installed.)
Preparing to replace libmp4v2-0 1:1.4.1-1 (using .../libmp4v2-0_2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3_i386.deb) ...
Unpacking replacement libmp4v2-0 ...
Setting up libmp4v2-0 (2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3) ...



---


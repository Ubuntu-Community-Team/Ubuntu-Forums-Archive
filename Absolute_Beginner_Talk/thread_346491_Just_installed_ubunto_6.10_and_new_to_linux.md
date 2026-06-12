---
title: "Just installed ubunto 6.10 and new to linux"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by uncledave1969 on 2007-01-25
I am tring to install 'wine' and having problems.I have done what it says on websight and I get this......

kebbler2929@Michelle:~$ sudo apt-get update
Password:
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:3 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release.gpg [191B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Sources
Fetched 4B in 1s (2B/s)
Reading package lists... Done
kebbler2929@Michelle:~$ sudo apt-get install wine winesetuptk
Reading package lists... Done
Building dependency tree... Done
Package winesetuptk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  wine
E: Package winesetuptk has no installation candidate
kebbler2929@Michelle:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: libasound2 (> 1.0.11) but 1.0.10-2ubuntu4 is to be installed
        Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20.2 is to be installed
        Depends: libgcc1 (>= 1:4.1.1-12) but 1:4.0.3-1ubuntu5 is to be installed        Depends: libglib2.0-0 (>= 2.12.0) but 2.10.3-0ubuntu1 is to be installed        Depends: libgphoto2-2 (>= 2.2.1) but 2.1.6-5.2ubuntu8 is to be installed        Depends: libgphoto2-port0 (>= 2.2.1) but 2.1.6-5.2ubuntu8 is to be installed
        Depends: libstdc++6 (>= 4.1.1-12) but 4.0.3-1ubuntu5 is to be installed
        Depends: libusb-0.1-4 (>= 2:0.1.12) but 2:0.1.10a-22ubuntu1 is to be installed
        Depends: libxml2 (>= 2.6.26) but 2.6.24.dfsg-1ubuntu1 is to be installed        Depends: libxslt1.1 (>= 1.1.17) but 1.1.15-1ubuntu1 is to be installed
E: Broken packages

Are ther some things I need to install before installing "wine". and I am not linux 'literate'.

Thanx.....uncledave1969

---

### Post by meng on 2007-01-25
It looks like you installed Dapper (6.06) not Edgy (6.10). Change your /etc/apt/sources.list:
sudo nano -B /etc/apt/sources.list
and replace edgy in the final line with dapper. Then save (ctrl-x to exit)

sudo apt-get update
sudo apt-get install wine

---


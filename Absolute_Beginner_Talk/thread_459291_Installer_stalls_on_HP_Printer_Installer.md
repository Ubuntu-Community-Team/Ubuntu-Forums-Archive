---
title: "Installer stalls on HP Printer Installer"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by doyler78 on 2007-05-30
I'm trying to install my printer - hp photosmart c5180 on ubuntu 7.04. When I run the installer it goes until it starts to get and install missing dependencies.

Here's a the install progress or non progress.

```
INSTALLATION MODE
-----------------
Please choose the installation mode (a=automatic*, c=custom, q=quit) : 

INTRODUCTION
------------
This installer will install HPLIP version 1.7.4a on your computer.
Distro is Ubuntu 7.04


DISTRO/OS SELECTION
-------------------

Is "Ubuntu 7.04" your correct distro/OS and version (y=yes*, n=no, q=quit) ? 

ENTER ROOT/SUPERUSER PASSWORD
-----------------------------
Please enter the root/superuser password: 
error: Incorrect password (attempt 1). Please re-enter.
Please enter the root/superuser password: 
note: Password accepted.


INSTALLATION NOTES
------------------
Enable the universe/multiverse repositories. See: https://help.ubuntu.com/community/Repositories/Ubuntu for more information.

Please read the installation notes and hit <enter> to continue (<enter>=continue*, q=quit) : 

INSTALL MISSING REQUIRED DEPENDENCIES
-------------------------------------

warning: There are 4 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: libjpeg (libjpeg - JPEG library)
----------

warning: Missing REQUIRED dependency: cups-devel (cups-devel- Common Unix Printing System development files)
----------

warning: Missing REQUIRED dependency: libusb (libusb - USB library)
----------

warning: Missing REQUIRED dependency: lsb (LSB - Linux Standard Base support)
----------


INSTALL MISSING OPTIONAL DEPENDENCIES
-------------------------------------

note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency for option 'Network/JetDirect I/O': libnetsnmp-devel (libnetsnmp-devel - SNMP networking library development files)
----------

warning: Missing OPTIONAL dependency for option 'PC Send Fax': reportlab (Reportlab - PDF library for Python)
----------

warning: Missing OPTIONAL dependency for option 'Scanning': scanimage (scanimage - Shell scanning program)
----------

Running 'sudo dpkg --configure -a'
Please wait, this may take several minutes...
Running 'sudo apt-get install --yes --force-yes -f '
Please wait, this may take several minutes...
Running 'sudo apt-get update'
Please wait, this may take several minutes...
Running 'xterm -e sudo apt-get install --yes --force-yes postfix'
Please wait, this may take several minutes...
 

DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
Running 'sudo apt-get install --yes --force-yes libjpeg62-dev libcupsys2-dev libusb-dev lsb libsnmp9-dev python-reportlab sane-utils'
Please wait, this may take several minutes...

```Any ideas what could be causing the issues and how should I go about solving them. I have little experience in linux therefore if you can keep it as simple as possible it would be appreciated. Thanks in advance.

---

### Post by daimaru on 2007-05-30
im just saying this since i got a hp printer too and all i had to do was choose system-->administration-->printing
select new printer and mine was already detected. otherwise choose from list .

---

### Post by doyler78 on 2007-05-30
Sorted. Putting it here in case anyone else has this problem. Easy solution is to install the dependencies manually.

sudo apt-get install (whatever dependencies you are missing with a space between each)

Working great now.

---

### Post by doyler78 on 2007-05-30
hi diamaru,

Yeah you can do that and  it will allow you to print no problems however if you have extra functionality with your printer as it is multi-function like mine then installing the hplip will install a range of drivers and software which will allow you access the other functions ie scanning, reading memory cards, faxing if your mfd supports this (mine doesn't).

---

### Post by daimaru on 2007-05-30
> **doyler78 said:**
> hi diamaru,

Yeah you can do that and  it will allow you to print no problems however if you have extra functionality with your printer as it is multi-function like mine then installing the hplip will install a range of drivers and software which will allow you access the other functions ie scanning, reading memory cards, faxing if your mfd supports this (mine doesn't).

nice to hear you got it running. guess i never ran into those probs cause my printer is soooooo old :)

---


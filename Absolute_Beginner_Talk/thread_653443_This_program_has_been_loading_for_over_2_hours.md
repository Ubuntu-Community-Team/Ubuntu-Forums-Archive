---
title: "This program has been loading for over 2 hours"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by trugreg on 2007-12-29
Gutsy on Plll 900 - 512 mem - I am sure something is not right. I love Ubuntu and want everything working so I NEVER boot XP again

HP Linux Imaging and Printing System (ver. 2.7.12)
HPLIP Installer ver. 3.0

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Installer log saved in: hplip-install_Sat-29-Dec-2007_16:33:58.log

|
note: Defaults for each question are maked with a '*'. Press <enter> to accept the default.


INSTALLATION MODE
-----------------
Automatic mode will install the full HPLIP solution with the most common options.
Custom mode allows you to chose installation options to fit specific requirements.

Please choose the installation mode (a=automatic*, c=custom, w=web installer, q=quit) : a

Initializing. Please wait...
 

INTRODUCTION
------------
This installer will install HPLIP version 2.7.12 on your computer.
Please close any running package management systems now (YaST, Adept, Synaptic, Up2date, etc).


DISTRO/OS CONFIRMATION
----------------------
Distro appears to be Ubuntu 7.10.

Is "Ubuntu 7.10" your correct distro/OS and version (y=yes*, n=no, q=quit) ? y


ENTER ROOT/SUPERUSER PASSWORD
-----------------------------
Please enter the root/superuser password: 
Password accepted


INSTALLATION NOTES
------------------
Enable the universe/multiverse repositories. See: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) for more information.  Disable the CD-ROM/DVD source if you do not have the Ubunbtu installation media inserted in the drive.

Please read the installation notes. Press <enter> to continue or 'q' to quit: 


RUNNING PRE-INSTALL COMMANDS
----------------------------


INSTALL MISSING REQUIRED DEPENDENCIES
-------------------------------------
warning: There are 7 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: gcc (gcc - GNU Project C and C++ Compiler)
warning: Missing REQUIRED dependency: libpthread (libpthread - POSIX threads library)
warning: Missing REQUIRED dependency: python-devel (python-devel - Python development files)
warning: Missing REQUIRED dependency: cups-devel (cups-devel- Common Unix Printing System development files)
warning: Missing REQUIRED dependency: libusb (libusb - USB library)
warning: Missing REQUIRED dependency: libtool (libtool - Library building support services)
warning: Missing REQUIRED dependency: libjpeg (libjpeg - JPEG library)


INSTALL MISSING OPTIONAL DEPENDENCIES
-------------------------------------
warning: There are 6 missing OPTIONAL dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency for option 'network': libcrypto (libcrypto - OpenSSL cryptographic library)
warning: Missing REQUIRED dependency for option 'network': libnetsnmp-devel (libnetsnmp-devel - SNMP networking library development files)
warning: Missing OPTIONAL dependency for option 'fax': reportlab (Reportlab - PDF library for Python)
warning: Missing REQUIRED dependency for option 'scan': sane-devel (SANE - Scanning library development files)
warning: Missing OPTIONAL dependency for option 'scan': pil (PIL - Python Imaging Library (required for commandline scanning with hp-scan))
warning: Missing OPTIONAL dependency for option 'scan': scanimage (scanimage - Shell scanning program)


CHECKING FOR NETWORK CONNECTION
-------------------------------
Network connection present.


RUNNING PRE-PACKAGE COMMANDS
----------------------------
sudo dpkg --configure -a (Pre-depend step 1)
sudo apt-get install --yes --force-yes -f (Pre-depend step 2)
sudo apt-get update (Pre-depend step 3)


DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
Running 'sudo apt-get install --yes --force-yes build-essential build-essential python2.5-dev libcupsys2-dev cupsys-bsd libusb-dev libtool libjpeg62-dev openssl libsnmp9-dev python-reportlab libsane-dev python-imaging libsane'
Please wait, this may take several minutes...

---

### Post by Sef on 2007-12-29
Did you try to plug in your HP and see if just worked OOTB (Out of the Box)?   I have an HP PSC 1610 and that's all I did to get it to work.

---

### Post by trugreg on 2007-12-29
it prints but no scan or fax. But anyway how can I stop this to try something else.

---

### Post by trugreg on 2007-12-30
it is still running - how can I stop this

---

### Post by SOULRiDER on 2007-12-30
Check the name of the process and kill it. Go to Applications > system tools > System Monitor and click ont he process tab, then find it and kill it.

---

### Post by taurus on 2007-12-30
Is it from a terminal?  Press <Ctrl>z to stop it and then "kill %" to kill it.

---

### Post by Sef on 2007-12-30
> it prints but no scan or fax.

If it only prints, then plug it in and see if it works.

---

### Post by The_Dud on 2007-12-30
Did you try installing the missing dependencys yourself? If that's in terminal hit Ctrl + C to cancle and use "sudo apt-get install" to install the packages that it needs/wants. (gcc, libpthread, python-devel, cups-devel, libusb, libusb, libtool, libjpeg, libcrypto,
 ibnetsnmp-devel, reportlab,: sane-devel, pil, scanimage) Sorry I can't test to make sure that all of these are in the repositories (I'm on 64 bit Ubuntu, so some may be 32 bit specific) but go ahead and give it a try.

---

### Post by bwtranch on 2007-12-30
I'm still trying to understand this one. Heard a lot of strange things tonite though. Can you boot Linux from a live CD?

---

### Post by eternicode on 2007-12-30
> **bwtranch said:**
> I'm still trying to understand this one. Heard a lot of strange things tonite though. Can you boot Linux from a live CD?

:???: eh?

He basically had a runaway process....

---

### Post by Sef on 2007-12-30
> I'm still trying to understand this one. Heard a lot of strange things tonite though. Can you boot Linux from a live CD?

Yes, from the Ubuntu Live CD, you can either use it as a Live CD or install.

---

### Post by yaknowwat on 2007-12-30
From what I can tell the installer attempted to put this command in .

sudo apt-get install --yes --force-yes build-essential build-essential python2.5-dev libcupsys2-dev cupsys-bsd libusb-dev libtool libjpeg62-dev openssl libsnmp9-dev python-reportlab libsane-dev python-imaging libsane

I'm not very familiar with the linux command line but could it be that it declared build-essential twice.?
Also it attempting to force this.


I'd suggest Checking for Updates With the Update Manager then open the Synaptic Package manager and search up the missing dependencies

looking up :
python
cupsys
lib
openssl

finding all the files and mark for installation or re-installation

I checked and all of them exist in synaptic package manger Ubuntu 7.10 32-Bit

---

### Post by SOULRiDER on 2007-12-30
Most of those packages area already installed but you can still reinstall them. Try this
```
sudo aptitude install build-essential build-essential python2.5-dev libcupsys2-dev cupsys-bsd libusb-dev libtool libjpeg62-dev openssl libsnmp9-dev python-reportlab libsane-dev python-imaging libsane
```

---

### Post by Linux Lurker on 2007-12-31
???Solved???
Just installed 7.10.  New to linux.  This is my first post on these boards.

Ok... I was experiencing the same problem trying to update to hplip 2.7.12.  It hung up at exactly the same point.  I searched the boards for a solution.  Seems others have the same problem.

So, I decided to try installing all the necessary dependancy files via the adept manager.
As I was doing it (one file at a time), it asked for my installation DVD.  Hmmmmm.

Long story short.  I guessed this *may* be the reason the installer was hanging up at that point.  To test this theory, I ran it again with my kubuntu DVD in the drive.
Woo hoo!
hplip 2.7.12 installed without a hitch and I'm now happily printing.
I hope this helps someone else stop banging their head.

---


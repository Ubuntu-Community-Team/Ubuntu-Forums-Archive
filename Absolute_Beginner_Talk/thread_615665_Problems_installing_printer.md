---
title: "Problems installing printer"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by pajim17020 on 2007-11-17
Hi I just install Ubuntu. It is running great but I am having problems getting my HP photosmart 3200 working. It is hooked up to my router. It worked fine with XP PRO. I down loaded HPLIP 2.7.10 but it won't install. I follow the instructions but I keep getting errors. 


NSTALL MISSING OPTIONAL DEPENDENCIES
-------------------------------------
warning: There are 7 missing OPTIONAL dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency for option 'network': libcrypto (libcrypto - OpenSSL cryptographic library)
warning: Missing REQUIRED dependency for option 'network': libnetsnmp-devel (libnetsnmp-devel - SNMP networking library development files)
warning: Missing REQUIRED dependency for option 'gui': pyqt (PyQt - Qt interface for Python)
warning: Missing OPTIONAL dependency for option 'fax': reportlab (Reportlab - PDF library for Python)
warning: Missing REQUIRED dependency for option 'scan': sane-devel (SANE - Scanning library development files)
warning: Missing OPTIONAL dependency for option 'scan': pil (PIL - Python Imaging Library (required for commandline scanning with hp-scan))
warning: Missing OPTIONAL dependency for option 'scan': scanimage (scanimage - Shell scanning program)
A package manager 'apt-get' appears to be running. Please quit the package manager and press enter to continue (i=ignore, q=quit*) :
A package manager 'apt-get' appears to be running. Please quit the package manager and press enter to continue (i=ignore, q=quit*) :
A package manager 'apt-get' appears to be running. Please quit the package manager and press enter to continue (i=ignore, q=quit*) :
A package manager 'apt-get' appears to be running. Please quit the package manager and press enter to continue (i=ignore, q=quit*) :
A package manager 'apt-get' appears to be running. Please quit the package manager and press enter to continue (i=ignore, q=quit*) :
A package manager 'apt-get' appears to be running. Please quit the package manager and press enter to continue (i=ignore, q=quit*) :
A package manager 'apt-get' appears to be running. Please quit the package manager and press enter to continue (i=ignore, q=quit*) :
A package manager 'apt-get' appears to be running. Please quit the package manager and press enter to continue (i=ignore, q=quit*) :
A package manager 'apt-get' appears to be running. Please quit the package manager and press enter to continue (i=ignore, q=quit*) :
A package manager 'apt-get' appears to be running. Please quit the package manager and press enter to continue (i=ignore, q=quit*) :
A package manager 'apt-get' appears to be running. Please quit the package manager and press enter to continue (i=ignore, q=quit*) :
A package manager 'apt-get' appears to be running. Please quit the package manager and press enter to continue (i=ignore, q=quit*) :
A package manager 'apt-get' appears to be running. Please quit the package manager and press enter to continue (i=ignore, q=quit*) :
A package manager 'apt-get' appears to be running. Please quit the package manager and press enter to continue (i=ignore, q=quit*) :q
A package manager 'apt-get' appears to be running. Please quit the package manager and press enter to continue (i=ignore, q=quit*) :i
warning: Ignoring running package manager. Some package operations may fail.


CHECKING FOR NETWORK CONNECTION
-------------------------------
Network connection present.


RUNNING PRE-PACKAGE COMMANDS
----------------------------
warning: An error occurred running 'sudo dpkg --configure -a'
sudo dpkg --configure -a (Pre-depend step 1)
warning: An error occurred running 'sudo apt-get install --yes --force-yes -f'
sudo apt-get install --yes --force-yes -f (Pre-depend step 2)
warning: An error occurred running 'sudo apt-get update'
sudo apt-get update (Pre-depend step 3)


DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
Running 'sudo apt-get install --yes --force-yes build-essential build-essential python2.5-dev libcupsys2-dev cupsys-bsd libusb-dev libtool libjpeg62-dev openssl libsnmp9-dev python-qt3 python-reportlab libsane-dev python-imaging libsane'
Please wait, this may take several minutes...
error: Package install command failed with error code 100
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ? y
Running 'sudo apt-get install --yes --force-yes build-essential build-essential python2.5-dev libcupsys2-dev cupsys-bsd libusb-dev libtool libjpeg62-dev openssl libsnmp9-dev python-qt3 python-reportlab libsane-dev python-imaging libsane'
Please wait, this may take several minutes...
error: Package install command failed with error code 100
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ? n
warning: Some HPLIP functionality might not function due to missing package(s).
error: A required dependency 'gcc (gcc - GNU Project C and C++ Compiler)' is still missing.
error: A required dependency 'libpthread (libpthread - POSIX threads library)' is still missing.
error: A required dependency 'python-devel (python-devel - Python development files)' is still missing.
error: A required dependency 'cups-devel (cups-devel- Common Unix Printing System development files)' is still missing.
error: A required dependency 'libusb (libusb - USB library)' is still missing.
error: A required dependency 'libtool (libtool - Library building support services)' is still missing.
error: A required dependency 'libjpeg (libjpeg - JPEG library)' is still missing.
error: Installation cannot continue without these dependencies.
error: Please manually install this dependency and re-run this installer.
jim@mycomputer:~$ sudo aptitude purge sh hplip-2.7.10
[sudo] password for jim:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
jim@mycomputer:~$ 


If anyone has any advice it would be a great help. I never used anything but windows but I like ubuntu. I hate to go back to windows.:(

---

### Post by Arwen on 2007-11-17
Have you tried [this ]("http://hplip.sourceforge.net/install/manual/distros/ubuntu.html")guide?Make sure that when you do sudo apt-get etc,you don't run synaptic at the same time.(E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?)

---

### Post by pajim17020 on 2007-11-17
Yes I did try that guide. I keep getting.
jim@mycomputer:~$ sudo apt-get upgrade
[sudo] password for jim:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
jim@mycomputer:~$ 

I have no idea how to if any other process is using it or how to stop it if it is. I tried rebooting and closing everything down but it didn't help.

---

### Post by Arwen on 2007-11-17
You can find it by typing "ps aux" or "pstree" in terminal to find out and kill the process(close the application that uses package manager)

---

### Post by pajim17020 on 2007-11-17
Thank You for your help. I managed to get it working. The problem turned out to be my cd-rom drive failed. I put the ubuntu cd in my other drive and everything installed fine.:guitar:

---


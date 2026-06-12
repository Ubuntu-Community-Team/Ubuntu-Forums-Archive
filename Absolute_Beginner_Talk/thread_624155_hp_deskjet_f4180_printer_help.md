---
title: "hp deskjet f4180 printer help"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by kahram.yoon on 2007-11-26
I cannot get this printer to start printing anything.  I have installed it with the hplip driver and it still does not work when i try to print something.  It says, "error while printing."  When I click print test page, nothing happens, it says it is going to job whatever number but never prints.  I open manage print jobs but there are no jobs there.  need help with this printer please.  Any ways to fix this problem and to get this printer to work? thank you.

---

### Post by 11hjpphty76lkjj on 2007-11-26
Can you please run:

```
hp-check -t 
```

and post the output?

---

### Post by kahram.yoon on 2007-11-26
this is what came out....
-----------
| SUMMARY |
-----------

error: 1 error or warning.

Summary of needed commands to run to satisfy missing dependencies:
sudo apt-get install --yes --force-yes libsane

Please refer to the installation instructions at:
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)

i ran the needed command and got this....
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libsane is already the newest version.
The following packages were automatically installed and are no longer required:
  libgnucrypto-java libcairo-jni libgtk-jni libcairo-java libglib-jni
  libbcprov-java libglib-java libgtk-java
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

i still have an error when trying to print....

---

### Post by Sef on 2007-11-26
What version of Ubuntu do you have?

---

### Post by kahram.yoon on 2007-11-26
Ubuntu 7.10 i believe

---

### Post by kahram.yoon on 2007-11-27
help please?

---

### Post by kahram.yoon on 2007-11-27
oh something useful
the printer state in printer configuration says processing
is it supposed to say that?

---

### Post by 11hjpphty76lkjj on 2007-11-27
If you can please post the entire hp-check -t log.

Also got to the cups interface:

[http://localhost:631/printers](http://localhost:631/printers)

and make sure your printer is 'started'.  If that doesn't work try deleting it (run hp-toolbox, click the printer, then delete or you can delete it from the cups interface) and run hp-setup to configure the printer.

Hope this helps.

A

---

### Post by gapthemind on 2008-01-12
Hi, I'm having the same problem: I removed and reinstalled the printer, told it to print a test page, and nothing happens.

Below is the output of hp-check -t. I see it's telling me some optional packages aren't installed, but when I run the provided commands, they tell me the packages are updated to the latest version already. (what can I do about that?)

Thanks,
Rob




% more hp-check.log 
hp-check[22293]: info: :
Initializing. Please wait...
Distributor ID:	Ubuntu

Release:	6.06

scheduler is running

1.2.2

Linux excursus 2.6.15-29-386 #1 PREEMPT Wed Aug 29 13:20:33 UTC 2007 i686 GNU/Linux

hp-check[22293]: info: :
hp-check[22293]: info: :---------------
hp-check[22293]: info: :| SYSTEM INFO |
hp-check[22293]: info: :---------------
hp-check[22293]: info: :
hp-check[22293]: info: :Basic system information:
hp-check[22293]: info: :Linux excursus 2.6.15-29-386 #1 PREEMPT Wed Aug 29 13:20:33 UTC 2007 i686 GNU/Linux
hp-check[22293]: info: :
hp-check[22293]: info: :Distribution:
hp-check[22293]: info: :ubuntu 6.06
hp-check[22293]: info: :
HPOJ running?
hp-check[22293]: info: :No, HPOJ is not running (OK).
hp-check[22293]: info: :
hp-check[22293]: info: :Checking Python version...
hp-check[22293]: info: :OK, version 2.4.3 installed
hp-check[22293]: info: :
hp-check[22293]: info: :Checking PyQt version...
hp-check[22293]: info: :OK, version 3.15 installed.
hp-check[22293]: info: :
hp-check[22293]: info: :Checking SIP version...
hp-check[22293]: info: :OK, Version 4.3.2 installed
hp-check[22293]: info: :
hp-check[22293]: info: :Checking for CUPS...
hp-check[22293]: info: :Status: scheduler is running
hp-check[22293]: info: :Version: 1.2.2
hp-check[22293]: info: :
hp-check[22293]: info: :Checking for Reportlab...
warning: Version < 2.0 (1.2). HPLIP fax coverpages requires Reportlab 2.0+.
hp-check[22293]: info: :
hp-check[22293]: info: :----------------
hp-check[22293]: info: :| DEPENDENCIES |
hp-check[22293]: info: :----------------
hp-check[22293]: info: :
hp-check[22293]: info: :
hp-check[22293]: info: :Checking for dependency: cups - Common Unix Printing System...
hp-check[22293]: info: :OK, found.
hp-check[22293]: info: :
hp-check[22293]: info: :Checking for dependency: cups-devel- Common Unix Printing System development files...
hp-check[22293]: info: :OK, found.
hp-check[22293]: info: :
hp-check[22293]: info: :Checking for dependency: gcc - GNU Project C and C++ Compiler...
hp-check[22293]: info: :OK, found.
hp-check[22293]: info: :
hp-check[22293]: info: :Checking for dependency: GhostScript - PostScript and PDF language interpreter and previewer...
hp-check[22293]: info: :OK, found.
hp-check[22293]: info: :
hp-check[22293]: info: :Checking for dependency: libcrypto - OpenSSL cryptographic library...
hp-check[22293]: info: :OK, found.
hp-check[22293]: info: :
hp-check[22293]: info: :Checking for dependency: libjpeg - JPEG library...
hp-check[22293]: info: :OK, found.
hp-check[22293]: info: :
hp-check[22293]: info: :Checking for dependency: libnetsnmp-devel - SNMP networking library development files...
hp-check[22293]: info: :OK, found.
hp-check[22293]: info: :
hp-check[22293]: info: :Checking for dependency: libpthread - POSIX threads library...
hp-check[22293]: info: :OK, found.
hp-check[22293]: info: :
hp-check[22293]: info: :Checking for dependency: libtool - Library building support services...
hp-check[22293]: info: :OK, found.
hp-check[22293]: info: :
hp-check[22293]: info: :Checking for dependency: libusb - USB library...
hp-check[22293]: info: :OK, found.
hp-check[22293]: info: :
hp-check[22293]: info: :Checking for dependency: make - GNU make utility to maintain groups of programs...
hp-check[22293]: info: :OK, found.
hp-check[22293]: info: :
hp-check[22293]: info: :Checking for dependency: PIL - Python Imaging Library (required for commandline scanning with hp-scan)...
hp-check[22293]: info: :OK, found.
hp-check[22293]: info: :
hp-check[22293]: info: :Checking for dependency: ppdev - Parallel port support kernel module....
hp-check[22293]: info: :OK, found.
hp-check[22293]: info: :
hp-check[22293]: info: :Checking for dependency: PyQt - Qt interface for Python...
hp-check[22293]: info: :OK, found.
hp-check[22293]: info: :
hp-check[22293]: info: :Checking for dependency: python-devel - Python development files...
hp-check[22293]: info: :OK, found.
hp-check[22293]: info: :
hp-check[22293]: info: :Checking for dependency: Python 2.3 or greater - Required for fax functionality...
hp-check[22293]: info: :OK, found.
hp-check[22293]: info: :
hp-check[22293]: info: :Checking for dependency: Python 2.2 or greater - Python programming language...
hp-check[22293]: info: :OK, found.
hp-check[22293]: info: :
hp-check[22293]: info: :Checking for dependency: Reportlab - PDF library for Python...
warning: NOT FOUND! This is an OPTIONAL dependency. Some HPLIP functionality may not function properly.
hp-check[22293]: info: :To install this dependency, execute this command:
hp-check[22293]: info: :sudo apt-get install --yes --force-yes python-reportlab
hp-check[22293]: info: :
hp-check[22293]: info: :Checking for dependency: SANE - Scanning library...
hp-check[22293]: info: :OK, found.
hp-check[22293]: info: :
hp-check[22293]: info: :Checking for dependency: SANE - Scanning library development files...
hp-check[22293]: info: :OK, found.
hp-check[22293]: info: :
hp-check[22293]: info: :Checking for dependency: scanimage - Shell scanning program...
warning: NOT FOUND! This is an OPTIONAL dependency. Some HPLIP functionality may not function properly.
hp-check[22293]: info: :To install this dependency, execute this command:
hp-check[22293]: info: :sudo apt-get install --yes --force-yes libsane
hp-check[22293]: info: :
hp-check[22293]: info: :Checking for dependency: xsane - Graphical scanner frontend for SANE...
hp-check[22293]: info: :OK, found.
hp-check[22293]: info: :
hp-check[22293]: info: :
hp-check[22293]: info: :----------------------
hp-check[22293]: info: :| HPLIP INSTALLATION |
hp-check[22293]: info: :----------------------
hp-check[22293]: info: :
hp-check[22293]: info: :
hp-check[22293]: info: :Currently installed HPLIP version...
hp-check[22293]: info: :HPLIP 2.7.12 currently installed in '/usr/share/hplip'.
hp-check[22293]: info: :
hp-check[22293]: info: :Current contents of '/etc/hp/hplip.conf' file:
hp-check[22293]: info: :# hplip.conf.  Generated from hplip.conf.in by configure.

[hpssd]
# Note: hpssd does not support dynamic ports
# Port 2207 is the IANA assigned port for hpssd
port=2207

[hplip]
version=2.7.12

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-2.7.12
icon=/usr/share/applications
cupsbackend=/usr/lib/cups/backend
foomatic=/usr/share/foomatic

# Following values are determined at configure time and cannot be changed.
[configure]
network-build=yes
pp-build=no
gui-build=yes
scanner-build=yes
fax-build=yes
cups11-build=no
doc-build=yes
shadow-build=no
foomatic-xml-install=no
foomatic-ppd-install=yes
internal-tag=2.7.12.10

hp-check[22293]: info: :
hp-check[22293]: info: :--------------------------
hp-check[22293]: info: :| DISCOVERED USB DEVICES |
hp-check[22293]: info: :--------------------------
hp-check[22293]: info: :
hp-check[22293]: info: :
hp-check[22293]: info: :---------------------------------
hp-check[22293]: info: :| INSTALLED CUPS PRINTER QUEUES |
hp-check[22293]: info: :---------------------------------
hp-check[22293]: info: :
hp-check[22293]: info: :
hp-check[22293]: info: :Deskjet_F4100
hp-check[22293]: info: :-------------
hp-check[22293]: info: :Type: Printer
hp-check[22293]: info: :Installed in HPLIP?: Yes, using the hp: CUPS backend.
hp-check[22293]: info: :Device URI: hp:/usb/Deskjet_F4100_series?serial=CN79T4T18K04TJ
hp-check[22293]: info: :PPD: /etc/cups/ppd/Deskjet_F4100.ppd
hp-check[22293]: info: :PPD Description: HP LaserJet 4100 Series v.3010.107 Postscript (recommended)
hp-check[22293]: info: :Printer status: printer Deskjet_F4100 is idle.  enabled since Fri 11 Jan 2008 10:10:21 PM PST
hp-check[22293]: info: :Communication status: Good
hp-check[22293]: info: :
hp-check[22293]: info: :
hp-check[22293]: info: :----------------------
hp-check[22293]: info: :| SANE CONFIGURATION |
hp-check[22293]: info: :----------------------
hp-check[22293]: info: :
hp-check[22293]: info: :'hpaio' in '/etc/sane.d/dll.conf'...
hp-check[22293]: info: :OK, found. SANE backend 'hpaio' is properly set up.
hp-check[22293]: info: :
hp-check[22293]: info: :Checking output of 'scanimage -L'...
error: scanimage not found.
hp-check[22293]: info: :
hp-check[22293]: info: :---------------------
hp-check[22293]: info: :| PYTHON EXTENSIONS |
hp-check[22293]: info: :---------------------
hp-check[22293]: info: :
hp-check[22293]: info: :Checking 'cupsext' CUPS extension...
hp-check[22293]: info: :OK, found.
hp-check[22293]: info: :
hp-check[22293]: info: :Checking 'pcardext' Photocard extension...
hp-check[22293]: info: :OK, found.
hp-check[22293]: info: :
hp-check[22293]: info: :Checking 'hpmudext' I/O extension...
hp-check[22293]: info: :OK, found.
hp-check[22293]: info: :
hp-check[22293]: info: :Checking 'scanext' SANE scanning extension...
hp-check[22293]: info: :OK, found.
hp-check[22293]: info: :
hp-check[22293]: info: :
hp-check[22293]: info: :-----------------
hp-check[22293]: info: :| USB I/O SETUP |
hp-check[22293]: info: :-----------------
hp-check[22293]: info: :
hp-check[22293]: info: :
hp-check[22293]: info: :Checking for permissions of USB attached printers...
hp-check[22293]: info: :
HP Device 0x7e04 at 001:006: 
hp-check[22293]: info: :    Device URI: hp:/usb/Deskjet_F4100_series?serial=CN79T4T18K04TJ
hp-check[22293]: info: :    Device node: /dev/bus/usb/001/006
hp-check[22293]: info: :    Mode: 0666
hp-check[22293]: info: :
hp-check[22293]: info: :-----------
hp-check[22293]: info: :| SUMMARY |
hp-check[22293]: info: :-----------
hp-check[22293]: info: :
error: 3 errors and/or warnings.
hp-check[22293]: info: :
hp-check[22293]: info: :Summary of needed commands to run to satisfy missing dependencies:
hp-check[22293]: info: :sudo apt-get install --yes --force-yes python-reportlab
hp-check[22293]: info: :sudo apt-get install --yes --force-yes libsane
hp-check[22293]: info: :
hp-check[22293]: info: :Please refer to the installation instructions at:
hp-check[22293]: info: :[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)

---

### Post by 11hjpphty76lkjj on 2008-01-12
If you run:

sudo aa-complain cupsd

does it fix it?

A

---

### Post by gapthemind on 2008-01-12
Hmm.

aa-complain: command not found

I'm on ubuntu..

Rob

---

### Post by plasmidmap on 2008-01-12
Same printer, same problem: I can confirm that kalosaurusrex's command does fix it.

Thanks a lot!

---

### Post by 11hjpphty76lkjj on 2008-01-13
> **gapthemind said:**
> Hmm.

aa-complain: command not found

I'm on ubuntu..

Rob

Rob,

Yes I know you are running ubuntu... perhaps apparmor isn't in the older version of ubuntu (6.06).  Is it possible for you to upgrade ubuntu perhaps?  I don't have a system running 6.06 and I can work on getting one going to test but honestly it's probably not going to be for a bit.

The aa-complain cups should fix it for at least gusty.  and from other reports does.

Sorry I couldn't help more..

A

---

### Post by sharu on 2008-07-24
Is that printer is under warranty, if yes  visit to service center, if no. you have to change other printer.
*********
sharu
  	  [url="http://www.concordsupplies.com/hp-color-laserjet-2600-black-toner-cartridge-hp-q6000a/41424.html"]
HP q6000a[/url]

---


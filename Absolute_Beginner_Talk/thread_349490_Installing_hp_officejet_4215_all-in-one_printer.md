---
title: "Installing hp officejet 4215 all-in-one printer"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by britbikest on 2007-01-30
I'm trying to install a hp officejet 4215 all-in-one printer to use with Ubuntu.  I downloaded the drivers HP recommended from a non-HP site, but it still doesn't work.  

Any suggestions?

I'm a newbie so a simple explanation would be appreciated](*,) ](*,) . 

Thanks.

---

### Post by NewOldTimer on 2007-01-30
newbie here also but try---System>administration>synaptic package manager>reload>search for - hpoj - see if needed>apply.  Hope thats right for you

---

### Post by 11hjpphty76lkjj on 2007-01-30
Please do **NOT** use HPOJ. It's very old and outdated. (and not supported!!)

Use HPLIP.

[http://hplip.sf.net](http://hplip.sf.net)

There is a walk through, and auto installer.  If you have any problems/questions I'd love to help.

A

---

### Post by NewOldTimer on 2007-01-30
thanks - nice to know

---

### Post by LikeAbird on 2007-07-02
Hi.

I have an HP Officejet 4215xi all-in-one printer/scanner/copier/fax.
I recently installed the Ubuntu 7.04 on my laptop and connected the printer. I don't remember how I did but once I could print just after I added a new printer. There was no exactly same model in the list, so I chose hp officejet 4200 and it worked: only printing, no scanning. So I started trying install scanner and ended up this website hplip.sf.net and downloaded installer and started installation. Before I start installation, I removed the printer from the System-Administration-Printing list.

It seemed processed smoothly until the installer asked me to log off and run "sudo hp-setup". It opened a window and asked about connection. I checked on the USB and clicked Next. And then it gave me an error "No device found". Of course I connected and turned on the printer. Now it prints but doesn't scan.

Below is the "hp-check" result. There is "warning: No queues found" in the "Installed Printers" section, but funny enough, the "Summary" says "No errors or warnings."

Please help me to correct problem.

Thank you.

HP Linux Imaging and Printing System (ver. 2.7.6)
Dependency/Version Check Utility ver. 8.0

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Initializing. Please wait...
Saving output in log file: hp-check.log

---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux jinseok-laptop 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

Distribution:
ubuntu 7.04

HPOJ running?
No, HPOJ is not running (OK).

Checking Python version...
OK, version 2.5.1 installed

Checking PyQt version...
OK, version 3.17 installed.

Checking SIP version...
OK, Version 4.5 installed

Checking for CUPS...
Status: scheduler is running
Version: 1.2.8

----------------
| DEPENDENCIES |
----------------

 
Checking for dependency cups - Common Unix Printing System...
OK, found.

Checking for dependency cups-devel- Common Unix Printing System development files...
OK, found.

Checking for dependency gcc - GNU Project C and C++ Compiler...
OK, found.

Checking for dependency GhostScript - PostScript and PDF language interpreter and previewer...
OK, found.

Checking for dependency libcrypto - OpenSSL cryptographic library...
OK, found.

Checking for dependency libjpeg - JPEG library...
OK, found.

Checking for dependency libnetsnmp-devel - SNMP networking library development files...
OK, found.

Checking for dependency libpthread - POSIX threads library...
OK, found.

Checking for dependency libusb - USB library...
OK, found.

Checking for dependency make - GNU make utility to maintain groups of programs...
OK, found.

Checking for dependency ppdev - Parallel port support kernel module....
OK, found.

Checking for dependency PyQt - Qt interface for Python...
OK, found.

Checking for dependency python-devel - Python development files...
OK, found.

Checking for dependency Python 2.3 or greater - Required for fax functionality...
OK, found.

Checking for dependency Python 2.2 or greater - Python programming language...
OK, found.

Checking for dependency Reportlab - PDF library for Python...
OK, found.

Checking for dependency sane - Scanning library...
OK, found.

Checking for dependency sane-devel - Scanning library development files...
OK, found.

Checking for dependency scanimage - Shell scanning program...
OK, found.

Checking for dependency xsane - Graphical scanner frontend for SANE...
OK, found.


----------------------
| HPLIP INSTALLATION |
----------------------


Currently installed HPLIP version...
HPLIP 2.7.6 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hpssd]
# Note: hpssd does not support dynamic ports
# Port 2207 is the IANA assigned port for hpssd
port=2207

[hplip]
version=2.7.6

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-2.7.6
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
foomatic-xml-install=yes
foomatic-ppd-install=no
internal-tag=2.7.6.13


----------------------
| INSTALLED PRINTERS |
----------------------

 
warning: No queues found.

----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
 
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).


---------------------
| PYTHON EXTENSIONS |
---------------------

Checking 'cupsext' CUPS extension...
OK, found.

Checking 'pcardext' Photocard extension...
OK, found.

Checking 'hpmudext' I/O extension...
OK, found.

Checking 'scanext' SANE scanning extension...
OK, found.


-----------------
| USB I/O SETUP |
-----------------

Checking proper HPLIP I/O setup (USB I/O only)...
udev "usb_device" access mode: 0664 (OK)

Checking for permissions of USB attached printers...
HP Device 0x3d11 at 001:011:
warning:     Device URI: (Makeuri FAILED)
    Device node: /dev/bus/usb/001/011
    Mode: 0664
    UID: 0 (root)
    GID: 7 (lp)
    Device group and mode appear correct.

Is user 'member1' a member of the 'lp' group?
Yes (OK)

Is user 'member2' a member of the 'lp' group?
Yes (OK)

Is user 'member3' a member of the 'lp' group?
Yes (OK)

Is user 'member4' a member of the 'lp' group?
Yes (OK)


-----------
| SUMMARY |
-----------

No errors or warnings.

---

### Post by 11hjpphty76lkjj on 2007-07-02
Everything looks good.  Although it appears no printer is configured.  Run; 

```
sudo hp-setup
```

and try printing/scanning again.

---

### Post by LikeAbird on 2007-07-02
Thank you for your quick reply, kalosaurusrex. But it didn't work yet.
When I ran "sudo hp-setup", following message was appeared in the terminal and opened the "HP Device Manager". I chose USB connection and clicked Next. It gave me an error "No Device Found". I can print, but no scan. What else can I do now?

Thank you for your help.



HP Linux Imaging and Printing System (ver. 2.7.6)
Printer/Fax Setup Utility ver. 4.5

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

HP Linux Imaging and Printing System (ver. 2.7.6)
Services and Status Daemon ver. 9.2

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: No devices found.Please make sure your printer is properly connected and powered-on.
Done.

---

### Post by 11hjpphty76lkjj on 2007-07-02
Please run hp-check and post the output.

---

### Post by LikeAbird on 2007-07-02
Here is the hp-check result. By the way, thank you so much for your quick responses.
In the result, you will notice there is HP Officejet 4200 is installed. This is because I found the System-Administration-Printing can detect the printer automatically and I installed 4200, which is the closest one with my 4215xi, after I failed install the printer and the scanner using hp-setup. This way, I could print. So I tried this also. That is, unistall this 4200 and run hp-setup again... didn't work. So I installed the printer (4200) again with the system-admin-printing to use it for now. 

hp-check result:

HP Linux Imaging and Printing System (ver. 2.7.6)
Dependency/Version Check Utility ver. 8.0

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Initializing. Please wait...
Saving output in log file: hp-check.log

---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux jinseok-laptop 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

Distribution:
ubuntu 7.04

HPOJ running?
No, HPOJ is not running (OK).

Checking Python version...
OK, version 2.5.1 installed

Checking PyQt version...
OK, version 3.17 installed.

Checking SIP version...
OK, Version 4.5 installed

Checking for CUPS...
Status: scheduler is running
Version: 1.2.8

----------------
| DEPENDENCIES |
----------------

 
Checking for dependency cups - Common Unix Printing System...
OK, found.

Checking for dependency cups-devel- Common Unix Printing System development files...
OK, found.

Checking for dependency gcc - GNU Project C and C++ Compiler...
OK, found.

Checking for dependency GhostScript - PostScript and PDF language interpreter and previewer...
OK, found.

Checking for dependency libcrypto - OpenSSL cryptographic library...
OK, found.

Checking for dependency libjpeg - JPEG library...
OK, found.

Checking for dependency libnetsnmp-devel - SNMP networking library development files...
OK, found.

Checking for dependency libpthread - POSIX threads library...
OK, found.

Checking for dependency libusb - USB library...
OK, found.

Checking for dependency make - GNU make utility to maintain groups of programs...
OK, found.

Checking for dependency ppdev - Parallel port support kernel module....
OK, found.

Checking for dependency PyQt - Qt interface for Python...
OK, found.

Checking for dependency python-devel - Python development files...
OK, found.

Checking for dependency Python 2.3 or greater - Required for fax functionality...
OK, found.

Checking for dependency Python 2.2 or greater - Python programming language...
OK, found.

Checking for dependency Reportlab - PDF library for Python...
OK, found.

Checking for dependency sane - Scanning library...
OK, found.

Checking for dependency sane-devel - Scanning library development files...
OK, found.

Checking for dependency scanimage - Shell scanning program...
OK, found.

Checking for dependency xsane - Graphical scanner frontend for SANE...
OK, found.


----------------------
| HPLIP INSTALLATION |
----------------------


Currently installed HPLIP version...
HPLIP 2.7.6 currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf.  Generated from hplip.conf.in by configure.

[hpssd]
# Note: hpssd does not support dynamic ports
# Port 2207 is the IANA assigned port for hpssd
port=2207

[hplip]
version=2.7.6

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-2.7.6
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
foomatic-xml-install=yes
foomatic-ppd-install=no
internal-tag=2.7.6.13


----------------------
| INSTALLED PRINTERS |
----------------------

 
OfficeJet-4200
--------------
Type: Unknown
Installed in HPLIP?: No, not using the hp: or hpfax: CUPS backend.
Device URI: usb://hp/?serial=CN544GI3C1
PPD: /etc/cups/ppd/OfficeJet-4200.ppd
PPD Description: HP OfficeJet 4200 Foomatic/hpijs (recommended)
Printer status: printer OfficeJet-4200 is idle.  enabled since Mon 02 Jul 2007 06:29:30 PM EDT
error: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.


----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
 
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).


---------------------
| PYTHON EXTENSIONS |
---------------------

Checking 'cupsext' CUPS extension...
OK, found.

Checking 'pcardext' Photocard extension...
OK, found.

Checking 'hpmudext' I/O extension...
OK, found.

Checking 'scanext' SANE scanning extension...
OK, found.


-----------------
| USB I/O SETUP |
-----------------

Checking proper HPLIP I/O setup (USB I/O only)...
udev "usb_device" access mode: 0664 (OK)

Checking for permissions of USB attached printers...
HP Device 0x3d11 at 001:009: 
warning:     Device URI: (Makeuri FAILED)
    Device node: /dev/bus/usb/001/009
    Mode: 0664
    UID: 0 (root)
    GID: 7 (lp)
    Device group and mode appear correct.

Is user 'member1' a member of the 'lp' group?
Yes (OK)

Is user 'member2' a member of the 'lp' group?
Yes (OK)

Is user 'member3' a member of the 'lp' group?
Yes (OK)

Is user 'member4' a member of the 'lp' group?
Yes (OK)


-----------
| SUMMARY |
-----------

error: 1 error or warning.

---

### Post by 11hjpphty76lkjj on 2007-07-02
The printer has to be using the hp:// backend else you'll have problems.  Can you run:
```

/usr/lib/cups/backend/hp
```

and post the results.  Are you using a usb hub?

And your welcome. :D

---

### Post by LikeAbird on 2007-07-02
The code "/usr/lib/cups/backend/hp" gave me
> direct hp "Unknown" "HP Printer (HPLIP)"

Currently I'm using USB hub, but I tried to connect directly, too....didn't work.

Thanks.

---

### Post by LikeAbird on 2007-07-02
What I don't understand are:
1. How come System-Administration-Printing can detect the printer, even though there is no exact model (hp officejet 4215xi) but only I could choose 4200 instead, when hp-setup or xsane can not detect the printer.
2. Why there is no exact model (4215xi) in the list of the System-Administration-Printing (I don't know how I can call this short). Should I download any driver for this? I did some search but no success.

I wonder....:(

---


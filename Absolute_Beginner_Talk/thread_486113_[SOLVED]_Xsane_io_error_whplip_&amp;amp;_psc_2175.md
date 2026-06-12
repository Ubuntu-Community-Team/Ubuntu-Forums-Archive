---
title: "[SOLVED] Xsane io error w/hplip &amp;amp; psc 2175"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by matthewartz on 2007-06-27
Hi - I have an HP PSC 2175 that I'm trying to get scanning.  (On Feisty x64)

I downloaded and installed hplip-2.7.6 from sourceforge.  Did an automatic install, no errors, printing works.

When I try to use xsane to scan, I get a lengthy delay (average of about 90 seconds) followed by:
```
Failed to open device 'hpaio:/usb/PSC_2170_Series?serial=MY3CAF74D373': Error during device I/O
```

I tried 'sudo tail -f /var/log/messages' for 'sudo /etc/init.d/hplip restart' but no error messages.

sane-find-scanner returns that it did find the scanner:
```
martz@martz-laptop:~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x03f0 [Hewlett-Packard], product=0x2b11 [PSC 2170 Series]) at libusb:003:005
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
```

Results from hp-check:
```
martz@martz-laptop:~$ hp-check

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
Linux martz-laptop 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 x86_64 GNU/Linux

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

 
PDF
---
Type: Unknown
Installed in HPLIP?: No, not using the hp: or hpfax: CUPS backend.
Device URI: cups-pdf:/
PPD: /etc/cups/ppd/PDF.ppd
PPD Description: Generic PostScript Printer Foomatic/Postscript (recommended)
Printer status: printer PDF is idle.  enabled since Fri 15 Jun 2007 03:26:00 PM MDT
error: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.

PSC_2170
--------
Type: Printer
Installed in HPLIP?: Yes, using the hp: CUPS backend.
Device URI: hp:/usb/PSC_2170_Series?serial=MY3CAF74D373
PPD: /etc/cups/ppd/PSC_2170.ppd
PPD Description: HP PSC 2170 Foomatic/hpijs (recommended)
Printer status: printer PSC_2170 is idle.  enabled since Wed 27 Jun 2007 01:09:50 PM MDT


----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
device `hpaio:/usb/PSC_2170_Series?serial=MY3CAF74D373' is a Hewlett-Packard PSC_2170_Series all-in-one


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
HP Device 0x2b11 at 003:005: 
    Device URI: hp:/usb/PSC_2170_Series?serial=MY3CAF74D373
    Device node: /dev/bus/usb/003/005
    Mode: 0664
    UID: 0 (root)
    GID: 7 (lp)
    Device group and mode appear correct.

Is user 'martz' a member of the 'lp' group?
Yes (OK)

Is user 'test' a member of the 'lp' group?
Yes (OK)


-----------
| SUMMARY |
-----------

error: 1 error or warning.

Please refer to the installation instructions at:
http://hplip.sourceforge.net/install/index.html
```

This "error: 1" is the only other error I receive outside of the io error.

Other code results referenced in some of the other forum posts:
```
martz@martz-laptop:~$ sudo /etc/init.d/hplip restart
martz@martz-laptop:~$ scanimage -L
device `hpaio:/usb/PSC_2170_Series?serial=MY3CAF74D373' is a Hewlett-Packard PSC_2170_Series all-in-one
martz@martz-laptop:~$ /usr/lib/cups/backend/hp
direct hp:/usb/PSC_2170_Series?serial=MY3CAF74D373 "HP PSC 2170 Series" "HP PSC 2170 Series USB MY3CAF74D373 HPLIP" "MFG:HP;MDL:PSC 2170 Series;CLS:PRINTER;DES:PSC 2170 Series;SN:MY3CAF74D373;"
martz@martz-laptop:~$ lsmod | grep ppdev
ppdev                  11272  0 
parport                43404  3 ppdev,parport_pc,lp
```

Anyone have ideas?

---

### Post by matthewartz on 2007-06-27
Just noticed that running xsane from a terminal gives one other error response:
martz@martz-laptop:~$ xsane &
[1] 6285
martz@martz-laptop:~$ /home/martz/.gtkrc-2.0:2: error: scanner: unterminated string constant - e.g. `style'

---

### Post by matthewartz on 2007-06-28
*bump*

---

### Post by 11hjpphty76lkjj on 2007-06-29
can you run

tail -f /var/log/messages

and then try and scan and post the /var/log/messages log.

---

### Post by matthewartz on 2007-06-29
Away from the printer for the day, but will do so tonight.  Tried that once earlier and it didn't turn up any error messages, but will do so again.

Thanks!

---

### Post by matthewartz on 2007-06-30
First, apologies for the bump followed by inaction.  Wasn't intended to be that way - just ended up away from the PSC unexpectedly.

Per your suggestion, did tail -f /var/log/messages then launched xsane (via Applications > Graphics > Xsane) but not a single new line.  (Some other lines related to errors in Google Desktop, but I expected those.)

Verified that the plug was well connected to the back of the printer.  Unplugged the USB from the laptop and moved it to another port.  Resulting output below.
```
martz@martz-laptop:~$ tail -f /var/log/messages
Jun 30 14:00:36 localhost kernel: [  379.681195] usb 3-3.5: USB disconnect, address 3
Jun 30 14:00:36 localhost kernel: [  379.682041] hald-addon-keyb[4844] general protection rip:2b9982bb221b rsp:7fff285dbdd0 error:0
Jun 30 14:00:36 localhost kernel: [  380.010674] hald-addon-keyb[4845] general protection rip:2ba8ed41121b rsp:7fffbdd7f560 error:0
Jun 30 14:00:40 localhost kernel: [  381.798528] usb 1-2: new full speed USB device using ohci_hcd and address 3
Jun 30 14:00:41 localhost kernel: [  381.894072] usb 1-2: configuration #1 chosen from 1 choice
Jun 30 14:00:41 localhost kernel: [  381.896722] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x03F0 pid 0x2B11
Jun 30 14:00:41 localhost kernel: [  381.896982] scsi2 : SCSI emulation for USB Mass Storage devices
Jun 30 14:00:46 localhost kernel: [  384.119564] scsi 2:0:0:0: Direct-Access     HP       psc 2175         1.00 PQ: 0 ANSI: 2
Jun 30 14:00:46 localhost kernel: [  384.124045] sd 2:0:0:0: Attached scsi removable disk sda
Jun 30 14:00:46 localhost kernel: [  384.124084] sd 2:0:0:0: Attached scsi generic sg0 type 0
Jun 30 14:00:59 localhost kernel: [  390.050000] drivers/usb/class/usblp.c: usblp0: removed

```

The 390.05 line is where I launched xsane again.  No new lines appearing when I get the i/o error message.

Does the 390.05 signify that xsane is actually removing the usb link?

---

### Post by matthewartz on 2007-06-30
Installed gnome scanner and followed the same procedure (unplug printer from laptop, plug it back into laptop) then launched gnome scanner.  Identical results:
```
Jun 30 14:16:08 localhost kernel: [  814.902581] usb 1-2: USB disconnect, address 3
Jun 30 14:16:15 localhost kernel: [  817.916089] usb 1-2: new full speed USB device using ohci_hcd and address 4
Jun 30 14:16:15 localhost kernel: [  818.011635] usb 1-2: configuration #1 chosen from 1 choice
Jun 30 14:16:15 localhost kernel: [  818.014273] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 4 if 1 alt 0 proto 2 vid 0x03F0 pid 0x2B11
Jun 30 14:16:15 localhost kernel: [  818.014540] scsi3 : SCSI emulation for USB Mass Storage devices
Jun 30 14:16:20 localhost kernel: [  820.237173] scsi 3:0:0:0: Direct-Access     HP       psc 2175         1.00 PQ: 0 ANSI: 2
Jun 30 14:16:20 localhost kernel: [  820.241679] sd 3:0:0:0: Attached scsi removable disk sda
Jun 30 14:16:20 localhost kernel: [  820.241744] sd 3:0:0:0: Attached scsi generic sg0 type 0
Jun 30 14:16:36 localhost kernel: [  827.133009] drivers/usb/class/usblp.c: usblp0: removed

```
No messages in /var/log/messages but gnome scanner returns a very similar error: "The scan backend returned the following error: Error during device I/O"

---

### Post by matthewartz on 2007-07-17
Did a full uninstall of 2.7.6 and installed 1.7.4 using the sh installer from sourceforge.  Install was clean, HP Device Manager (i.e. hp-toolbox) works perfectly this time, no errors on install.

However, still getting that same error when I try to scan.  

Followed the advice of kalosaurusrex over on another post:
[INDENT]sudo /etc/init.d/hplip restart
sudo /etc/init.d/cupsys restart
then delete the printer from hp-toolbox. Then reconnect the printer and run:
sudo hp-setup[/INDENT]

Reinstalled the printer, same result when I try to scan.

Here's the output from hp-check
```
martz@martz-laptop:~$ hp-check
Traceback (most recent call last):
  File "/usr/bin/hp-check", line 37, in <module>
    from installer import dcheck, distros
ImportError: No module named installer
```

Output from tail -f /var/log/messages
```
martz@martz-laptop:~$ tail -f /var/log/messages
Jul 17 10:27:18 localhost kernel: [ 6311.068347] SCSI device sda: 2014992 512-byte hdwr sectors (1032 MB)
Jul 17 10:27:18 localhost kernel: [ 6311.074343] sda: Write Protect is off
Jul 17 10:27:18 localhost kernel: [ 6311.098312] SCSI device sda: 2014992 512-byte hdwr sectors (1032 MB)
Jul 17 10:27:18 localhost kernel: [ 6311.104300] sda: Write Protect is off
Jul 17 10:27:19 localhost kernel: [ 6311.104333]  sda: sda1
Jul 17 10:27:19 localhost kernel: [ 6311.121429] sd 2:0:0:0: Attached scsi removable disk sda
Jul 17 10:27:19 localhost kernel: [ 6311.121483] sd 2:0:0:0: Attached scsi generic sg0 type 0
Jul 17 10:28:01 localhost hpiod: removing usblp driver interface=1 for hp:/usb/PSC_2170_Series?serial=MY3CAF74D373 io/hpiod/device.cpp 504 
Jul 17 10:28:01 localhost kernel: [ 6352.476390] drivers/usb/class/usblp.c: usblp0: removed
Jul 17 10:30:19 localhost hpiod: device cleanup uri=hp:/usb/PSC_2170_Series?serial=MY3CAF74D373 
Jul 17 10:43:14 localhost hpiod: device cleanup uri=hp:/usb/PSC_2170_Series?serial=MY3CAF74D373
``` 

10:27 is the reconnect and reinstall.  10:30 and 10:43 are the attempt to scan.    10:28:01 is the one that catches my eye - something wrong there?

---

### Post by 11hjpphty76lkjj on 2007-07-17
Actually if you could go back to 2.7.6 it would be easier for us to troubleshoot because that's the latest release.

hp-check isn't working because I believe there is a mess of hplip installs.

Lets uninstall hplip, and re-install, and then run hp-check. Should tell us a lot.  If possible stick with 2.7.6..

sudo rm -rf /usr/share/hplip

and then install using the automatic installer.

And finally run hp-check.

A

---

### Post by matthewartz on 2007-07-17
Okay, per your request, back to 2.7.6.  (Ran the uninstall, removed /usr/share/hplip, etc.)  Used the installer to add 2.7.6 back in, chose all the defaults (PSC2170 driver, though it's a 2175).

Still getting the i/o error when I try to scan (via xsane, gnome scanner, or HP toolbox).

Here's the hp-check output
```
martz@martz-laptop:/$ hp-check

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
Linux martz-laptop 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 x86_64 GNU/Linux

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

 
PDF
---
Type: Unknown
Installed in HPLIP?: No, not using the hp: or hpfax: CUPS backend.
Device URI: cups-pdf:/
PPD: /etc/cups/ppd/PDF.ppd
PPD Description: Generic PostScript Printer Foomatic/Postscript (recommended)
Printer status: printer PDF is idle.  enabled since Fri 06 Jul 2007 10:27:09 AM MDT
error: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.

PSC_2170
--------
Type: Printer
Installed in HPLIP?: Yes, using the hp: CUPS backend.
Device URI: hp:/usb/PSC_2170_Series?serial=MY3CAF74D373
PPD: /etc/cups/ppd/PSC_2170.ppd
PPD Description: HP PSC 2170 Foomatic/hpijs (recommended)
Printer status: printer PSC_2170 disabled since Tue 17 Jul 2007 11:51:44 AM MDT -       Filter "foomatic-rip" for printer "PSC_2170" not available: No such file or directory


----------------------
| SANE CONFIGURATION |
----------------------

'hpaio' in '/etc/sane.d/dll.conf'...
OK, found. SANE backend 'hpaio' is properly set up.

Checking output of 'scanimage -L'...
device `hpaio:/usb/PSC_2170_Series?serial=MY3CAF74D373' is a Hewlett-Packard PSC_2170_Series all-in-one


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
HP Device 0x2b11 at 001:007: 
    Device URI: hp:/usb/PSC_2170_Series?serial=MY3CAF74D373
    Device node: /dev/bus/usb/001/007
    Mode: 0664
    UID: 0 (root)
    GID: 7 (lp)
    Device group and mode appear correct.

Is user 'martz' a member of the 'lp' group?
Yes (OK)

Is user 'test' a member of the 'lp' group?
Yes (OK)


-----------
| SUMMARY |
-----------

error: 1 error or warning.

Please refer to the installation instructions at:
http://hplip.sourceforge.net/install/index.html
```

And here's the tail -f /var/log/messages
```
Jul 17 11:43:18 localhost python: hplip-install[24576]: note: Defaults for each question are maked with a '*'. Press <enter> to accept the default.
Jul 17 11:43:33 localhost python: hplip-install[24576]: note: Password accepted.
Jul 17 11:49:51 localhost kernel: [ 9212.086493] usb 1-2: new full speed USB device using ohci_hcd and address 7
Jul 17 11:49:51 localhost kernel: [ 9212.300819] usb 1-2: configuration #1 chosen from 1 choice
Jul 17 11:49:51 localhost kernel: [ 9212.306765] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 7 if 1 alt 0 proto 2 vid 0x03F0 pid 0x2B11
Jul 17 11:49:51 localhost kernel: [ 9212.307137] scsi3 : SCSI emulation for USB Mass Storage devices
Jul 17 11:49:56 localhost kernel: [ 9217.308922] scsi 3:0:0:0: Direct-Access     HP       psc 2175         1.00 PQ: 0 ANSI: 2
Jul 17 11:49:56 localhost kernel: [ 9217.318973] sd 3:0:0:0: Attached scsi removable disk sda
Jul 17 11:49:56 localhost kernel: [ 9217.319023] sd 3:0:0:0: Attached scsi generic sg0 type 0
Jul 17 11:50:05 localhost kernel: [ 9222.963542] drivers/usb/class/usblp.c: usblp0: removed

```

---

### Post by 11hjpphty76lkjj on 2007-07-17
Everything looks good.  You can print okay?  Are you going through a usb hub?  Has it ever worked? If so when did it work last?

A

---

### Post by matthewartz on 2007-08-06
Think the problem might have had other sources.

Did a clean install of Ubuntu, used default hplip from distribution, and all works fine (printing & scanning).

---

### Post by FXFman1209 on 2007-10-22
Hang on, I'm still having the SAME exact problem. I have installed a the new Gutsy and I'm getting this, and it is also happening on my Feisty machine (which I know used to work, but I may have upgraded sane or osmething without knowing).

Can anyone help?

---

### Post by hardawayd on 2007-10-29
I am having the same problem also.

---

### Post by blackest_knight on 2008-02-11
I am part way through this scanning problem looks like i can use xsane as root probably not a great idea, but i think that its a permissions issue.

---


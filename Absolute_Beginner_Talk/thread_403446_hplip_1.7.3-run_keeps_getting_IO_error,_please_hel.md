---
title: "hplip 1.7.3-run keeps getting IO error, please help!"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2007-04-07
I am running Dapper on my laptop here at home, and trying to run the hplip 1.7.3-run installer. I use the command (in terminal) sudo sh hplip-1.7.3.run. Everyting goes just fine until the end where I should configure the printer but all I keep getting is
 
"X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
error: Unable to connect to hpiod.
error: Unable to connect to HPLIP I/O. Please (re)start HPLIP and try again."

Any idea why I keep getting this error? I did the same install on my desktop (Compaq 5900Z with Dapper running) and all went just fine--set up the printer and it works great. The HP C5140 is a network printer used by three comps, two running Dapper and one running XP. The XP and Compaq both print just fine, and all comps can ping each other and the printer just fine. This laptop is the only one showing me this error everytime. Any clues to a fix for this?? Thanks again for the help.

---

### Post by jerrynewt on 2007-04-07
Any ideas ??

---

### Post by pixeldotz on 2007-04-08
i'm getting the same error trying to get the latest hplip for 1315 hp.

can anyone help us out?

---

### Post by rajeev1204 on 2007-04-08
What about hplip from synaptic?

That isnt working for u folks?

---

### Post by 11hjpphty76lkjj on 2007-04-09
If you are getting the i/O error try restarting HPLIP.

```
sudo /etc/init.d/hplip restart
```

```
sudo /etc/init.d/cupsys restart
```

and try again.  If you have the same problem after restarting hplip run

```
sudo tail -f /var/log/messages
```

and then in a seperate terminal window run:

```
sudo /etc/init.d/hplip restart
```

and post any messages in /var/log/messages.

A

---

### Post by pondochris on 2007-05-14
I am trying to install a HP D4160 and am getting the same results
```
May 14 03:02:16 Chris gconfd (root-22469): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
May 14 03:02:16 Chris gconfd (root-22469): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
May 14 03:02:46 Chris gconfd (root-22469): SIGHUP received, reloading all databases
May 14 03:02:46 Chris gconfd (root-22469): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May 14 03:02:46 Chris gconfd (root-22469): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
May 14 03:02:46 Chris gconfd (root-22469): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May 14 03:02:46 Chris gconfd (root-22469): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
May 14 03:02:46 Chris gconfd (root-22469): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
May 14 03:02:46 Chris gconfd (root-22469): GConf server is not in use, shutting down.
May 14 03:02:46 Chris gconfd (root-22469): Exiting
^[[A


```
then when I open up another terminal and run  sudo /etc/init.d/hplip restart
I get this
```
Stopping hpiod:                                            [  OK  ]
Stopping hpssd: /etc/init.d/hplip: line 57: kill: (22658) - No such process
                                           [FAILED]
Starting hpiod:                                            [  OK  ]
Starting hpssd:    
```
Hope this helps someone help me and anybody else :)

---

### Post by 11hjpphty76lkjj on 2007-05-14
Can you please run hp-check and post the output?

A

---

### Post by pondochris on 2007-05-14
hp-check?  said command not found for that...however I did try this...```
chris@Chris:~$ sudo /etc/init.d/hplip status
hpiod (pid 7696) is running...
hpssd (pid 7699) is running...

```

I'm confused :confused:

---

### Post by pondochris on 2007-05-14
I installed hplip 1.7.4a and at the end I got this
```
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Unable to connect to HPLIP I/O (hpssd).
error: Unable to connect to HPLIP I/O. Please (re)start HPLIP and try again.

```
I then ran hp-check
```
HP Linux Imaging and Printing System (ver. 1.7.4a)
Dependency/Version Check Utility ver. 5.3

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.


---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux Chris 2.6.20-15-386 #2 Sun Apr 15 07:34:00 UTC 2007 i686 GNU/Linux

Detected distro (/etc/issue):
ubuntu 7.04

Detected distro (lsb_release):
Ubuntu 7.04 (feisty)

Currently installed HPLIP version...
HPLIP 1.7.4a currently installed in '/usr/share/hplip'.

Current contents of '/etc/hp/hplip.conf' file:
# hplip.conf

[hpiod]
# port=0 (dynamic IP port)
port=2208
[hpssd]
# port=0 (dynamic IP port)
port=2207

[hplip]
version=1.7.4a
jdprobe=0

[dirs]
home=/usr/share/hplip
run=/var/run
ppd=/usr/share/ppd/HP
ppdbase=/usr/share/ppd
doc=/usr/share/doc/hplip-1.7.4a

# Following values are determined at configure time and cannot be changed.
[configure]
network-build=1
pp-build=0
gui-build=1
scanner-build=1
fax-build=1
cups11-build=0
installinitd=/usr/lib/lsb/install_initd
chkconfig=
internal-tag=1.7.4.13


HPLIP running?
Yes, HPLIP is running (OK).

HPOJ running?
No, HPOJ is not running (OK).

Checking Python version...
OK, version 2.5.1 installed

Checking PyQt version...
OK, version 3.17 installed.

Checking SIP version...
OK, Version 4.5 installed

----------------
| DEPENDENCIES |
----------------

 
Checking for dependency libcrypto - OpenSSL cryptographic library...
OK, found.

Checking for dependency gcc - GNU Project C and C++ Compiler...
OK, found.

Checking for dependency SANE - Scanning library...
OK, found.

Checking for dependency GhostScript - PostScript and PDF language interpreter and previewer...
OK, found.

Checking for dependency libjpeg - JPEG library...
OK, found.

Checking for dependency libpthread - POSIX threads library...
OK, found.

Checking for dependency make - GNU make utility to maintain groups of programs...
OK, found.

Checking for dependency python-devel - Python development files...
OK, found.

Checking for dependency Reportlab - PDF library for Python...
OK, found.

Checking for dependency PyQt - Qt interface for Python...
OK, found.

Checking for dependency cups-devel- Common Unix Printing System development files...
OK, found.

Checking for dependency ppdev - Parallel port support kernel module....
OK, found.

Checking for dependency libusb - USB library...
OK, found.

Checking for dependency scanimage - Shell scanning program...
OK, found.

Checking for dependency libnetsnmp-devel - SNMP networking library development files...
OK, found.

Checking for dependency Python 2.2 or greater - Python programming language...
OK, found.

Checking for dependency LSB - Linux Standard Base support...
OK, found.

Checking for dependency xsane - Graphical scanner frontend for SANE...
OK, found.

Checking for dependency cups - Common Unix Printing System...
OK, found.

Checking for dependency Python 2.3 or greater - Required for fax functionality...
OK, found.


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


No errors detected.

```

---

### Post by 11hjpphty76lkjj on 2007-05-15
Everything looks okay.  Run:

sudo /etc/init.d/hplip restart

then

sudo hp-setup

A

---

### Post by pondochris on 2007-05-18
pulling out my hair here...I get the same thing but now with new stuff...the hp device manager comes up and just seems to keep searching but never does anything else... is there something I'm just not getting?```
chris@chris-desktop:~$ sudo hp-setup

HP Linux Imaging and Printing System (ver. 1.7.4a)
Printer/Fax Setup Utility ver. 4.5

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Traceback (most recent call last):
  File "/usr/share/hplip/ui/setupform.py", line 202, in showPage
    devices_found = self.updateProbedDevicesPage()
  File "/usr/share/hplip/ui/setupform.py", line 368, in updateProbedDevicesPage
    devices = device.probeDevices(self.hpiod_sock, self.bus, self.timeout, self.ttl, self.filter, self.search) # net_search='slp'
  File "/usr/share/hplip/base/device.py", line 379, in probeDevices
    xmitMessage(hpiod_sock, "ProbeDevices", None, {'bus' : bus,})
  File "/usr/share/hplip/base/msg.py", line 165, in xmitMessage
    raise Error(ERROR_INTERNAL)
base.g.Error: ('Unknown internal error', 99)



``` I have searched just about everywhere I think and tried stuff here and there that people say to do but I still haven't gotten anywhere

---

### Post by pondochris on 2007-05-21
:grin::guitar::lolflag::-\"\\:D/:cry:with tears of joy even....test page now printing!!!!!!! I did some searching and a whole lot of reading.  I stumbled across some stuff about .ppd files, went into synaptic and voila!!! there was a package named hplip .ppd files or something like that.  I installed it then re-installed hplip-1.7.4a and to my amazement my printer was actually set up successfully!!!  Thanks for being here even though I may have been more help to myself...It's good to know I'm not incompetent...just maybe impatient lol.

---


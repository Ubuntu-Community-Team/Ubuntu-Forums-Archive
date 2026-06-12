---
title: "pctel modem"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by Rory from the Rock on 2007-02-12
Hi,

I am trying to download the new driver for my pctel hsp56 micromodem.  The only internet connection that I have is on a windows box.  I was wondering if it is possible to download the file on the windows box and burn it.  Insert the disk on the linux box and extract and install.

Thanks for any help...R.

---

### Post by Rory from the Rock on 2007-02-19
New Question...

I downloaded the driver and burned it.  Seems to have worked fine.
I was following the directions for Ubuntu-txt on the DL page.


The pctel-0.9.7-9-rht-6_for_Ubuntu-2.6.15-23-386.tgz has precompiled
drivers suitable for use ONLY with Ubuntu kernel 2.6.15-23-386.
Copy it into your Linux partition.
Open a command console.  Verify that the package is displayed by:
$ ls pctel*
If not change directory (cd)  to the correct folder and recheck.

Unpack with:
$  tar zxf pctel*.tgz
THere should be a new folder pctel-0.9.7-9-rht-6
Check with:
$ ls -d  pctel*
Move into it with
$  cd pctel-0.9.7-9-rht-6
Look around:
$ ls
Move into the src/  folder
$ cd  src
$ ls

The drivers to be installed are selectively displayed with:
$   ls *.ko
     linmodem.ko  pctel_hw.ko  pctel.ko
Install then with Root priviledges with:
$ sudo  make install

Back down a folder:
$  cd  ../
Read the documentation on how to proceed further.


But briefly, the drivers will be loaded by
$ sudo  modprobe pctel
Check with
$  lsmod | grep pctel

If loaded the modem should be found  at  /dev/ttyS_PCTEL0  by:
$  sudo wvdialconf  /etc/wvdial.conf
Edit in your personal information with
$  sudo gedit /etc/wvdial.conf
to the format below:

[Dialer Defaults]
Modem = /dev/ttyS_PCTEL0
Baud = 115200
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Phone =  3015560020
Username = YourLoginName
Password = YourLoginPassWord

### to make a record
# wvdial 2>&1 | tee wvdial.out

## usually not necessary
# Auto DNS = yes
#### End wvdial.conf

Then you should be able to dialout with:
$ sudo wvdial

Once online do enjoy browsing for a while.  Then do:
$ sudo  apt-get update
$ sudo apt-get upgrade

This will correct the problem causing the compile failure:
   error : stdio.h
You should then be able to compile your own drivers for other kernels,
following the standard instructions.

"I got to the...Read the documentation on how to proceed further...and did not know how to open the faq file.  When I "sudo modprobe pctel" the computer tried to find my modem but this  came up...Sorry could not find your modem... Did you configure it properly with setserial.

I do not know if it was configured properly or not...

Also when I went back to the src directory and ls  this is what is now in that directory
configure linmodem-2.6.c  Make log  ptserial-2.6.h
i8xxhal.s linmodem-2.6.h  ptmodule.c  ptserial_hw2.6.c
include Make file~ ptserial-2.4.6.c   ptserial_pci-2.6.c
inst Makefile-2.4.in ptserial-2.4.7.c ptserial_pci-2.6.0
Lib Makefile-2.6.in ptserial-2.6.c  ptserial_pci-2.6.0
                                               uart.s


This is as far as I got..


Help

---

### Post by helmut_hed on 2007-03-26
Hi Rory,

Have you tried following these instructions:

[http://ubuntuforums.org/showthread.php?t=171163](http://ubuntuforums.org/showthread.php?t=171163)

I'm one of the maintainers of the driver and I'll be happy to help you debug anything that goes wrong.

Cheers,
Jeff
PS: I'm not sure about the other thing you downloaded, but please try this approach instead.

---


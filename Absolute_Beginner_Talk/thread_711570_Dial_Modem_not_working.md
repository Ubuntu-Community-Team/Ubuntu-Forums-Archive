---
title: "Dial Modem not working"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by imranmalik on 2008-02-29
hi all, i configured my dial up modem using wvdialcong and pppconfig.
pppconfig did nothing good at all.
but wvdial configured my modem and i was able to dial but after dial i got the following results.



imranmalik@imranmalik-laptop:~$ wvdial de

WvDial<*1>: WvDial: Internet dialer version 1.56

WvModem<*1>: Cannot get information for serial port.

WvDial<*1>: Initializing modem.

WvDial<*1>: Sending: ATZ
Wv
Dial Modem<*1>: ATZ

WvDial Modem<*1>: OK

WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0

WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0

WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.

WvDial<*1>: Sending: ATDT13112000
WvDial<*1>: Waiting for carrier.

WvDial Modem<*1>: ATDT13112000

WvDial Modem<*1>: NO DIALTONE
WvDial<Err>: No dial tone.

WvDial<*1>: Disconnecting at Sat Mar  1 04:39:58 2008

imranmalik@imranmalik-laptop:~$ 

There was no dial tone while the same modem with the same telephone line is working fine in windows. 
anyone can help???? please?

---

### Post by AnonCat on 2008-02-29
Do you know which chipset your modem is using (often Smartlink or Connexant)? Give us more information about your modem, have you installed the slamr and ungrabwinmodem drivers for instance if it's a Smartlink modem?  Also, is this an external hardware modem or an internal modem?  Please provide as much information as you can.  Post the "modemdata.txt" file from the scanmodem utility you can find at the site linked to below:

[http://linmodems.technion.ac.il/](http://linmodems.technion.ac.il/)

---

### Post by imranmalik on 2008-03-01
thanx for ur attention
my modem details  are as below
      Conexant M360, 6000 Series Modem Driver 

      Version: 7.18.00.50
below are the results of ModemData.txt
**************************************************************************************
CPU=i686,  
Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007
 scanModem update of:  2008_02_25
The modem symbolic link is /dev/modem -> ttySL0
The slmodemd set symbolic link is /dev/ttySL0 -> /dev/pts/0

 There are no blacklisted modem drivers in /etc/modprobe*  files 

The Advanced Linux Sound Architecture (ALSA) packages providing audio support, 
also includes drivers for some modems. The ALSA diagnostics are written during 
bootup to /proc/asound/ folders.

 The /proc/asound/ audio+modem diagostics are being copied.
 Finished copy to Modem/ALSAroot.tgz

The ALSA verion is 1.0.14
The modem cards detected by "aplay -l"  are:
card 1: Modem [Intel 82801DB-ICH4 Modem], device 0: Intel ICH - Modem [Intel 82801DB-ICH4 Modem - Modem]

The /proc/asound/pcm file reports:
-----------------------
00-04: Intel ICH - IEC958 : Intel 82801DB-ICH4 - IEC958 : playback 1
00-03: Intel ICH - ADC2 : Intel 82801DB-ICH4 - ADC2 : capture 1
00-02: Intel ICH - MIC2 ADC : Intel 82801DB-ICH4 - MIC2 ADC : capture 1
00-01: Intel ICH - MIC ADC : Intel 82801DB-ICH4 - MIC ADC : capture 1
00-00: Intel ICH : Intel 82801DB-ICH4 : playback 1 : capture 1
01-00: Intel ICH - Modem : Intel 82801DB-ICH4 Modem - Modem : playback 1 : capture 1

about /proc/asound/cards:
------------------------
 0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with unknown codec at irq 5
 1 [Modem          ]: ICH-MODEM - Intel 82801DB-ICH4 Modem
                      Intel 82801DB-ICH4 Modem at irq 5


The driver snd-intel8x0m with its dependent drivers:
snd_intel8x0m          18572  5 
snd_ac97_codec        100644  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0
snd_pcm                80388  8 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd                    54660  23 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         11400  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_pcm
----------
provide modem + audio support.

Lines in: /proc/asound/card1/codec97#0/mc97#0-0+regs
-------------------------------
0:7c = 4358  and  0:7e = 5430
are translated from hexadecimal code into the modem chip identifier:  CXT30

 Support if provided only through hsfmodem drivers.  Read Conexant.txt
USB modem not detected by lsusb

For candidate card in slot 00:1f.6, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1f.6	8086:24c6	107b:0360	Modem: Intel Corporation 82801DB/DBL/DBM 

 Modem interrupt assignment and sharing: 
  5:       1303    XT-PIC-XT        Intel 82801DB-ICH4, Intel 82801DB-ICH4 Modem
 --- Bootup diagnostics for card in PCI slot 00:1f.6 ----


 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===


Predictive diagnostics for card in bus 00:1f.6:
	Modem chipset  detected on
CLASS="Class 0703: 8086:24c6"
NAME="Modem: Intel Corporation 82801DB/DBL/DBM "
PCIDEV=8086:24c6
SUBSYS=107b:0360
SUBven=107b
IRQ=5
IDENT=hsfmodem
CODECd=CXT30
COD=CXT
Driver=snd-intel8x0m
SOFT=8086:24c6.MC97

 For candidate modem in:  00:1f.6
   Class 0703: 8086:24c6 Modem: Intel Corporation 82801DB/DBL/DBM
      Primary PCI_id  8086:24c6
    Subsystem PCI_id  107b:0360 
    Softmodem codec or chipset from diagnostics: CXT30, a Conexant type using hsfmodem software.
                               from    Archives: 
      CXT is  a generic for all CXTnumbers, with  Linuxant hsfmodem software support.                  
      

 This is a NEW softmodem case!  Please send the output ModemData.txt 
 to [email]DISCUSS@linmodems.org[/email] to enrich the Archive and help others!
 If further assistance is not needed, please use email Subject:
     New Case Only
 -------------------------------------------
 Lacking a dsp (digital signal processing) chip, the modem is a software 
 intensive or "softmodem" type. Its primary controller manages the traffic 
 with the CPU. But the software needed is specified in the Subsystem.
 -----------------------------------------
Support type needed or chipset:	hsfmodem


Writing Intel.txt

For owners of a Dell PCs with Conexant HSF modems, a driver source package with full speed enabled is available, but requires driver compiling. Read Conexant.txt

 The hsfmodem package serves a great variety of Conexant chipset modems. 
 From  [http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php](http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php)
 download hsfmodem_hsfmodem_7.68.00.07full_k.deb.zip 
                           with 2.6.22_14_generic equivalent to 2.6.22-14-generic, your kernel version.
 Under Linux unpack with:
 $ unzip hsfmodem*.zip
 Then install with:
 $ sudo dpkg -i hsfmodem*.deb
 Subsequently, the modem should be found with
 $ sudo wvdialconf /etc/wvdial.conf
 Edit in your personal information with:
 $ sudo gedit /etc/wvdial.conf
 and try dialing out with:
 $ sudo wvdial.
 See Testing.txt  for details.
 
 Read Conexant.txt

Writing Conexant.txt


 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.1.3
             and the compiler used in kernel assembly: 4.1.3


 
 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.1
   linuc_headers base folder /lib/modules/2.6.22-14-generic/build

 However some compilations and executable functions may need additional files,
 in the FileNames.h (so called kernel "h"eaders) collection installed in  /usr/include/ .
 For martian_modem, additional required packages are libc6-dev (and for Debian/Ubuntu,  linux-libc-dev). The also required headers of package libc6 are commonly installed by default. 



If a driver compilation fails, with message including some lack of some FileName.h (stdio.h for example), then
Some additional kernel-header files need installation to /usr/include. The minimal additional packages are libc6-dev
and any of its dependents, under Ubuntu linux-libc-dev

If an alternate ethernet connection is available,
$  apt-get update
$  apt-get -s install linux-kernel-devel
will install needed package
For Debian/Ubuntu related distributions, run the following command to display the needed package list:

Otherwise packages have to be found through [http://packages.ubuntu.com](http://packages.ubuntu.com)
Once downloaded and transferred into a Linux partition,
they can be installed alltogether with:
$ sudo dpkg -i *.deb


Checking pppd properties:
	-rwsr-xr-- 1 root dip 269256 2007-10-05 00:57 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    [http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html](http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html)

To enable dialout without Root permission do:
	$ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
	sudo chmod a+x /usr/sbin/pppd

Checking settings of:	/etc/ppp/options
asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

In case of a message like:
   Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
see [http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html](http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html)

Read Modem/YourSystem.txt concerning other COMM channels: eth0 ppp0
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for the experts
 should trouble shooting be necessary.
==========================================================

# start/stop the daemon when the USB modem is connected
KERNEL=="slusb[0-9]*", GROUP="dialout", RUN+="/etc/init.d/sl-modem-daemon"
 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   lrwxrwxrwx 1 root root 6 2008-03-02 03:15 /dev/modem -> ttySL0
slmodemd created symbolic link /dev/ttySL0:  lrwxrwxrwx 1 root root 10 2008-03-02 03:16 /dev/ttySL0 -> /dev/pts/0
     Within /etc/udev/ files:
/etc/udev/rules.d/030_sl-modem-daemon.rules:# start/stop the daemon when the USB modem is connected
/etc/udev/rules.d/030_sl-modem-daemon.rules:KERNEL=="slusb[0-9]*", GROUP="dialout", RUN+="/etc/init.d/sl-modem-daemon"
/etc/udev/sl-modem-daemon.rules:# start/stop the daemon when the USB modem is connected
/etc/udev/sl-modem-daemon.rules:KERNEL=="slusb[0-9]*", GROUP="dialout", RUN+="/etc/init.d/sl-modem-daemon"
     Within /etc/modprobe.conf files:
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
/etc/modprobe.d/sl-modem-daemon.modutils:install slamr modprobe --ignore-install ungrab-winmodem ;  modprobe --ignore-install slamr; test -e /dev/slamr0 || (/bin/mknod -m 660 /dev/slamr0 c 242 0 2>/dev/null && chgrp dialout /dev/slamr0) 
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------
******************************************************************************
i hope this huge bulk of text will not bother u :)

i also tried wvdialconf
the configuration file is as under

------------------------------=====================-------------------------------------------------------

[Dialer Def]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Phone = 13112000
Modem = /dev/ttySL0
Username = wfk85neb
Password = *******
Baud = 460800
when i dial this, i get an error saying that "There was no dial tone" while my phone line is fine and IT IS Connected as well (i mean i m sure that the phone is attached)
thanks

---

### Post by Kalawala on 2008-05-21
i also am having this problem so i was wondering were you able to find the answer?

---


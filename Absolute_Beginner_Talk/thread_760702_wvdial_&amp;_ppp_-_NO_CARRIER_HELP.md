---
title: "wvdial &amp; ppp - NO CARRIER HELP"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by lkraemer on 2008-04-20
I am requesting help to get Ubuntu Ver 7.10 working with my internal modem.
I have the modem drivers installed, wvdial configured, ppp configured, but
modem still will not connect either with wvdial or ppp.  What am I missing?

Ubuntu 7.10 - Motorola SM56 Speakerphone Modem installed in Gateway MT6840 Laptop
as per Windows XP Control Panel.

STEPS I have done so far:

1. Download scanModem, and execute it to find the modems information.

NOTE: Always use the most recent update of scanModem accessed ONLY at
      [http://linmodems.technion.ac.il/packages/scanModem.gz](http://linmodems.technion.ac.il/packages/scanModem.gz)


2. Review document /modem/ModemData.txt ..... as follows:

 Only plain text email is forwarded by the  [email]Discuss@Linmodems.org[/email] List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.22-14-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Your contry's local Linux experts
 can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html). 
They will know your Country's modem code, which may be essential for dialup service.
Responses from [email]Discuss@Linmodems.org[/email] are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) 
--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease)
(Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008  scanModem update of:  2008_04_16

 There are no blacklisted modem drivers in /etc/modprobe*  files 
USB modem not detected by lsusb

For candidate card in slot 00:1b.0, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1b.0	8086:27d8	107b:0366	Audio device: Intel Corporation 82801G 

 Modem interrupt assignment and sharing: 
 21:        752          0   IO-APIC-fasteoi   HDA Intel
 --- Bootup diagnostics for card in PCI slot 00:1b.0 ----
[   14.532000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   14.532000] PCI: Setting latency timer of device 0000:00:1b.0 to 64


===== Advanced Linux Sound Architecture (ALSA) diagnostics ===== 
The ALSA packages provide audio support and also drivers for some modems.
ALSA diagnostics are written during bootup to /proc/asound/ folders.
 PCI slot 00:1b.0 has a High Definition Audio Card

The ALSA verion is 1.0.14
The modem cards detected by "aplay -l"  are:
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]

The /proc/asound/pcm file reports:
-----------------------
00-06: Si3054 Modem : Si3054 Modem : playback 1 : capture 1
00-00: STAC92xx Analog : STAC92xx Analog : playback 1 : capture 2

about /proc/asound/cards:
------------------------
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd8240000 irq 21

Modem support under STAC92xx audio card hosts may require upgrade
of snd-hda-intel + its dependent drivers to ALSA version  1.0.16.
The following modem only worked after the upgrade from to 1.0.16 from 1.0.14
 PCI ID      SubsystemID     Name
 ---------   ---------       --------------
 8086:27d8   107b:0366       Audio device: Intel Corporation 82801G
with ALSA diagnostics
00-00: STAC92xx Analog : STAC92xx Analog : playback 1 : capture 2
00-06: Si3054 Modem : Si3054 Modem : playback 1 : capture 1
       Codec: Motorola Si3054
            for 107b:0366 hosted modem chip: 0x10573057

For a standard Ubuntu system needed to support the driver compilation were

 The modem codec file for the the HDA card is: /proc/asound/card0/codec#1
--------------------------------------------------------
Codec: Motorola Si3054
Address: 1
Vendor Id: 0x10573057
Subsystem Id: 0x10001
Revision Id: 0x100100

 The audio card hosts a softmodem chip:  0x10573057

The softmodem chip 0x10573057 is in principle supported by the COMM support of slmodemd 
and the joint snd-hda-intel audio+modem driver, begun with ALSA version 1.0.13.  
For HDA cards with ALC883 chips, an upgrade to ALSA verions 1.0.15 way be necessary.
Instructions for upgrading snd-hda-intel and its dependent driver set are at:
[http://linmodems.technion.ac.il/archive-seventh/msg00282.html](http://linmodems.technion.ac.il/archive-seventh/msg00282.html)

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive diagnostics for card in bus 00:1b.0:
	Modem chipset  detected on
CLASS="Class 0403: 8086:27d8"
NAME="Audio device: Intel Corporation 82801G "
PCIDEV=8086:27d8
SUBSYS=107b:0366
IRQ=21
HDA=8086:27d8
SOFT=8086:27d8.HDA
CodecArchived=10573057
CHIP=0x10573057
IDENT=slmodemd
SLMODEMD_DEVICE=hw:0,6
Driver=snd-hda-intel

 For candidate modem in:  00:1b.0
   Class 0403: 8086:27d8 Audio device: Intel Corporation 82801G
      Primary PCI_id  8086:27d8
    Subsystem PCI_id  107b:0366 
    Softmodem codec or chipset from diagnostics: 0x10573057
                               from    Archives: 0x10573057
                        The HDA card softmodem chip is 0x10573057
      

Support type needed or chipset:	slmodemd supporting the snd-hda-intel audio+modem driver

 An ALSA (Advanced Linux Sound Architecture) modem driver:  snd-hda-intel
 provides Low Level support enabling contact with the modem hardware.
 For all BUT Conexant chip soft modems (using hsfmodem software)
 complementary High Level support is through a Smartlink utility:  slmodemd

 Download from [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/) 
 the package SLMODEMD.gcc4.1.tar.gz having a compiled slmodemd. Unpack under Linux with:
 	$ tar zxf SLMODEMD.gcc4.1.tar.gz
 and read instructions therein. But briefly, the modem is setup with command:
 	sudo slmodemd -c YOUR_COUNTRY --alsa hw:0,6
 reporting dynamic creation of ports:
	/dev/ttySL0 --> /dev/pts/N   , with N some number
 Read Smartlink.txt and Modem/YourSystem.txt for follow through guidance.

----------------end Softmodem section --------------

Writing Intel.txt
Writing Smartlink.txt
============ end Smartlink section =====================

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
	-rwsr-xr-- 1 root dip 269256 2007-10-04 12:57 /usr/sbin/pppd

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

Read Modem/YourSystem.txt concerning other COMM channels: eth0
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for the experts
 should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:

     Within /etc/modprobe.conf files:
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------



3.Downloaded slmodemd & installed modem driver

[http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/) 
 the package SLMODEMD.gcc4.1.tar.gz having a compiled slmodemd.
Open a Terminal window
 Unpack under Linux with:
gzip -d scanModem.gz
chmod 777 scanModem
sudo ./scanModem


tar zxf SLMODEMD.gcc4.1.tar.gz

cd SLMODEMD.gcc4.1
sudo chmod a+x slmodemd
sudo cp slmodemd /usr/sbin

Note:
find /usr -name slmodemd
should ONLY report the newly copied slmodemd  
Should another older slmodemd copy be found rename it slmodem.old

Locate the ALSA Modem driver from the choices below:
Compatible primary modem controllers currently are :
      PCI  ID       modem controller  name/source     low_level_driver
    =======        ===============    =======         =================       
    1002:434d          ATI                            snd-atiixp-modem
    1002:4379          ATI                                 "
    1106:3068          VIA                            snd-via82xx-modem
    10b9:5451          ALI 5451 audio with modem      snd-ali5451
    8086:????           many Intel controllers        snd-intel8x0m
    10de:00d9          Nvidia Corp                          "
    1039:7013          SIS 630                              "
     Others?                                                "
Under each of these controllers, may different Subsystems can be hosted, 
and having a variety of modem codecs, with most meeting a mc97 standard.  
All are potentially supported by slmodemd with one exceptional family.

First insert an ALSA modem driver. (Format:# modprobe low_level_driver)

sudo modprobe snd-hda-intel



4. ##Open Terminal Window and started slmodemd

larry@LK-MT6840:~$ sudo slmodemd -c USA --alsa hw:0,6
[sudo] password for larry:
SmartLink Soft Modem: version 2.9.11 Feb 17 2008 09:31:10
symbolic link `/dev/ttySL0' -> `/dev/pts/1' created.
modem `hw:0,6' created. TTY is `/dev/pts/1'
Use `/dev/ttySL0' as modem device, Ctrl+C for termination.


5. Test wvdial
larry@LK-MT6840:~$ sudo wvdialconf wvtest
Editing `wvtest'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttySL0<*1>: ATQ0 V1 E1 -- OK
ttySL0<*1>: ATQ0 V1 E1 Z -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttySL0<*1>: Modem Identifier: ATI -- SmartLink Soft Modem
ttySL0<*1>: Speed 4800: AT -- OK
ttySL0<*1>: Speed 9600: AT -- OK
ttySL0<*1>: Speed 19200: AT -- OK
ttySL0<*1>: Speed 38400: AT -- OK
ttySL0<*1>: Speed 57600: AT -- OK
ttySL0<*1>: Speed 115200: AT -- OK
ttySL0<*1>: Speed 230400: AT -- OK
ttySL0<*1>: Speed 460800: AT -- OK
ttySL0<*1>: Max speed is 460800; that should be safe.
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttySL0.
wvtest<Warn>: Can't open 'wvtest' for reading: No such file or directory
wvtest<Warn>: ...starting with blank configuration.
Modem configuration written to wvtest.
ttySL0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"



6. ##let it run while I configure wvdial in another Terminal window.

##Wvdial.conf follows:

[Dialer defaults]
# Lines begining with # are comments.
# wvdial will look for this file at  /etc/wvdial.conf  or  /home/LoginName/.wvdial.rc
#
# Redhat/Fedora have an  Internet Connection Wizard in the popup menus 
# ICW will write a two part  /etc/wvdial.conf supporting multiple modem usage.
#
#Modem = ModemPort
# typically a symbolic link to the true port is used, /dev/modem or /dev/ttyS*
# wvdialconf will test all port names /dev/modem and /dev/ttyS*
Modem = /dev/ttySL0

Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C0 &D2 +FCLASS=0
#  Changed &C1 to &C0 to not use Carrier Detect
#  Lack of dialtone acquisition can be due to low line voltage,
#    a common problem in Italy.
#  Try inserting a "dial without waiting": X3
#  Init2 = ATQ0 V1 E1 S0=0 X3 &C1 &D2 +FCLASS=0
#  In case of connection instabilities, specify a lower frequency:
#  Init2 = ATQ0 V1 E1 S0=0 X3 &C1 &D2  +MS=34
#  a MS=90 option is sometimes necessary for Internet Providers with buggy V92 protocols:
#  Init2 = ATQ0 V1 E1 S0=0 X3 &C1 &D2  +MS=90
ISDN = 0
Modem Type = Analog Modem
#Dial Command = ATDP
## replaces Touch Tone prefix ATDT to Dialout_phone_number, with older Pulse prefix ATDP
Baud = 115200
Phone =  8374162
# if going through a switch board, a perhaps necessary pause can produced with a comma:
# Phone = 1,Dialout_phone_number 
Username = [email]mylogin@copper.net[/email]
# if Internet Provider is MSN.net, use under Linux:   MSN/LoginName
Password = mypassword

# the following lines is NEEDED only for usage with slmodemd or martian_helper

Carrier check = no

# Kinternet appears to add it automatically.

## If CONNECT is achieved but browsing fails, try activating the following line

Auto DNS = yes

##    To make a logfile wvdial.out
#  wvdial 2>&1 | tee wvdial.out
# #  For some Internet providers, the following line is necessary 

Stupid Mode = yes

##  for other wvdial  options, do "man wvdial" or see the documentation in
##    /usr/share/doc/wvdial/

# to dial an alternate provide use "wvdial 2nd" which will preferentially read:
# [Dialer 2nd]
# Phone =  2nd_phone_number
# Username = 2nd_LoginName
# Password = 2nd_PassWord

## End wvdial config file


7. #Open a Terminal window and configure ppp, then SAVE the file and EXIT:
 sudo pppconfig
 
8. Verify PPP & wvdial files are correct for:

/etc/passwd
/etc/chap-secrets
/etc/pap-secrets
/etc/ppp/peers/provider
/ect/wvdial.conf

9. Dial out with wvdial
#Open Terminal Window and start Wvdial

larry@LK-MT6840:/etc$ sudo wvdial --config /etc/wvdial.conf
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C0 &D2 +FCLASS=0
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C0 &D2 +FCLASS=0
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT8374162
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT8374162
WvDial<Warn>: Timed out while dialing.  Trying again.
WvDial<*1>: Sending: ATDT8374162
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: NO CARRIER
WvDial Modem<*1>: ATDT8374162
WvDial<Warn>: No Carrier!  Trying again.
WvDial<*1>: Sending: ATDT8374162
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: NO CARRIER
WvDial Modem<*1>: ATDT8374162
WvDial<Warn>: No Carrier!  Trying again.


I have tried Dialing out with PPP and also WVDIAL and both have the same problem
of not detecting a Carrier.  Both programs never detect the Carrier.

Modem will go OFFHOOK, Dial out using TONE, and never detect a Carrier even though
[www.copper.net](www.copper.net) is transmitting.  System works fine with Win XP and same
modem and XP Drivers.  What am I missing?

Thanks

LK

---

### Post by linfidel on 2008-04-20
I'm just using old knowledge about modems from the old days - I have no idea what the first 95% of your post means. :)

But, it looks like it's talking to the modem; the modem responds to AT... commands with OK, which it's doing.

Then, there's the dialing, ATDT8374162 (AT is the command prefix, DT means dial tone).

It is dialing 8374162, and never getting an answer.  So, there's two things that may be happening:
1.  There is no answer.  Try dialing 8374162 and see if you get a loud modem tone.
if so,
2.  The modem may not be connected to the telephone line correctly. There are probably two connectors, one for the wall (that's the one to use) and one for a phone.  So,
    a.  Connect a phone to the 2nd jack, and see if it works.
    b.  When the modem tries to dial, listen on an extension, and see if it breaks the dial tone, and you should hear the dialing beeps.

Hope this helps.

---

### Post by lkraemer on 2008-04-21
Thanks linfidel,
But, as I stated:
Modem will go OFFHOOK, Dial out using TONE, and never detect a Carrier even though [www.copper.net](www.copper.net) is transmitting.  I have used a second phone to hear the Modem DIAL, [www.Copper.Net's](www.Copper.Net's) Modem ANSWER,
(meaning transmitting tones) and then wvdial for some reason never
CONNECTS.  PPP does the exact same thing.

LK

---

### Post by _duncan_ on 2008-04-21
1. There seems to be an inconsistency in the process. The command
```
sudo wvdialconf wvtest
```will write the configuration into the file wvtest, not /etc/wvdial.conf.


2. However, when dialing out using the command
```
sudo wvdial --config /etc/wvdial.conf
```
you are basically telling wvdial to use /etc/wvdial.conf instead of wvtest.


Can you repeat the process, but this time instead of the first command, try using
```
sudo wvdialconf /etc/wvdial.conf
```


I scrutinized the config file you posted. Everything seems to be in order. Is that from /etc/wvdial.conf or wvtest?

---

### Post by lkraemer on 2008-04-21
_duncan_
Here is the information in /home/larry/wvtest

[Dialer Defaults]
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
; Phone = <Target Phone Number>
ISDN = 0
; Username = <Your Login Name>
Init1 = ATZ
; Password = <Your Password>
Modem = /dev/ttySL0
Baud = 460800


The same information is in my /etc/wvdial.conf file.
I have also checked the file /home/larry/.wvdial.conf
and tried to use it for dialing out.

Still the same results.  NO CONNECT  because of NO CARRIER detected.

I have used:
ifconfig to see if eth0 is enabled then

turned off eth0 with:

ifconfig eth0 down

Still no connect.

LK

---

### Post by _duncan_ on 2008-04-21
Just make sure the config file you are using to dial out contains the following:
```
Carrier Check = off
Stupid Mode = on

```

This is important for modems with smartlink chipsets.

---

### Post by Mark_in_Hollywood on 2008-04-21
I hate to ask this, but please check the modem in another slot of it's current motherboard's place and if that doesn't work, check the modem in another computer.

---

### Post by lkraemer on 2008-04-23
Well, the folks at [www.linmodems.org](www.linmodems.org) have given me enough
information to know it is a problem with the Alsa Drivers
(1.0.14 vs 1.0.16) and Ubuntu Ver 7.10.  So, the next
logical step is to go to Ubuntu 8.04 if they get the
proper information to verify that this Modem will work
properly in the latest version.

WHEW!!!!!  What a deal!

I just didn't want to disassemble my new Gateway MT6840 laptop
to see if there was another slot for this modem....

LK

---

### Post by _duncan_ on 2008-04-24
I'm sorry to hear that.

Ubuntu Hardy 8.04 will be out today. From what I read in the dev mailing list past few months, there will be better support for ALSA-based modems with the new version. I hope it works out for you.

Otherwise, you may have to consider buying one of those external USB hardware modems. My info isn't up-to-date, but you probably have to shell out 50 to 80 US$ if you go this route.

---


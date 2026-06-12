---
title: "US, Ubuntu 7.04 kernel 2.6.20-15-generic"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by zaryk on 2007-08-31
can anyone help me?  I have a toshiba satellite a105-s4284.



--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007
 scanModem update of:  2007_August_28


 There are no blacklisted modem drivers in /etc/modprobe*  files 
USB modem not detected by lsusb


Several modems are supported by drivers with ALSA, the Advanced Linux Sound Architecture software.
Copying ALSA diagnostics to Modem/ALSAubuntu.tgz
ALSAversion = 1.0.13

Modem or candidate host audio card have firmware information and diagnostics:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1b.0	8086:27d8	1179:ff10	Audio device: Intel Corporation 82801G 

 Modem interrupt assignment and sharing: 
 22:       2728          0   IO-APIC-fasteoi   HDA Intel
 --- Bootup diagnostics for card in PCI slot 00:1b.0 ----
[   84.608000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   84.608000] PCI: Setting latency timer of device 0000:00:1b.0 to 64

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

8086:27d8 is a High Definition Audio card, possibly hosting a soft modem.
Bootup diagnostics lack ALSA data.

 The HDA modem codec file is: /proc/asound/card0/codec#1
-----------------------------------
Codec: Generic 11c1 Si3054
Address: 1
Vendor Id: 0x11c13026
Subsystem Id: 0x11790001
Revision Id: 0x100700

 The audio card hosts a softmodem chip with Vendor ID:  0x11c13026

 For candidate modem in PCI bus:  00:1b.0
   Class 0403: 8086:27d8 Audio device: Intel Corporation 82801G
      Primary PCI_id  8086:27d8
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

 Already loaded into the kernel is snd-hda-intel and audio drivers it depends on,
 displayed by:	lsmod | grep snd_hda_intel
Module                  Size  Used by
-------------------------------------
snd_hda_intel          21912  1 
snd_hda_codec         205440  1 snd_hda_intel
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm


The diagnostic outputs for this softmodem section have their raw information in
folders and text files under /proc/asound/ which you can browse. The information
is from files:
	/proc/asound/pcm
-------------------------------
00-06: Si3054 Modem : Si3054 Modem : playback 1 : capture 1
00-00: ALC861 Analog : ALC861 Analog : playback 1 : capture 2

	/proc/asound/modules
-------------------------------
 0 snd_hda_intel
	11c13026
-------------------------------

-------------------------------
Current support status of HDA cards is:
  Vendor IDs  Chip maker     Support type 
  ----------  ----------    -------------
  0x14f12bfa  Conexant      hsfmodem , not slmodemd compatible
  0x14f12c06  Conexant      hsfmodem , not slmodemd compatible
  0x11c13026  AgereSystems  snd-hda-intel, slmodemd supported
  0x11c11040  AgereSystems      "             "     support not yet available.
  0x11c13055  AgereSystems      "             "    ,      "
  0x163c3055  Smartlink         "             "    ,      "
  0x163c3155    "               "             "    ,      "
  0x10573055  Motorola          "             "    ,      "
  0x10573155     "              "             "    ,      ""
as of October 2006.

	/proc/asound/card0/codec#1
-------------------------------


and from the command:
	aplay -l | grep -i modem
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]

----------------end Softmodem section --------------

Writing Intel.txt
Writing Smartlink.txt
============ end Smartlink section =====================

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.1.2
             and the compiler used in kernel assembly: 4.1.2


 
 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.1
   linuc_headers base folder /lib/modules/2.6.20-15-generic/build

 However some compilations and executable functions may need additional files,
 in the FileNames.h (so called kernel "h"eaders) collection installed in  /usr/include/ .
 For martian_modem, additional required packages are libc6-dev (and for Debian/Ubuntu,  linux-libc-dev). The also required headers of package libc6 are commonly installed by default. 



If a driver compilation files with message including some lack of some FileName.h (stdio.h for example. 
Some additional kernel-header files need installation to /usr/include.
For Debian/Ubuntu related distributions, run the following command to display the needed package list:
$ sudo apt-get -s install linux-kernel-devel
While some of the files may be on the install CD, others may have to be found through [http://packages.ubuntu.com](http://packages.ubuntu.com)

For Ubuntu Feisty, additional packages required were:
 libc6-dev linux-libc-dev
available through [http://packages.ubuntu.com/](http://packages.ubuntu.com/) , if not on the install CD.
Such packages may have different names for other Linux distributions.
Try installing just the libc6-dev, then test the compile again.


Checking pppd properties:
	-rwsr-xr-- 1 root dip 269224 2007-04-05 03:41 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    [http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html](http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html)

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

Read Modem/YourSystem.txt concerning other COMM channels: eth0 eth1
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

---

### Post by louieb on 2007-08-31
No help here, but I'll give you a bump. Now what is the problem/question? :confused: Really can't tell  what it is from your post. At least you shown you have done some research  and tried to solve what ever it is.

---

### Post by zaryk on 2007-08-31
Im trying to get dial-up running on it.  I take my laptop everywhere, and in most cases im using wireless but there are some places I need the dial-up.  I went to linmodems website and got scanmodem.gz, where i proceeded to scan linux and got the info above.  Afterwards i got lost and was hoping someone could figure out what I needed by looking at the information.

---


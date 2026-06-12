---
title: "scanModem (modem problems)"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by rameez on 2006-04-15
Hi,
I have a Toshiba Saatellite A25, I am trying to install the modem on it, I tried the wiki [https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto) but have gotten stuck.
I have succesfully scanned the modem, downloaded the sldmodem
and installed it then I got this:
```
root@NoteBook:~/Desktop/SLMODEMD.gcc3# sudo modprobe snd-ali5451
root@NoteBook:~/Desktop/SLMODEMD.gcc3# sudo slmodemd --alsa -c USA -s hw:0,1
Usage: slmodemd [option...] <device>
Where 'device' is name of modem device (default `/dev/slamr0')
  and 'option' may be:
  -h, --help            this usage
  -u, --usage           this usage
  -v, --version         show version and exit
  -c, --country=VAL     default modem country name (default `USA')
      --countrylist     show list of supported countries
  -a, --alsa            ALSA mode (see README for howto)
  -g, --group=VAL       Modem TTY group (default `dialout')
  -p, --perm=VAL        Modem TTY permission (default `0660')
  -n, --nortpriority    run with regular priority
  -d, --debug=VAL       debug level (default `0')
  -l, --log=VAL         logging mode (default `5')

```
I dont know what am I doing wrong, where should I go from here?

Here is my modemdata.txt
```


 DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 5.10 "Breezy Badger"  kernel 2.6.12-10-386  
 Occassionally reponses are blocked by an Internet Provider mail filters.
 So do in a day also check the Archived responses at DISCUSS@linmodems.org
Code updated on:  2006_April_07
------------ --------------  System information ------------------------
 Ubuntu 5.10 "Breezy Badger" 
 on System with processor: i686
 currently under kernel:   2.6.12-10-386

 https://wiki.ubuntu.com/DialupModemHowto has good general guidance.
 Be sure to read the Ethernet section of Modem/YourSystem.txt 
A /dev/modem symbolic link is not present
 USB modem not detected.

 Checking for audio card 
0000:00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
	Reading /proc/asound/pcm 
00-00: ALI 5451 : ALI 5451 : playback 32 : capture 1
00-01: ALI 5451 modem : ALI 5451 modem : playback 1 : capture 1

The modem is supported by an ALSA modem driver plus slmodemd, OR alternatively
an hsfmodem package from http://www.linuxant.com/drivers. Further diagnostics
below may resolve between the two.
ALSA modem drivers are included in 2.6.n kernel packages and currently include:
	snd-hda-intel, a joint audio + modem driver
	snd-ali5451  ,        "             "
	intel8x0m        , depending on intel8x0    audio driver
	snd_via82xx_modem,          "   snd_via82xx   "
	snd-atiixp-modem ,          "   snd-atiixp    "
Driver loading itself does NOT resolve between ALSA and hsfmodem alternatives. 

 The potentially supporting drivers now loaded on this System are:
0 snd_ali5451


 The kernel was assembled with compiler:  3.4.5
 with current System compiler GCC=4.0.2
-------------
 Found make utility.
-------------
Checking for kernel-headers needed for compiling.
 Kernel-header resources needed for compiling are not manifestly ready!

Modem candidates are at PCI_buses:  0000:00:06.0
0000:00:09.0
    
Providing detail for device at  0000:00:06.0
  with vendor-ID:device-ID
	    ----:----
Class 0401: 10b9:5451   Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
  SubSystem 1179:0221  Toshiba America Info Systems: Unknown device 0221
	Flags: bus master, medium devsel, latency 64, IRQ 11
 Checking for IRQ 11 sharing with modem.
      XT-PIC  ohci_hcd:usb1, ohci_hcd:usb2, ehci_hcd:usb3, ALI 5451, yenta, yenta, eth0, 0.0, serial

  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 10b9:5451 1179:0221 debian_version 2.6.12-10-386  3.4.5 4.0.2    i686
The audio card 10b9:5451 may carry a soft modem chip.
-------------------------------
The modem should be setup by:
     sudo slmodemd --alsa -c YOUR_COUNTRY 
Get the SLMODEMD.gcc3 from http://linmodems.technion.ac.il/packages/smartlink/
and follow guidance therein.
	The soft modem in the 8086:2668 High Definition Audio has low level support by 
the snd-hda-intel driver, beginning with the 2.6.14 kernels.  
        The Conexant soft modem chipset is not supported by snd-hda-intel and
http://www.Linuxant.com is developing support for these modems.

 For snd-ali5451.ko compiling instructions, see http://phep2.technion.ac.il/linmodems/archive/msg04955.html.
Modem support within the snd-ali5451 driver is included in some 2.6.12 and later kernels
              From records, 1179:0221 has soft modem codec type SIL21
The following two Root commands should set up the modem.
	sudo modprobe snd-ali5451
	sudo slmodemd --alsa -c YOUR_COUNTRY -s hw:0,1
Get the SLMODEMD.gcc3.tar.gz from http://linmodems.technion.ac.il/packages/smartlink/
       
 The controller: 10b9:5451  ALI 5451 
 is capable of supporting soft modem chips from AT LEAST manufacturers:
	AgereSystems
	Conexant
	Smartlink
 The Subsystem PCI id does not itself identify the modem Codec.
Checking for autoloaded ALSA modem drivers
snd_atiixp_modem       15396  0 
snd_ac97_codec         72188  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ali5451
snd_pcm                78344  7 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10120  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_pcm
snd                    48644  16 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_via82xx_modem      14500  0 
snd_ac97_codec         72188  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ali5451
snd_pcm                78344  7 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10120  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_pcm
snd                    48644  16 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_intel8x0m          16836  0 
snd_ac97_codec         72188  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ali5451
snd_pcm                78344  7 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10120  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_pcm
snd                    48644  16 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_ali5451            22596  2 
snd_ac97_codec         72188  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ali5451
snd_pcm                78344  7 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd                    48644  16 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

  Driver snd-ali5451  may enable codec acquisition 
  === Begin mc97 codec query  ===
	   
 Files under /proc/asound/ do not include  modem codec information. 
 If more decisive information is not given below,
 this is a tentative signature of a Conexant hsfmodem.  Download a hsfmodem package from
 http://www.linuxant.com/drivers or your installation CDs.  For SuSE/Novell, install both
 km_hsfmodem and hsfmodem packages,  for drivers and configuration tools respectively.
 
  === End mc97 codec query  ===

 Beginning check for older ac97_codec modems.
 An older ac97_modem codec was not detected.

 The Subsystem has a PCTel codec SIL21

 The modem can be set up by Root commands:
   sudo modprobe snd-ali5451
   sudo slmodemd --alsa -c YOUR_COUNTRY -s hw:0,1
 
 The ALSA modem driver snd-ali5451 provides low level hardware access.
 The slmodemd provides high level functions and is  not kernel-version specific.
 From http://linmodems.technion.ac.il/packages/smartlink/   follow the link 
 SLMODEMD.gcc3.tar.gz 
 Also download the ungrad-winmodem.tar.gz and the http://linmodems.technion.ac.il/packages/unloading.gz
 Within the SLMODEMD package the 1st_Read.txt gives instructions 
 For guidance on bootup automation see:
   http://linmodems.technion.ac.il/archive-fifth/msg04652.html
 
	Read Modem/Slmodem.txt instruction for doing the slamr diagnostic.
 == Checking PCI IDs through modem chip suppliers ==

 SmartLink at http://www.smlink.com/ owns vendor IDs 163c, 2000, 2003, and 2004
 The official download site is:  http://www.smlink.com/main/index1.php?ln=en&main_id=40
 But a more recent code and a much broader license for other chipset support,
 can be downloaded from http://linmodems.technion.ac.il/packages/smartlink/  
 Though not always needed, download the files: 
   slmodem-CurrentVersion.tar.gz - provides the most general code package.
   SLMODEMD.gcc3 - provides a compiled slmodemd 
   ungrab-winmodem.tar.gz  -  may be needed for usage with slamr. 
 Details on their usage are in Slmodem.txt, Slmodem-ALSA.txt and
 http://linmodems.technion.ac.il/slmodem-serial.html

 == Checking PCI IDs through modem chip suppliers ==

 Vendor 10b9 is Acer Labs, producing highly integrated motherboards and Ali components.
 The tight integration unfortunately ofter blocks identification of the modem chipset.
 Desired information may be gained by using a COMM console under MS Windows,
   and using ATI commands to elicit chipset and driver information.
 10b9:5450  ALI 5450 and  10b9:5451  ALI 5451 are controllers for unsupported "sound  modems"
 

    
Providing detail for device at  0000:00:09.0
  with vendor-ID:device-ID
	    ----:----
Class 0703: 10b9:5457   Modem: ALi Corporation M5457 AC'97 Modem Controller (prog-if 00 [Generic])
  SubSystem 1179:0001  Toshiba America Info Systems: Unknown device 0001
	Flags: medium devsel, IRQ 11
 Checking for IRQ 11 sharing with modem.
      XT-PIC  ohci_hcd:usb1, ohci_hcd:usb2, ehci_hcd:usb3, ALI 5451, yenta, yenta, eth0, 0.0, serial

  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 10b9:5457 1179:0001 debian_version 2.6.12-10-386  3.4.5 4.0.2    i686
              From records, 1179:0001 has soft modem codec type SIL27
The following two Root commands should set up the modem.
	sudo modprobe snd-intel8x0m
	sudo slmodemd --alsa -c YOUR_COUNTRY modem:1
Get the SLMODEMD.gcc3.tar.gz from http://linmodems.technion.ac.il/packages/smartlink/
       
 The controller: 10b9:5457  ALI 5457 AC-Link 
 is capable of supporting soft modem chips from AT LEAST manufacturers:
	Pctel
	Conexant
	Intel
	Smartlink
 The Subsystem PCI id does not itself identify the modem Codec.
Checking for autoloaded ALSA modem drivers
snd_atiixp_modem       15396  0 
snd_ac97_codec         72188  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ali5451
snd_pcm                78344  6 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10120  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_pcm
snd                    48644  15 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_via82xx_modem      14500  0 
snd_ac97_codec         72188  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ali5451
snd_pcm                78344  6 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10120  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_pcm
snd                    48644  15 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_intel8x0m          16836  0 
snd_ac97_codec         72188  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ali5451
snd_pcm                78344  6 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10120  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_pcm
snd                    48644  15 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_ali5451            22596  1 
snd_ac97_codec         72188  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ali5451
snd_pcm                78344  6 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd                    48644  15 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

  Driver snd-intel8x0m  may enable codec acquisition 
  === Begin mc97 codec query  ===
	   
 Files under /proc/asound/ do not include  modem codec information. 
 If more decisive information is not given below,
 this is a tentative signature of a Conexant hsfmodem.  Download a hsfmodem package from
 http://www.linuxant.com/drivers or your installation CDs.  For SuSE/Novell, install both
 km_hsfmodem and hsfmodem packages,  for drivers and configuration tools respectively.
 
  === End mc97 codec query  ===

 Beginning check for older ac97_codec modems.
 An older ac97_modem codec was not detected.

 DisAgreement between diagostic and Archive data.  Using diagnostic: CODEC=SIL21
 The Subsystem has a PCTel codec SIL21

 The modem can be set up by Root commands:
   sudo modprobe snd-intel8x0m
   sudo slmodemd --alsa -c YOUR_COUNTRY modem:1
 
 The ALSA modem driver snd-intel8x0m provides low level hardware access.
 The slmodemd provides high level functions and is  not kernel-version specific.
 From http://linmodems.technion.ac.il/packages/smartlink/   follow the link 
 SLMODEMD.gcc3.tar.gz 
 Also download the ungrad-winmodem.tar.gz and the http://linmodems.technion.ac.il/packages/unloading.gz
 Within the SLMODEMD package the 1st_Read.txt gives instructions 
 For guidance on bootup automation see:
   http://linmodems.technion.ac.il/archive-fifth/msg04652.html
 
	Read Modem/Slmodem.txt instruction for doing the slamr diagnostic.
 == Checking PCI IDs through modem chip suppliers ==
 == Checking PCI IDs through modem chip suppliers ==

 Vendor 10b9 is Acer Labs, producing highly integrated motherboards and Ali components.
 The tight integration unfortunately ofter blocks identification of the modem chipset.
 Desired information may be gained by using a COMM console under MS Windows,
   and using ATI commands to elicit chipset and driver information.
 10b9:5450  ALI 5450 and  10b9:5451  ALI 5451 are controllers for unsupported "sound  modems"
 

 These messages may aid setup of soft modems under 10b9:M5457 controllers:
   http://linmodems.technion.ac.il/archive-third/msg02518.html
   http://linmodems.technion.ac.il/archive-third/msg02100.html
 The slmodem-2.9.9 support was developed for 10b9:5459,
   but there a range of reports the related 10b9:5457 modemd controllers:
     fully functional;
     functional only after a power on reboot from Microsoft windows;
     hang/crash upon initiation of modem usage.
 
 10b9:5457   Modem: ALi Corporation [M5457 AC-Link Modem] 
 SubSystem 1179:0001   Toshiba America Info Systems: Unknown device 0001
 has an AgereSoftModem chip which may be supported by the Smartlink slmodem-2.9.9 driver 
     

  ======= PCI_ID checking completed ====== 
 Update=2006_April_07

Analyzing information for PCMCIA device at PCI Bus 00:10.0
0000:00:10.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
	Subsystem: Lucent Technologies: Unknown device ab01
	Flags: bus master, medium devsel, latency 168, IRQ 11
GREPping for an inserted PCMCIA modem with filter:        ommunication

Analyzing information for PCMCIA device at PCI Bus 00:11.0
0000:00:11.0 CardBus bridge: Toshiba America Info Systems ToPIC95 PCI to Cardbus Bridge with ZV Support (rev 33)
	Subsystem: Toshiba America Info Systems: Unknown device 0001
	Flags: bus master, slow devsel, latency 168, IRQ 11
GREPping for an inserted PCMCIA modem with filter:        ommunication
 If a PCMCIA modem is currently inserted and the sockets activated by
    /etc/init.d/pcmcia start
 then the PCMCIA bridge is NOT transparent.

 If the modem is known to have a Lucent digital signal processing chipset,
 then PCMCIA.tar.gz variant assembled by Joern Wustenfeld is necessary,
 rather than the standard ltmodem-8.31b1.tar.gz at  http://ltmodem.heby.de/
drwxr-xr-x  2 root root 0 2006-04-16 01:38 /dev/.udevdb

There is an active UDEV file system, creating device nodes in volatile RAM.
For SmartLink modems using the slamr.ko or slusb.ko drivers an /etc/init.d/ script
will be necessary to create /dev/slamr0 or /dev/slusb0 ports, or manually by:
#  mknod -m 600 /dev/slamr0 c 242 0
#  mknod -m 600 /dev/slusb0 c 243 0
upon each bootup.

For information on modem port creation under the UDEV device file system see:
   http://linmodems.technion.ac.il/archive-fourth/msg03299.html  for Conexnant modems
   http://linmodems.technion.ac.il/archive-fifth/msg01177.html  for Lucent/Agere DSP modems
   
 Checking for modem symbolic link support lines within /etc/udev/ files


Checking the /etc/apt/sources.list
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

deb-src http://archive.ubuntu.com/ubuntu breezy universe


deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse

deb http://wine.sourceforge.net/apt/ binary/

deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

deb http://deb.opera.com/opera/ etch non-free


deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://koti.mbnet.fi/~ots/ubuntu/ breezy/
deb-src http://koti.mbnet.fi/~ots/ubuntu/ breezy/

deb http://theli.free.fr/packages/breezy/ ./

A package kernel-kbuild-2.6-3 or later version must be installed to support compiling


    /usr/bin/gcc -> gcc-4.0
      
 The Major.Minor versions differ in the designated compiler 4.0.2 and the 3.4.5 used in kernel assembly!!"
But there must be a match on the target for driver installation, 
of gcc Major.Minor versions or kernel and drivers!!
Otherwise the drivers will fail to load with warning:
  Invalid module format!!"
See http://linmodems.technion.ac.il/archive-fifth/msg04252.html 
 
Kernel-header resources needed for compiling are not manifestly ready!
Checking /usr/src/ for compressed compressed headers or kernel-source

Kernel-header resources needed for compiling are not manifestly ready!
If compressed resources are present, expand and then configure them following DriverCompiling.txt
They may have to be installed.
Within your Linux distributions' installation CD or online resource (and mirrows), search for :
  Distribution  PackageName			OnLine
  ----------------------------------------------------------------------
 Debian  		kernel-headers-2.6.12-10-386    	http://www.debian.org/distrib/packages or install CD
 Ubuntu 		linux-headers-2.6.12-10-386		http://http://packages.ubuntu.com/ or install CD
 Xandros
                        kernel-kbuild-3.6 are additionally required by  Debian, Ubuntu and Xandros
 Mandrake 	kernel-source-2.6.12-10-386	   If not present on install CDs search
 	http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/RPMS/ 
	http://rpms.mandrakeclub.com/rpms/mandrake/official/LByName.html, or other mirrors.
  SuSE		kernel-source-2.6.12-10-386		 , kernels are named k_deflt
  FedoraCore4  kernel-devel-2.6.12-10-386 or kernel-smp-devel-2.6.12-10-386 on install CD1 or CD4
One of which must be installed if compiling drivers to match kernel 2.6.12-10-386 proves necessary.
Within the output Modem/ folder, read CompilingDrivers.txt for details.
   

 A /dev/modem symbolic link is not set.

The following information blocks just query some ppp support items.

====================================================
   grep -rs ppp /etc/modprobe.*
-------------------------------------
/etc/modprobe.d/aliases:alias net-pf-24 pppoe
/etc/modprobe.d/aliases:alias ppp-compress-18 ppp_mppe_mppc
-------------------------------------
 Resident PPP support modules are properly uncompressed .
----active COMM services are ------------
eth0      Link encap:Ethernet  HWaddr 00:08:0D:DF:CF:52  
          inet6 addr: fe80::208:dff:fedf:cf52/64 Scope:Link
This COMM mode should be closed before using the modem, or DNS services may fail.
Be sure to read the section about ppp related modules and aliases in Modem/YourSystem.txt
 ---- dmesg queries -------

  pppd version 2.4.2 may not be fully compatible with 2.6.8 kernel releases.
  If an initial CONNECT is achieved without PPP being subsequently established,
  drop back to a 2.4.1 version.  This has worked for PCTEL AMR modem users,
  supported by the http://www.smlink.com  slmodem software.
  Check pppd version with:
    pppd --version
  See  http://linmodems.technion.ac.il/archive-fourth/msg03167.html
    
  debian_version is not yet providing pre-compiled drivers for WinModems


```

---

### Post by towsonu2003 on 2006-04-15
ok, here is the instructions (different from those available in the second link in my signature. if these do not work, try the instructions in there, in the section slmodem):

1: download and put this file to your desktop: [http://linmodems.technion.ac.il/packages/smartlink/slmodemd-2.9.9e-pre1-alsa.tar.gz](http://linmodems.technion.ac.il/packages/smartlink/slmodemd-2.9.9e-pre1-alsa.tar.gz) this is the precompiled alsa-supported slmodem deamon. 

2: make sure the snd-ali5451 is loaded:
```
lsmod | grep snd-ali5451
```
if there is no output, do ```
sudo modprobe snd-ali5451
```

if in the next reboot this gives you output ```
lsmod | grep snd-ali5451
``` then you do NOT need to do this ```
sudo modprobe snd-ali5451
``` everytime you start the slmodem deamon (below). 

3: now that the module is in place, navigate to your desktop, untar file, navigate to untarred directory, start slmodem deamon:
```
cd ~/Desktop
tar xvzf slmodemd-2.9.9e-pre1-alsa.tar.gz
cd SLMODEMD
sudo ./slmodemd -a -c USA OPTION
```

The weird part:
Instead of OPTION, use one of these (by trial and error, you'll find out which one you should be using). Try them by the order given below:
hw:1
modem:0
modem:1
hw:0

for example: 
sudo ./slmodemd -a -c USA modem:1
do NOT close that terminal!

after this, go to the second link in my signature, read (fully) the section about wvdial, configure and dial with **wvdial** in a new terminal. When configured though, add the following lines at the end of **/etc/wvdial.conf**:
```

Carrier Check = no
Stupid Mode = yes

```Now, you may be unable to connect on first try. Try and try again. I usually connect between 2 and 20 minutes. If not working, kill wvdial (ctrl + c), kill slmodem deamon (sudo killall slmodemd), and go back to another option for starting the deamon (sudo ./slmodemd bla in directory ~/Desktop/SLMODEMD/). 

If you get connected, copy the slmodem deamon file to /usr/bin and activate it next time you reboot (or kill deamon)
```

sudo cp ~/Desktop/SLMODEM/slmodemd  /usr/bin
sudo slmodemd -a -c USA OPTION

```

Any questions, errors, post here ;) good luck!

---

### Post by rameez on 2006-04-15
```
$ lsmod | grep ali
i2c_ali1535             6788  0
i2c_ali15x3             7172  0
i2c_core               19728  3 i2c_acpi_ec,i2c_ali1535,i2c_ali15x3
snd_ali5451            22596  2
snd_ac97_codec         72188  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ali5451
snd_pcm                78344  7 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ali5451,snd_ac97_codec,snd_pcm_oss
ali_agp                 6656  0
agpgart                32328  1 ali_agp
snd                    48644  16 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
alim15x3               11020  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,alim15x3

```

---

### Post by towsonu2003 on 2006-04-15
just posted the instructions (above)

according to this: 
[QUOTE=rameez]```
$ lsmod | grep ali
...
**snd_ali5451            22596  2**

```[/QUOTE]
the module snd_ali5451 is loaded. So you don't need to do sudo modprobe snd_ali5451. If this module is automatically loaded on boot (check with lsmod | grep ali right after reboot), than you won't need to do sudo modprobe snd_ali5451 ever again.

**edit:**
PS1. you'll get used to all this crap in a few days if this works...
PS2. just to remind, your first try with wvdial may not be a success (to connect, not to setup). if so, try again and again. I connect in 2 to 20 minutes, just luck...
PS3. do not close the terminals of slmodemd and wvdial (so when you get connected, you will have two terminals open, one ith slmodemd running, one with wvdial.

---

### Post by rameez on 2006-04-16
[SIZE="1"]I did everything per instructions, and it seems to load the modem but does not dial. here are the outputs:
```
$ sudo ./slmodemd -a -c USA hw:0
error: mixer setup: Off-hook switch not found for card hw:0
SmartLink Soft Modem: version 2.9.9e-pre1 Sep 24 2005 14:47:19
symbolic link `/dev/ttySL0' -> `/dev/pts/1' created.
modem `hw:0' created. TTY is `/dev/pts/1'
Use `/dev/ttySL0' as modem device, Ctrl+C for termination.
```

Here is what I get when I try 
```
sudo wvdial
--> WvDial: Internet dialer version 1.54.0
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT(Number of ISP)
--> Waiting for carrier.
ATDT(Number of ISP)
--> Timed out while dialing.  Trying again.
--> Sending: ATDT(Number of ISP)
--> Waiting for carrier.
--> Timed out while dialing.  Trying again.

```
This keeps on coming until I press Control + C[/SIZE]

---

### Post by towsonu2003 on 2006-04-16
kill slmodemd (ctrl +c in slmodemd's terminal) and try it with hw:1
if doesn't work, kill slmodemd and try with modem:0 and than modem:1

after trying each of the above options, you might need to reconfigure wvdial (don't forget to add the last two lines I mentioned before). 

Check your modem & phone cables. After wvdial dials and *is* waiting, you can pick up the phone and listen the modem communicating (scary robot-like sounds). 

Note: if you hear modem voices in the phone (dulululu bililili ululu etc ;) ) but wvdial craps out with "no carrier", kill wvdial (not slmodemd) and try again and again. As I said, for me, it takes 2 to 20 minutes to dial out. 

PS. ouch, my eyes...

---


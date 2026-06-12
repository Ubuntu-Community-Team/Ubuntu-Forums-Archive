---
title: "scanModem, Ubuntu 5.10 &quot;Breezy Badger&quot;  kernel 2.6.12-9-386"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by GeorgeAD on 2006-04-13
Is it possible to use this internal modem at all easily? Or is it hopeless and better to get an external one off ebay?  Any help greatly appreciated! Here's the scanmodem output:


 DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 5.10 "Breezy Badger"  kernel 2.6.12-9-386  
 Occassionally reponses are blocked by an Internet Provider mail filters.
 So do in a day also check the Archived responses at [email]DISCUSS@linmodems.org[/email]
Code updated on:  2006_April_07
------------ --------------  System information ------------------------
 Ubuntu 5.10 "Breezy Badger" 
 on System with processor: i686
 currently under kernel:   2.6.12-9-386

 [https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto) has good general guidance.
A /dev/modem symbolic link is not present
 USB modem not detected.

 Checking for audio card 
0000:00:0c.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 04)
	Reading /proc/asound/pcm 
00-00: ES1371/1 : ES1371 DAC2/ADC : playback 1 : capture 1
00-01: ES1371/2 : ES1371 DAC1 : playback 1
 The potentially supporting drivers now loaded on this System are:
0 snd_ens1371


 The kernel was assembled with compiler:  3.4.5
 a gcc-3.4.5  package must be installed to support driver compiling
To support compiling, get the  BreezyGCC_3.4_i386.tar.gz from [http://phep2.technion.ac.il/linmodems/packages/smartlink/](http://phep2.technion.ac.il/linmodems/packages/smartlink/) 
-------------
 Compiling utility   make   Not found.
-------------
Checking for kernel-headers needed for compiling.
 Kernel-header resources needed for compiling are not manifestly ready!

Modem candidates are at PCI_buses:  0000:00:0f.0
    
Providing detail for device at  0000:00:0f.0
  with vendor-ID:device-ID
	    ----:----
Class 0780: 125d:2898   Communication controller: ESS Technology ES2898 Modem (rev 03)
  SubSystem  
	Flags: fast devsel, IRQ 5
 Checking for IRQ 5 sharing with modem.
      XT-PIC  Ensoniq AudioPCI
      XT-PIC  ide1

  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 125d:2898  debian_version 2.6.12-9-386  3.4.5 none    i686
      
 Information on several modem chipset providers is provided below,
 because ambiguities remain on the correct choice of supporting software.
            
 == Checking PCI IDs through modem chip suppliers ==

 Vendor=125d is ESS Technologies, making devices:
 There has been no formal support for Linux since kernels 2.2.2
 There is no hope for support under 2.6.n kernels.
 See InfoGeneral.txt about alternatives.

 Only under 2.4.n Linux kernels and are there some kludges of fadding utility:
   [http://linmodems.technion.ac.il/archive-fourth/msg00317.html](http://linmodems.technion.ac.il/archive-fourth/msg00317.html)   (2004Feb08)
   [http://andrew.cait.org/ess/](http://andrew.cait.org/ess/)
   [http://sidlo.penguin.cz/ES2838/index_en.html](http://sidlo.penguin.cz/ES2838/index_en.html)
   [http://tx.technion.ac.il/~raindel/](http://tx.technion.ac.il/~raindel/)
   [http://phep2.technion.ac.il/linmodems/archive/msg04424.html](http://phep2.technion.ac.il/linmodems/archive/msg04424.html)


  ======= PCI_ID checking completed ====== 
 Update=2006_April_07
A PCMCIA CardBus is not detected on this System.
drwxr-xr-x  2 root root 0 2006-04-09 16:51 /dev/.udevdb

There is an active UDEV file system, creating device nodes in volatile RAM.
For SmartLink modems using the slamr.ko or slusb.ko drivers an /etc/init.d/ script
will be necessary to create /dev/slamr0 or /dev/slusb0 ports, or manually by:
#  mknod -m 600 /dev/slamr0 c 242 0
#  mknod -m 600 /dev/slusb0 c 243 0
upon each bootup.

For information on modem port creation under the UDEV device file system see:
   [http://linmodems.technion.ac.il/archive-fourth/msg03299.html](http://linmodems.technion.ac.il/archive-fourth/msg03299.html)  for Conexnant modems
   [http://linmodems.technion.ac.il/archive-fifth/msg01177.html](http://linmodems.technion.ac.il/archive-fifth/msg01177.html)  for Lucent/Agere DSP modems
   
 Checking for modem symbolic link support lines within /etc/udev/ files


Checking the /etc/apt/sources.list
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted



deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe main restricted multiverse



deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe main restricted multiverse

A package kernel-kbuild-2.6-3 or later version must be installed to support compiling


      
 The Major.Minor versions differ in the designated compiler none and the 3.4.5 used in kernel assembly!!"
But there must be a match on the target for driver installation, 
of gcc Major.Minor versions or kernel and drivers!!
Otherwise the drivers will fail to load with warning:
  Invalid module format!!"
See [http://linmodems.technion.ac.il/archive-fifth/msg04252.html](http://linmodems.technion.ac.il/archive-fifth/msg04252.html) 
 
Kernel-header resources needed for compiling are not manifestly ready!
Checking /usr/src/ for compressed compressed headers or kernel-source

Kernel-header resources needed for compiling are not manifestly ready!
If compressed resources are present, expand and then configure them following DriverCompiling.txt
They may have to be installed.
Within your Linux distributions' installation CD or online resource (and mirrows), search for :
  Distribution  PackageName			OnLine
  ----------------------------------------------------------------------
 Debian  		kernel-headers-2.6.12-9-386    	[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages) or install CD
 Ubuntu 		linux-headers-2.6.12-9-386		[http://http://packages.ubuntu.com/](http://http://packages.ubuntu.com/) or install CD
 Xandros
                        kernel-kbuild-3.6 are additionally required by  Debian, Ubuntu and Xandros
 Mandrake 	kernel-source-2.6.12-9-386	   If not present on install CDs search
 	[http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/RPMS/](http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/RPMS/) 
	[http://rpms.mandrakeclub.com/rpms/mandrake/official/LByName.html](http://rpms.mandrakeclub.com/rpms/mandrake/official/LByName.html), or other mirrors.
  SuSE		kernel-source-2.6.12-9-386		 , kernels are named k_deflt
  FedoraCore4  kernel-devel-2.6.12-9-386 or kernel-smp-devel-2.6.12-9-386 on install CD1 or CD4
One of which must be installed if compiling drivers to match kernel 2.6.12-9-386 proves necessary.
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
 COMM services are not active
Be sure to read the section about ppp related modules and aliases in Modem/YourSystem.txt
 ---- dmesg queries -------
[4294670.898000] audit: initializing netlink socket (disabled)
[4294718.006000] shpchp: acpi_shpchprm:\_SB_.NRTH evaluate _BBN fail=0x5
[4294718.006000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294733.267000] ibm_acpi: ec object not found
[4294752.480000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294752.480000] apm: overridden by ACPI.

  pppd version 2.4.2 may not be fully compatible with 2.6.8 kernel releases.
  If an initial CONNECT is achieved without PPP being subsequently established,
  drop back to a 2.4.1 version.  This has worked for PCTEL AMR modem users,
  supported by the [http://www.smlink.com](http://www.smlink.com)  slmodem software.
  Check pppd version with:
    pppd --version
  See  [http://linmodems.technion.ac.il/archive-fourth/msg03167.html](http://linmodems.technion.ac.il/archive-fourth/msg03167.html)
    
  debian_version is not yet providing pre-compiled drivers for WinModems

---

### Post by towsonu2003 on 2006-04-13
I hate the state of winmodems in Linux when I read output like that... From what it says, there is no hope if you want to use the current Ubuntu kernel (2.6.x). But if you are willing to compile a 2.4.x kernel, there may be some (little) hope. Here is the relevant info:
> == Checking PCI IDs through modem chip suppliers ==

Vendor=125d is ESS Technologies, making devices:
There has been no formal support for Linux since kernels 2.2.2
There is no hope for support under 2.6.n kernels.
See InfoGeneral.txt about alternatives.

Only under 2.4.n Linux kernels and are there some kludges of fadding utility:
[http://linmodems.technion.ac.il/arch.../msg00317.html](http://linmodems.technion.ac.il/arch.../msg00317.html) (2004Feb0
[http://andrew.cait.org/ess/](http://andrew.cait.org/ess/)
[http://sidlo.penguin.cz/ES2838/index_en.html](http://sidlo.penguin.cz/ES2838/index_en.html)
[http://tx.technion.ac.il/~raindel/](http://tx.technion.ac.il/~raindel/)
[http://phep2.technion.ac.il/linmodem.../msg04424.html](http://phep2.technion.ac.il/linmodem.../msg04424.html)

I would send an email to linmodems.org mailing list to see what they think. Don't forget about this part:
> 
DO use the following line as the **email Subject Line**, to alert cogent experts:
scanModem, Ubuntu 5.10 "Breezy Badger" kernel 2.6.12-9-386 

---

### Post by brentroos on 2006-04-13
*

---

### Post by NiTsi on 2006-04-13
I'm new to linux too but what i have been trying to do for 1 month (told you i'm new) is rather impossible if you have a modem by Conexant. I don't know what the scan modem says but conexant modems work with linuxant drivers which are sold!!! Secondly i tried the limited version and it hangs every 2-3 minutes. So you should check first of all if you have a conexant modem.....

---

### Post by GeorgeAD on 2006-04-14
Thanks everyone, that's what I wanted to know - I'll find an external one, not usb, serial like the older US Robotics ones? They seem easy to find.

---

### Post by az on 2006-04-14
[QUOTE=brentroos]You will need to compile the driver and a custom kernel, and unless you are familiar and comforatable doing this, I would not reccomend this.
.[/QUOTE]

Actually, there is no driver to compile.  This hardware is not supported by the manufacturer, nor have they released specs to allow anyone to write one.

---

### Post by az on 2006-04-14
[QUOTE=NiTsi]I'm new to linux too but what i have been trying to do for 1 month (told you i'm new) is rather impossible if you have a modem by Conexant. I don't know what the scan modem says but conexant modems work with linuxant drivers which are sold!!! Secondly i tried the limited version and it hangs every 2-3 minutes. So you should check first of all if you have a conexant modem.....[/QUOTE]
Conexant are only a small portion of all the software modems available.  Most software modems have linux support, but not generally in free-libre open source.

---

### Post by az on 2006-04-14
[QUOTE=GeorgeAD]Thanks everyone, that's what I wanted to know - I'll find an external one, not usb, serial like the older US Robotics ones? They seem easy to find.[/QUOTE]
USR hate linux.  They make some hardware modems which work fine, but they have always refulsed to support linux by providing drivers or specs for their software modems.  Just gbe sure you are not getting a US robotics PCi modem for windows.

In the early days, they even released an ISA hardware modem that checked to see if you had a windows "driver" and would not work otherwise.  That card had all the workings of a hardware modem, but was limited to use only with the proper software.

---

### Post by GeorgeAD on 2006-04-14
Thanks for letting me know. The reason I was think of usr was that there seem to be a lot of them around secondhand, and I was under the impression that as long as I got an external one it would most likely work fine. But I suppose I should if possible get something from a manufacturer that actively supports linux - do you have any suggestions?

---

### Post by az on 2006-04-14
[QUOTE=GeorgeAD] The reason I was think of usr was that there seem to be a lot of them around secondhand, and I was under the impression that as long as I got an external one it would most likely work fine. [/QUOTE]

That is correct.  I'm not dissing the products, their hardware modems are unbreakable.  If you buy an external serial modem by any manufacturer (including USR), you will be fine.

---

### Post by helmut_hed on 2006-04-30
An ESS driver has recently been released.  You can find it here:

[http://tx.technion.ac.il/~raindel/ess_2.6-v0.1.tar.gz](http://tx.technion.ac.il/~raindel/ess_2.6-v0.1.tar.gz)

It's based on an ancient 2.2-era driver put out by ESS long ago.

Except for the driver file (ess_2.6-v0.1.tar.gz) the install procedure is analogous to the one in this HOWTO:

[http://ubuntuforums.org/showthread.php?t=171163](http://ubuntuforums.org/showthread.php?t=171163)

Regards,
Jeff Trull

---


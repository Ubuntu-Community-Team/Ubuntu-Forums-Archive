---
title: "Help me please- new to ubuntu."
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by Rabindranath on 2007-06-30
I cant set up my internet connection. I read all the posts here and nothing seems to help me. I use kubuntu and while opening kppp  I get an error "etc/resol.conf" missing or cannot open". I have a dial up connection to the internet. I used scan modem and I got the output. What to do next? 
Note: I am using XP to connect to the internet now.  :(

Here is the output: ModemData.txt





 Only plain text email is forwarded by the  [email]DISCUSS@linmodems.org[/email] List Server.
 Do use the following as the email Subject Line:
           SomeName, YourCountry Ubuntu 7.04  kernel 2.6.20-15-generic 
 This will alert cogent experts, and  distinguish cases in the Archives.
 YourCountry will enable Country Code guidance.
 Occassionally responses are blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) .
 Local Linux experts can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html)
--------------------------  System information ----------------------------
CPU=i686,  Ubuntu 7.04 
Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007
 scanModem update of:  2007_June_19


ALSAversion 1.0.13
USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 06:01.0	134d:2189	134d:1002	Modem: PCTel Inc HSP56 MicroModem 

 Modem interrupt assignment and sharing: 
 20:          0          0   IO-APIC-fasteoi   serial

 --- Bootup diagnositcs for card in PCI slot 06:01.0 ----
[    3.093569] ACPI: PCI Interrupt 0000:06:01.0[A] -> GSI 22 (level, low) -> IRQ 20
[    3.093809] 0000:06:01.0: ttyS1 at I/O 0xb808 (irq = 20) is a 16450
[    3.093963] 0000:06:01.0: ttyS2 at I/O 0xb810 (irq = 20) is a 8250
[    3.094116] 0000:06:01.0: ttyS3 at I/O 0xb818 (irq = 20) is a 16450
[    3.094187] Couldn't register serial port 0000:06:01.0: -28

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1b.0	8086:2668	8086:e202	Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW 

 Modem interrupt assignment and sharing: 
 16:     130204          0   IO-APIC-fasteoi   uhci_hcd:usb5, HDA Intel, i915@pci:0000:00:02.0

 --- Bootup diagnositcs for card in PCI slot 00:1b.0 ----
[   18.017112] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   18.017136] PCI: Setting latency timer of device 0000:00:1b.0 to 64

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

8086:2668 is a High Definition Audio card, possibly hosting a soft modem.
 For candidate modem in PCI bus:  00:1b.0
   Class 0403: 8086:2668 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW
      Primary PCI_id  8086:2668
    Subsystem PCI_id  8086:e202 
    Softmodem codec or Vendor from diagnostics: 
                              from    Archives: 
                        

 Lacking a dsp (digital signal processing) chip, the modem is a software 
 intensive or "softmodem" type. Its primary controller manages the traffic 
 with the CPU. But the software needed is specified in the Subsystem.
 -----------------------------------------
Support type needed or chipset:	

Support can likely be achieved through two mutually exclusive alternatives:
1) An ALSA modem driver plus slmodemd.  Read Smartlink.txt for details, and
to test get the package SLMODEMD-1.0.13.tar.gz from:  
	[http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)
2) The hsfmodem software for Conexant chipset modems: Read Conexant.txt

 An ALSA (Advanced Linux Sound Architecture) modem driver:  snd-intel8x0m
 provides Low Level support enabling contact with the modem hardware.
 For all BUT Conexant chip soft modems (using hsfmodem software)
 complementary High Level support is through a Smartlink utility:  slmodemd

 Download from [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/) 
 the package SLMODEMD-1.0.13.tar.gz having a compiled slmodemd. Unpack under Linux with:
 	$ tar zxf SLMODEMD-1.0.13.tar.gz
 and read instructions therein. But briefly, the modem is setup with command:
 	sudo slmodemd -c YOUR_COUNTRY --alsa modem:1 
 reporting dynamic creation of ports:
	/dev/ttySL0 --> /dev/pts/N   , with N some number
 Read Smartlink.txt and Modem/YourSystem.txt for follow through guidance.


The diagnostic outputs for this softmodem section have their raw information in
folders and text files under /proc/asound/ which you can browse. The information
is from files:
	/proc/asound/pcm
-------------------------------
00-02: ALC880 Analog : ALC880 Analog : capture 2
00-00: ALC880 Analog : ALC880 Analog : playback 1 : capture 2

	/proc/asound/modules
-------------------------------
 0 snd_hda_intel
and from the command:
	aplay -l | grep -i modem


----------------end Softmodem section --------------

scanModem could not identify the Support Type needed from diagnosics or archives.
	If an alternative boot into Microsoft windows can be done, do mouse
clicks on:
   Start > Settings > Control Panel > Classical View (for Window XP) > System
> Hardware > Device Manager > Modems > Click on the + > Modem. Double click to
expand the graphic. Manufacturer information may be displayed. For example, CXT
stands for Conexant. Click the Diagnostics Tab. Record any hardware ID or vendor
and device information.
Next do the Query Modem and record the ATI specifications displayed such as:
    ATI3 - Agere SoftModem Version 2.1.22
    ATI5 - 2.1.22, AMR Intel MB, AC97 ID:SIL REV:0x27
Try to identify the modem setup file, with name perhaps MODEM.INF.
If may contain chipset Vendor informaton.


Writing Intel.txt

 Freeware support may be available for a few Conexant chipset modems 
 with support confirmed only for the PCI_id chipset  14f1:2f00.
 See  [http://ubuntuforums.org/showthread.php?t=180632](http://ubuntuforums.org/showthread.php?t=180632)

 Otherwise formal support for Conexant chipset modems are available ONLY through 
 [http://www.linuxant.com/drivers](http://www.linuxant.com/drivers).  Read Conexant.txt for details.
 and Modem/YourSystem.txt for follow through guidance.  Driver speed is limited to
 14,400 until a key is purchased.  There is NO freeware alternative.
 There are two support package types: hsfmodem  and hcflinmodem.
 [http://www.lorenzobettini.it/linux/LinuxSonyVaioVGN-S5VP_B](http://www.lorenzobettini.it/linux/LinuxSonyVaioVGN-S5VP_B) reports a
 problem and solution in stalling a key, after testing of the free low
 speed download.

 Read Conexant.txt

Writing Conexant.txt

Writing Smartlink.txt
============ end Smartlink section =====================

 For candidate modem in PCI bus:  06:01.0
   Class 0703: 134d:2189 Modem: PCTel Inc HSP56 MicroModem
      Primary PCI_id  134d:2189
 Support type needed or chipset:	slamr
 

 134d:2189  is a PCTel HSP56 MicroModem 688T modem with the Oasis chipset.
 Under 2.6.n kernels, it is only supported through the Smartlink slamr.ko driver.

The modem is supported by the Smartlink slamr driver
plus the slmodemd helper utility.  Read the
Smartlink.txt and Modem/YourSystem.txt for follow through guidance.


 Download slamr-2.6.20-15-generic.tgz from [http://linmodems.technion.il/packages/smartlink/](http://linmodems.technion.il/packages/smartlink/)
 under Linux, open a terminal and unpack with:
 $ tar zxvf slamr*.tgz
 Move into the unpacked folder
 $ cd slamr-2.6.20-15-generic
 Look around
 $ ls
 Run the 
 $  sudo ./setup

 Afterwards do:
 $ slmodemd --help
 $ slmodemd --countrylist &> Clist.txt
 If not in the USA, look for your COUNTRY_NAME therein.
 Do and edit with:
 $ sudo gedit  /etc/default/sl-modem-daemon
 and therein replace the USA in the line:
 SLMODEMD_COUNTRY=USA
 This will provide for the correct Country setting in the automated:
    slmodemd -c COUNTRY /dev/slamr0

 Read the Smartlink.txt and YourSystem.txt 

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.1.2
             and the compiler used in kernel assembly: 4.1.2

 Kernel-header resources needed for compiling are not manifestly ready!

 If compiling is necessary packages must be installed, providing:
	 linux-headers-2.6.20-15-generic


Checking pppd properties:
	-rwsr-xr-- 1 root dip 269224 2007-04-05 09:11 /usr/sbin/pppd

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

Read Modem/YourSystem.txt concerning other COMM channels: eth0 eth0:avah
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
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------

---

### Post by Rabindranath on 2007-06-30
I tried PCTel drivers (i386) but gives errors and it says to download and install alternatives for my system(i386).

---

### Post by jimbob on 2007-06-30
Not sure but it appears you have a software modem (winmodem).

Post the output of lspci
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by Rabindranath on 2007-06-30
I have 13 output txt files but none of them is lspci. I dont understand "lspci". Do you mean this?




Modem Type Readout and Supporting Software Identification.
-------------------------------------------------------
Most add on cards to motherboards (including modems) adhere to a PCI standard, for
which there is firmware on the card which can be readout, providing setup parameters
and specification of the required software. This works under Linux provided that
drivers are resident. Herein is the practical problem. During the evolution of 
modems, some of the complementing software components became Proprietary and
Closed Source.  A consequence is that for reasons of Legality and/or Principle,
many Linux distributions do not distribute such modem drivers with the regular
releases, even when the modem chipset designer does provide Linux support code.
Without the drivers, additional assistance is needed to identify the modem
chipset and its complementing software.

The scanModem script includes four routines to determine the software required:
1) Read outs with a lspci tool accessing firmware on PCI cards.
2) A test using modem drivers already on your system as part of the ALSA (Advanced Linux 
Sound Architecture) software package. See Smartlink.txt for details.
3) Comparison of Primary+Subsystem PCI IDs with others historically gathered, and 
then archived within scanModem.
4) A test requiring the SmartLink slamr.ko driver. See Smartlink.txt for details.

Should these not be adequate, there are directions below for doing diagnostics during 
an alernate Microsoft Windows bootup.

Stop here on a first reading, and just run
   ./scanModem
Read on later if you are interested in details, OR
need instructions for doing modem diagnostics under Microsoft.

Using MicroSoft(MS) Windows:
-----------------------------
MS installations do generally have adequate diagostic capability. Try the following
routine 1), beginning with mouse clicks on:
   1) Start > Settings > Control Panel > Classical View (for Window XP) > System 
> Hardware > Device Manager > Modems > Click on the + > Modem. Double click to 
expand the graphic. Manufacturer information may be displayed. For example, CXT 
stands for Conexant. Click the Diagnostics Tab. Record any hardware ID or vendor 
and device information.
Next do the Query Modem and record the ATI specifications displayed such as:
     ATI3 - Agere SoftModem Version 2.1.22
     ATI5 - 2.1.22, AMR Intel MB, AC97 ID:SIL REV:0x27
Try to identify the modem setup file, with name perhaps MODEM.INF.

   2) Open a COMM console. Send ATI commands to the modem (ATI, ATI1, ATI2, etc) 
which may elicit chipset and driver information. Here is an example:
     ATI3 - Agere SoftModem Version 2.1.22
     ATI5 - 2.1.22, AMR Intel MB, AC97 ID:SIL REV:0x27
successfully identifying an Agere SoftModem chipset, both by name and through 
the softmodem SIL ID: AC97 ID:SIL REV:0x27

The IBM mwave modem:
This has a DSP chip usually seated on the motherboard. Not carried on a PCI card 
it cannot be detected by scanModem. However, the mwave driver is included in 
2.6.n kernel releases.
So try:
   # modprobe mwave
Either the module will load or the absence of the modem will be indicated by:
   FATAL: Error inserting mwave (/lib/modules/2.6.10-1-
686/kernel/drivers/char/mwave/mwave.ko): Input/output error
See [http://www.linuxdocs.org/HOWTOs/mini/ACP-Modem/](http://www.linuxdocs.org/HOWTOs/mini/ACP-Modem/) for details on this modem.

Modem evolution:
----------------
Here is a very abbreviated history on how modem evolutionary development. The
earliest modems (MOdulate and DEModulate signals for phone lines transmission)
managed all signal proceesing on the modem card through actions of expensive
Controllers chipsets with DSP (digital signal processing) capability. Copyrighted 
Vn.nm compression routines were also encoded in the chipset. Under Linux, an Open 
Source serial driver was the minimal complementing software. This generation of 
Controller chipset modems placed minimal burden on the early slow  central 
processing unips (CPU) of personal computers, such as the Intel 386.

As CPUs became faster, it was feasible to transfer some modem functions to
the CPU. A 2nd generation of modems retained a DSP chip, but Controller functions
were software driven on the CPU. A benefit was that modem hardware became cheaper.
But sadly the supporting software was Proprietary. Worst, some Intellectual Property
components were Closed Source to protect large investment in code development. Such
Controller free modems include the Conexant HCF, Intel-537EP and Mars chipset 
modems from Lucent or its later subsidary, Agere Systems Inc.

As CPUs became even faster, even DSP functions could be software code driven on
the CPU. This third generation of modems are commonly called "softmodems". Their
complementing software is comparable in sizeto that of the Linux kernel itself. The
residual "modem chip" is very cheap, but the development of the complementing
software is a large investment on the part of the chip designer/maker. 

Modem chipset determination under Linux:
---------------------------------------
The chipset of a modem determines which complementing software is required.
The Manufacturer and Model of an assembled modem are often inadequate to identify
the chipset. But sometimes there is an easy chipset identification. There is
a "lspci" utility provided in the Linux pciutils package. It reports the PCI 
identifiers (IDs hereafter) or the Primary card, its Subsystem, and some setup
parameters written in firmware. For example, there is a softmodem in the
PCI bus of address 00:11.6 on my laptop. Shown below is firmware information
acquired by two lspci commands:
$[COLOR="DarkOrange"] lspc[/COLOR]i -s 00:11.6
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller
$[COLOR="DarkOrange"] lspci [/COLOR]-s 00:11.6 -nv
     00:11.6 0780: 1106:3068 (rev 80)
        Subsystem: 14ff:100b
        Flags: medium devsel, IRQ 193
        I/O ports at e000 [size=256]
The translation is:  The card inserted into PCI bus slot 00:11.6 is named
"Communication controller: VIA Technologies, Inc. AC'97 Modem Controller".  The 
modem was assembled by a Vendor with ID identification code 1106 . Among 1106's 
products, it has a Device ID of 3068 in its 80th revison.  This usually  provides
adequate information, to get software from the Vendor designated by 1106 (VIA 
Technologies, Inc. in this case) for their device designation 3068.  The parameters
        Flags: medium devsel, IRQ 193
        I/O ports at e000 [size=256]
are determining by the environment of the host computer as reading modem firmware.
It may change if other hardware is added/removed from the host computer, or
under a change or Operating System (OS) kernel.

The problem for softmodems is that additional information is needed for the software
specification. The Subsystem Vendor_ID identifies only the assembler company.  But 
the modem chip housed in the Subsystem could be of a variety of types, each requiring 
different support software. In general, a single Subsystem assembler could use a
variety of different softmodem chips.  The Subsystem firwmare information on the chipset
is not accessible to lspci. Rather it requires usage of a modem driver, if one first had
some competent modem driver for minimal diagnositcs.

Fortunately there are the software tools and drivers of the ALSA (Advanced Linux 
Sound Architecture) suite. This includes modem drivers lacking COMM proficiency by
themselves, but enough capability to readout the Subsystem firmware.  For the VIA
modem above, the encoded modem codec is SIL22, reporting that the softmodem chip was
made by SmartLink Inc. 

It is important to emphasis, that AC'97 Modem Controllers are made by a variety
of companies, and each may house many different Subsystem modem chips. There is
an Archive within scanModem of those with previously identified codecs. For example, 
the table for the 1106:3068 AC'97 Controller is:
	codec SubSystems_with_codec  ------------>
	CXT   104d:8143 104d:80f6 1025:0030 
	SIL27 1102:0033 1025:0046 1025:0033 1734:1078 1509:2870 1025:0046 
	SIL22 1743:1032 10cf:118e 1734:1054 1462:309e 1631:e004 1543:4c22 161f:2032 and_more
	SIL21 10cf:118e 13bd:1022 1543:4c21 1071:8375 1019:0c04 1458:1543 1019:b320
	MOT66 1734:109b 
Because of hardware configuration issues, the ALSA tools may initially fail. Then this
Archive is a fall back reporting the codec, and therefrom the needed software. For reasons
obscure, a single Subsystem ID may have different codecs under different Primary
controllers. Thus the pair Primary+Subsystem IDs must BOTH be retained to record 
the codec.

In addition to the Modem Controllers adhering to the AC'97 specifications, softmodem
Subsystems may be hosted by High Definition Audio (HDA) cards such as the:
8086:2668 Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
These lack a softmodem codec.  Instead the softmodem chip information acquired with ALSA
tools is within a folder:   /proc/asound/card0/codec*#1/
and includes the Vendor ID of the softmodem chip, such as 14f1 corresponding to Conexant. 

The software support:
---------------------
The CXT designation above is an abbreviation of CXT_some_number, for Conexant HSF softmodem 
codecs. These now number some 41 (perhaps more) CXT. Fortunately, all these codecs are
supported by a single hsfmodem software package provided through [http://www.Linuxant.com](http://www.Linuxant.com)
The trial package is free, but locked to speeds of 14,400 K.  A software key must be 
purchased to enable full speed support, with future software updates free. There is NO
freeware alternative for the hsfmodem software.  But Linuxant does provide pre-compiled
drivers for the more common Linux kernels, and their support services are good.

In the Table below, there are currently some 13 other softmodem codecs. Fortunately
all are supported by a combination of the ALSA modem drivers, the ALSA audio drivers
the modem drivers depend on, and a very smart helper utility from Smartlink Inc.,
the slmodemd helper. Sasha Kharposky wrote the Linux slmodemd utility and remains its
volunteer maintainer. It  provides the cleverness to interface between the low level 
ALSA modem driver and the pppd package communications codes. For details do:
$ slmodemd --help
and read associated documentation.  The slmodemd is provided with some Linux distributions,
and can also be downloaded in SLMODEMD packages from:
    [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)

Subsystems of AC'97 Modem Controllers
--------------------------------------- 
Subsystems for softmodems are primarily made by Silicon Labs (SIL) under 
contract to companies like Intel, Agere Systems, Motorola etc. In the Table 
below, ChipMadeBy does NOT imply software support directly from that 
manufacturer. The chart of information below is largely harvested from messages 
to [email]discuss@linmodems.org[/email].
A codec_indent such as REV:0x27 is reported by diagnostics under Microsoft, as 
illustrated above. The matching designations such as SIL27 are translations 
under Linux, which are output by a diagnostic of the slamr.ko driver from the 
SmartLink slmodem software.
SIL is an abbreviation for Silicon Laboratories Inc., which provides Subsystems
on order to many modem assemblers. 
SML is used below as abbreviation for SmartLink Inc. with official driver 
resources at [http://www.smlink.com/main/index1.php?ln=en&main_id=40](http://www.smlink.com/main/index1.php?ln=en&main_id=40) .  BUT use
updated resources at [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/).
ALSA+SML means use an ALSA modem driver plus the Smartlink slmodemd helper,
with the particular driver depending on the AC'97 or HDA host controller.
ID was originally a hexadecimal readout from 7c and 7e registers of the SubSystem, 
but are translated into "english", as done automatically by the slamr driver.

ID    chip_maker     driver/helper sources
----------------     ----------------------
CXTnm   Conexant     hsfmodem package from [http://www.linuxant.com](http://www.linuxant.com) with several hsf* drivers.
   nm - a number
SIL25   Intel        ALSA+SML or INTEL-537EP supported AA variant
INT65   Intel        ALSA+SML or INTEL-537EP supported EA variant
SIL26   SML          SML, slamr driver plus slmodemd
SIL27   AgereSystems ALSA+SML
SIL2F     "          ALSA+SML
MOT66     "          ALSA+SML
AGR01     "          ALSA+SML
AGR02     "          ALSA+SML 
SIL21   PCTel        ALSA+SML
SIL23   PCTel        ALSA+SML
SIL22   SML          ALSA+SML
SIL24   Broadcom     ALSA+SML
BCM64   Broadcom     ALSA+SML, under Intel ICH family, AC'97 controllers.
----------------------------------------------
Subsystems with the above characteristics could reside under any of
the primary softmodem controllers listed below. Ignore the stuff after the > .
It serves during parsing of the Table by scan modem

Primary              
PCI_IDs           Name	                   Possible support by:
---------------  -----------------------------  -------------------------
8086:2416 82801AA ICHAA AC97 Modem Controller>  		+ A a  p c .
8086:2426 82801AB ICHAB AC97 Modem Controller> 		+ A a .
8086:7186 >				        			c .
8086:7196 82440MX Banister AC97 Modem Controller >     	+ A a      c .
8086:2446 82801BA/BAM ICH2 AC97 Modem Controller > 		+ A a p c .
8086:2486 82801CA/CAM ICH3 AC97 Modem Controller > 	+ A a p c i .
8086:24c6 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M)1DB ICH4 AC97 Modem Controller> 		+ A a   c i b .
8086:25a7 6300ESB AC97 Modem Controller  NEW >
8086:24d6 82801EB/ER ICH5/ICH5SR AC97 Modem Controller> 		+ A     c i .
8086:8280 1EB ICH6 AC97 Modem Controller> 	        + A	c .
8086:2668 Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller> H c . 
8086:266d Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC97 Modem Controller >
8086:2669 631xESB/632xESB AC97 Modem Controller  NEW >
8086:27d8 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller HDA > .
8086:27dd (ICH7 Family) AC97 Modem Controller  NEW >
8086:xxxx types above are from Intel> 

1039:7013  SIS 630 >               		+ a p c i .
1039:7018  SIS 960 >               		+       i .
10de:01c1  Nvidia Corp >          		+       i .
10de:00d9  Nvidia Corp >			    A      c   .
1106:3068  VIA >			+ a p c i .
1022:7446  AMD AC_LINK >		+ .
10b9:5450  ALI 5450 >
10b9:5451  ALI 5451 >			+ a  c .
10b9:5453  ALI 5453 AC-Link  >	      	p c .
1025:5453  ALI 5453 AC-Link  > 		    c .
10b9:5457  ALI 5457 AC-Link > 	+    p   c i .
1025:5457  ALI 5457 AC-Link  >        	     c .                   .
1002:434d  ATI >					  T  a    c i .
1002:437b  ATI Audio device: ATI Technologies Inc SB450 HDA Audio a .
1002:4378 ATI >						     c .
1543:3052  SI3052 >

Class 0403, High Definition Audio Controllers (HDA)
-----------------------------------------------------
8086:2668   Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) HDA Controller
8086:27d8   Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller
1002:437b   Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
10de:026c   nVidia Corporation MCP51 High Definition Audio
----------------------------------------------------
are the members of this family encountered as of September 2006.
From the file  /proc/asound/card0/codec*#1/, there are the following Subsystem chips:

  Vendor IDs  Chip maker     Support type
  ----------  ----------    -------------
  0x14f12bfa  Conexant      hsfmodem , not slmodemd compatible
  0x11c13026  AgereSystems  snd-hda-intel, slmodemd
  0x163c3055  Smartlink         "             "
  0x163c3155    "               "             "
  0x10573055  Motorola          "             "
  0x10573155     "              "             "

---

### Post by Grigorius on 2007-06-30
Open the terminal and write "lspci" (without the quotes) (then press enter) and copy paste what is says.

---

### Post by oilchangeguy on 2007-06-30
you can try this:
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)
but your best bet is to get an external serial port modem. they seem to work right out of the box, for most people.

---

### Post by Rabindranath on 2007-07-01
I have seen that topic but it does't help me. However this is the output of lspci.









00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:01.0 Modem: PCTel Inc HSP56 MicroModem (rev 04)
06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 01)

---

### Post by Alterax on 2007-07-01
Sounds like a DNS issue at first.

If you don't have an /etc/resolv.conf file, make one with nano (sudo nano /etc/resolv.conf)
Now get the information for your DNS server.  Add a line for each like this:
nameserver 111.222.111.222  
where the numbers are replaced by the DNS servers.

Hit CTRL-X to save it, then:
sudo chown root /etc/resolv.conf
sudo chmod 644 /etc/resolv.conf
sudo /etc/init.d/networking restart

Give that a try and see if it helps.

--Alterax

---

### Post by kirios on 2007-07-01
[COLOR="DarkSlateBlue"][SIZE="2"]If you have a winmodem, you could save yourself a lot of time and frustration by getting a hardware modem instead.[/SIZE][/COLOR]

---

### Post by Rabindranath on 2007-07-01
Then, is mine a sofware modem? I have drivers for linux. There are 3 types for linux. Linux 7.0,linux 8.0, linux 9.0. I think they are for red hat. Is that enough for kubuntu? Those files look like ordinary text files. If it is enough for kubuntu, how do I execute those files? Thanks for the fast replies :)

---

### Post by lame_duck on 2007-07-04
Your modem has been supported by Linux since 2000 - 2002 so you should be safe. What I suggest is change where you're telling KPPP to check for a modem at. IE: Mine says my modem is at /dev/modem when it's actually at /dev/tty03. I don't remember the command for check where your modem is keep in the system so try a process of elimination. KPP should have a drop-down box with all the logical locations for you modem and try them one by one. If that doesn't work, get back to me and I'll figure out what todo.

Been a while since I had to debug a modem so be easy on me. lol

---


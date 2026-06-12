---
title: "Please Help!!!"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by iritegood on 2007-03-25
I just bought a modem that supposedly supported linux from Fry's this morning. I tried to follow the directions on the CD but I kept getting errors. After downloading a newer version from the internet I still kept getting errors when trying to install it. Can someone just give me straight directions? What files should I download and what do I have to type into the terminal? I'm really new to Ubuntu and still don't understand a lot. Can someone please help me?

My modem is a Smartlink PCI one. Here's the "Smartlink.txt" file from the driver I downloaded from the internet.

```

 Smartlink modem setup.
 -----------------------------------------------------------
 The modem should setup with:
     modprobe ungrab-winmodem
     modprobe slamr
      slmodemd -c YOUR_COUNTRY   /dev/slamr0
 which should announce creation of ports:
    /dev/ttySL0 --> /dev/pts/N   , N some number
 Specify the symbolic link  /dev/ttySL0  as the port to be used by dailer software.


 SmartLink (http://www.smlink.com/) chipset modems are sold under a variety 
 of BrandNames, and have vendor IDs 163c, 2000, 2003, and 2004. Conexant bought
 Smartlinks's modem techhology sector in 2005. While Linux updates are not
 expected from Conexant, Linux support is still very good thanks to volunteer
 Linux maintainer Sasha Khapyorsky. Get his updated software from:
	http://linmodems.technion.il/packages/smartlink/

 A high level support component is a smart helper:            slmodemd
 Acting through one of several drivers, it creats ports dynamically and
 supports COMM and FAXing functions.  During facsimile usage, the AT&F command 
 is not supported.  Usage of SMP (Symmetric MultiProcessor) mother boards is
 supported. For service on 64 bit AMD x86_64 processor mother boards, see
        http://linmodems.technion.ac.il/archive-fourth/msg02594.html
	http://linmodems.technion.ac.il/archive-fifth/msg02490.html
 However a 64 bit compilation of a proprietary dsplibs.o conponent is not
 available. Hence for modem must be operated in 32 bit mode. The compiling
 must be done with the 32 bit version of compiling resources

 The slmodemd supports a few different types of modem drivers.  Below the suffix 
 .ko means the modular form of a driver, before loading into the kernel. The
 slmodemd does not access the modem hardware directly. Rather access is provided
 through lower sophistication drivers. Prior to usage of a slamr driver, there
 must be a release of serial driver interference by loading of:  ungrab-winmodem.ko
 For PCI card modems with Smartlink chips the driver used is:    slamr.ko 
 For USB modems with ID 0483:7554 use Smartlink driver:          slusb.ko 
 For ALSA (Advanced Linux Sound Architecture) modem drivers, see the Table below.

 Sasha's core resources are:
 ----------------------------
 ungrab-winmodem.tar.gz - for compiling a ungrab-winmodem.ko driver
 slmodem-2.9.11-MostRecentDate.tar.gz  - the core code resource for compiling
    and installing slmodemd, slamr.ko and slusb.ko.  The slmodemd dynamically 
    creates ports and provides higher level COMM functions, after driver
    loading. Not being a driver, slmodemd serves under alternative boot kernels.
 ALSA modem drivers, included with 2.6.n kernel+module releases.
 
 Some derivative resources at http://linmodems.technion.il/packages/smartlink/
 SLMODEMD.gcc3.tar.gz - containing a compiled slmodemd and usage instructions.
    When used with ALSA modem drivers, further compiling is not necessary.
    > SLMODEMD.gcc3.tar.gz will suffice for getting online, though read on about automation. <<<
 sl-modem-daemon-SomeVersion.deb - an installer for Debian related distros.
    It has slmodemd and scripts for starting slmodemd at boot.
    This package is also available from repositories of Debian related distros  
    Ubuntu, Kbuntu, Ebuntu, Xandros, Kanotix and others.
 sl-modem-daemon-SomeVersion.tar.gz has the same contents, but is repackaged
    in an easily opened format, for access to its automation scripts.
    After unpacking, they are resident in the etc/  subfolder
 sl-modem-source-SomeVersion.deb - is a Debian installer for the slamr and slusb
    source code.  It is Not necessary for ALSA driver usage.
 slamr-KernelVersion.tar.gz - for several Ubuntu KernelVersions, containing:
    ungrab-winmodem.ko, slamr.ko, slusb.ko, slmomdem, setup script and as 
    a convenience, the sl-modem-daemon-SomeVersion.deb.  Look in the folder:
    http://linmodems.technion.il/packages/smartlink/ubuntu/

 Slmodemd actions
 -----------------------------------------
 Start working with slmodemd with commands:
	slmodemd --help
        slmodemd --countrylist
 The long output can be written to a Clist.txt file with: 
        slmodemd --countrylist &> Clist.txt
 Find your COUNTRY_NAME within the 2nd column if the list and record it.
 It will be used in capital letters during the modem setup command.
 Try USA if your COUNTRY is not in the list.

 Before modem setup root/adm capacity must be acquired with:
	su - root
 or by prefixing commands with "sudo" for Ubuntu Linux and its cousins.
 The setup command is:
         slmodemd -c COUNTRY_NAME --alsa slmodemd_device
 if successful there will be reported dynamic creation of:
        /dev/ttySL0 --> /dev/pts/N    , with N a number
 The /dev/ttySL0 is a symbolic link to the real modem port /dev/pts/N ,
 and it is /dev/ttySL0 which should be named to dialup utilities such
 as wvdial.  The "--alsa" is only needed for usage with ALSA modem drivers.
 Throughout a dialout session  slmodemd MUST be kept running. Open another
 console/termimal to startup dialout software such as wvdial.

 The slmodemd device nodes
 ---------------------------
 The slmodemd_device is different for the several modem drivers.
 For usage with slamr.ko , the slmodemd_device is /dev/slamr0 , within 
 the command sequence:
         modprobe ungrab-windmodem
         modprobe slamr
	 slmodemd -c COUNTRY_NAME /dev/slamr0
 For USB modem usage:
         modprobe slusb
	 slmodemd -c COUNTRY_NAME /dev/slusb0
 For a modems using a ALSA driver, details are below.

 The /dev/slamr0 and /dev/slusb0 will be made the slmodem installation
 processes. However, they usually will NOT survice reboot, because
 most current Linux have ports created in volatile RAM space. However
 the these devices can be manually created under root/adm persmission with:
	 mknod -m 600 /dev/slamr0 c 242 0
	 mknod -m 600 /dev/slusb0 c 243 0
 if automation scripts are not yet in place.

 For automation of RPM using Linux distros see:
    http://www20.brinkster.com/olivares/slmodemd-setup-1.html
 For any Distro the following lines will serve in /etc/modprobe.conf or subfolders of
   /etc/modprobe.d/:
--------------
alias char-major-243 slusb
alias char-major-242 slamr

# The following  install and remove commands are to be written as single lines.
#    Preloads ungrab-winmodem and creates a device node upon "modprobe slamr"
install slamr modprobe --ignore-install ungrab-winmodem ;  modprobe --ignore-install slamr; test -e /dev/slamr0 || (/bin/mknod -m 660 /dev/slamr0 c 242 0 2>/dev/null && chgrp dialout /dev/slamr0)
# rpm using distros should use "uucp" rather than "dialout"

#     Removes slamr and ungrab-winmodem successively:
remove  slamr  /sbin/modprobe -r --ignore-remove  slamr ;  /sbin/modprobe -r --ignore-remove ungrab-winmodem


 Usage with ALSA modem drivers
 --------------------------------
 See SoftModem.txt for a description of the hardware.  For a modem using 
 an ALSA driver, the slmodemd_device only has to be  specified within the 
 slmodemd command line.  A preliminary "mknod something" command is not necessary. 
 The Table shows hardware PCI ID, its card type, driver and slmodemd_device name.
 The ALI5451 and HDA (High Definition Audio) cards can host softmodems. For these
 cards hw:0,0  is the audio card designation and the modem Subsystem on it 
 is most commonly hw:0,1 , but there are some hw:0,6 cases. For the older
 soft modem controller family, the ALSA software first assigns hw:0 to an audio
 card, and the following modem designation is hw:1 or equivalently modem:1
 An attempt to use modem:0 may initially appear successful, but modem:0 or hw:0 
 is actually the companion audio card. 

PCI  ID      controller           ALSA driver      slmodemd_device 
=========    ===============    ===============    ===================
several      HDA cards          snd-hda-intel      hw:0,1  or  hw:0,6
10b9:5451    ALI5451 audio      snd-ali5451        hw:0,1
------------------ softmodem controllers --------------------------
1002:434d    ATI                snd-atiixp-modem   modem:1 
1002:4378    ATI                        "            "
1106:3068    VIA                snd-via82xxx-modem   "
8086:xxxx    many Intel         snd-intel8x0m        "
10de:00d9    Nvidia Corp            "                "
1039:7013    SIS 630                "                "
   Others?                          "   test         "
---------------------------------------------------------------------------
* The scanModem script tries to determine ALSA modem driver and slmodemd_device 
dynamically from /proc/asound/ information, or the internal Archive as a fallback.

 Do a precautionary unloading and reloading of the driver.
	su - root 	(not for Ubuntu)
	 modprobe -r driver
	 modprobe driver
 This precaution is sometimes necessary, because a driver may functionally die
 although loaded. But usually it can be skipped.

 For most modems the setup command is:
	 slmodemd -c COUNTRY_NAME --alsa modem:1
 For modems on HDA cards, the command is:
 	 slmodemd -c COUNTRY_NAME --alsa hw:0,1  
             though there have been cases of  hw:0,6
 For the ALI5451 hosted modems, a shortbuffer (-s) option is needed:
	 slmodemd -s -c COUNTRY_NAME --alsa hw:0,1


 The slamr diagnostic
 ---------------------
 Sasha has provided slamr.ko with a capability for reporting softmodem codecs,
 even for modems not supported fully by slamr. This is useful when other
 resources do not report out the modem codec, needed to distinguish between 
 hsfmodem, slamr and ALSA driver support alternatives.
 This slamr test is Not effective for softmodems on HDA audio cards.

 The test routine is:
     modprobe ungrab-winmodem
     modprobe slamr
 followed by a readout from the dmesg buffer with:
    dmesg | grep slamr
 Among the few output lines, there is one like:
    slamr: mc97 codec is SIL27
 reporting in this example an ALSA driver supported, Agere Systems codec SIL27.
 Conexant codecs have format CXTnm, nm a number. These modems are not ALSA driver supported.
 Softmodems with all other codecs should be ALSA driver plus slmodemd supported.

Compiling details
-----------------
Within a slmodem-SomeVersion/ folder, always before compiling do a precautionary:
$ make clean
The next step is
$ make
The file slamr_compile.txt is the record of a compilation of slmodemd, slamr.ko and slusb.ko.
The command pair:
$ su root
# make install 
OR for Ubuntu
$ sudo make install
will install the drivers, make device nodes and copy slmodemd to /usr/sbin/slmodemd

IMPORTANT - ALSA driver competence of slmodemd requires a different process.
First a package libasound2-dev (for Debian/Ubuntu like distros) must be installed.
This resource package may have a different name for RPM using distros.
To compile do:
$ cd modem
$ make clean
$ make ALSA=1
The slmodemd product will reside in the modem/ folder. Put it on the COMMAND path with:
$ su - root
$ cp slmodemd /usr/sbin/
OR for Ubuntu related Distros:
$ sudo cp slmodemd /usr/sbin/
Note that slmodemd need NOT be compiled again with each change of kernel. 
Its functioning is NOT tightly kernel version dependent, in contrast to drivers.

 ============ end Smartlink section =====================

```

Please Help!

---

### Post by iritegood on 2007-03-25
And incase it helps any: the brand on the box says Hummingbird or something similar. The back of the box says it supports Windows and Linux. Please! I really need this to work!

---

### Post by Gilgad Drumheller on 2007-03-25
This should help you: [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)
It seems you would follow the directions for the smartlink drivers.  Other than that, i have no experience using dial-up on linux.

---

### Post by iritegood on 2007-03-25
AFter following soem directions it told me to install g++ 3.4 or something. But it said I also have to install libstdc++6-dev because g++ depends on libstdc++6. But libstdc++6-dev depends on g++ 3.4. Paradox? How do I install any of them?

---

### Post by MrKlean on 2007-03-25
Go to System>Administration>SynapticPackageManager>do a search on those file names...and install them...that should do it for you ; )

---

### Post by mtalexan on 2007-05-04
It sounds like you're missing the buildessentials.  Get that from the Synaptic Package Manager and it should take care of most your problems.

---

### Post by hasala on 2008-02-06
(if you use this method you can forget about the rpms no rpm will be needed to be installed for you to get the modem running.)
RATHER THAN EXTERNAL MODEMS internal modems offloads a lot of funtionality to the software driver.it has always been a big problem to configure those internal modems or(WINMODEMS/LINMODEMS) to work with linux because of manufacturers not supporting linux (and also the driver being pretty much more complex than ) But due to a great person Linux maintainer Sasha Khapyorsky writing the neccassary drivers needed to work the winmodem , now using a internal modem in linux has become as easy as ABC.


Linux maintainer: Sasha Khapyorsky. Get his updated software from:
[http://linmodems.technion.il/packages/smartlink/](http://linmodems.technion.il/packages/smartlink/)


what to do.

1. download a software called scanmodem from the foresaid site.

2. Browse [http://linmodems.technion.ac.il](http://linmodems.technion.ac.il) and  download scanModem.gz .
 Within a Linux partition open up a console and type in the following commands
    gunzip scanModem.gz
 To make it executable:
    chmod +x scanModem
 Run diagnositics with:
    ./scanModem 
3.scanmodem will check your hardware and software and then write its diagnostics to a subdir called modem.

4.open the ModemData.txt file.and go to   -----------end Softmodem section----------- part .

5.it will give the softwares you need to download and install.

6.if u have not installed the source at the installation of the distro. please install it.(source of the kernel) from the installation cd/dvd.

7.then install the downloaded software.

8.go to scanmodem/modem and open the diagnostic file chipsetname.txt eg:Smartlink.txt/conexant.txt .

9.In the start of the doc it gives the commands you have to run at the console to load the drivers that u downloaded and installed.

10.make sure that the smpppd, pppd services are installed and running.else install both and remember to enable them.

11.dial up using kinternet(i prefer it) or kppp. put to stupid mode option..now configure kinternet and the modem properly.to do that 
 goto yast->network devices ->modem.
           1.choose your modem device and press edit.
              enter modem device as /dev/ttySL0 and enter the details of the isp. if you are not sure call customer support for internet of your isp (internet provider) and get the required details such as number to dial and prefix.username
and password.

           2.remember to definitely check the box for stupid mode.

now every thing is set up

enjoy the internet with a great browser like firefox/opera.!!!!!!!
(with this you do not need any rpm for you to download,what you compile is enough)
if u have any comments or questions please mail to:dharmawardena_06@elect.mrt.ac.lk

						or [email]hasaladharmawardena@yahoo.com[/email]
or //(hasalaid@gmail.com).

hasala dharmawardena
faculty of engineering
department of electrical engineering([www.elect.mrt.ac.lk](www.elect.mrt.ac.lk))
University Of Moratuwa
SRILANKA

regards from srilanka , hasala.         ([www.hasala.bravehost.com](www.hasala.bravehost.com))

---


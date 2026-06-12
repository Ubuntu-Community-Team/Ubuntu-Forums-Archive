---
title: "winmodem help and a PnP error?"
date: 2005-06-21
forum: Absolute Beginner Talk
---

### Post by CoriolisSTORM on 2005-06-21
Okay everyone, I finally got Ubuntu loaded and ready the other day.  Now, I need to get my winmodem working.  It's an Agere winmodem and it is in PCI slot 3.  Now as a complete noob, how would I go about making it work?  All the articles I've found say to download a driver for it, but its a tad bit hard to do that when you dont have 'net access within Linux.  And on another note, whenever I start Ubuntu, it says that "Your PNP BIOS caused an error.  You might want to try booting with the "nopnp" option."  yet it continues to boot and does fine.  What does that mean?

---

### Post by az on 2005-06-21
try this:

[https://wiki.ubuntu.com/forum/hardware/modem](https://wiki.ubuntu.com/forum/hardware/modem)
[https://wiki.ubuntu.com/forum/hardware/smartlink](https://wiki.ubuntu.com/forum/hardware/smartlink)


Also, you can get rid of the error by adding the nopnp option to your grub menu.list.  Add it to the end of your kernel line.  You may also just be able to disable pnpos in your bios (that would be easier)

---

### Post by CoriolisSTORM on 2005-06-22
Well, I get this.  Here is a copy of everything in the terminal.  What am I doing wrong? Or what does all this (seemingly) gibberish mean?
---
rob@ubuntu:~ $ cd Desktop/
rob@ubuntu:~/Desktop $ gunzip scanModem.gz
rob@ubuntu:~/Desktop $ chmod +x scanModem
rob@ubuntu:~/Desktop $ sudo ./scanModem
Password:
Sorry, try again.
Password:

UPDATE=2005_June_21
ONLY use scanModem downloaded as: [http://linmodems.technion.ac.il/packages/scanM](http://linmodems.technion.ac.il/packages/scanM) odem.gz

./scanModem should ONLY be run within a Linux/UNIX partition.
If within a MicroSoft/DOS partition, abort with Ctrl-C now !!!
Copy scanModem.gz to your Linux partition and restart.

./scanModem: line 1: gcc: command not found
PCIBUS=0000:01:08.0

Providing detail for device at  0000:01:08.0
  with vendor-ID:device-ID
            ----:----
Class 0780: 11c1:044c   Communication controller: Lucent Microelectronics LT Win Modem (rev 02)
  SubSystem 11c1:044c   Lucent Microelectronics LT WinModem
        Flags: bus master, medium devsel, latency 64, IRQ 209

                  -----PCI_IDs-------                    --CompilerVer-
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 11c1:044c 11c1:044c debian 2.6.8.1-3-386  3.3.4 none    i686


 The modem has a supported Lucent/Agere DSP (digital signal processing) chipset
  with primary PCI_ID:  11c1:044c
 DSP=1

 Agere Systems, Inc provides periodic software releases for there DSP modems,
 which are made more Newbie friendly by volunteers.  There are some installer pa ckages
 and also resources for compiling drivers:
 [http://ltmodem.heby.de](http://ltmodem.heby.de)  is a repository for installers for later 2.4.2n and ear ly 2.6.n  kernels.
      Packages below are for compiling drivers:
            ResourceName                Use for kernel ranges
        ------------------------------------------------------------------------ --------------------------
        ltmodem-8.26a.tar.gz         kernels 2.4.21 and earlier
        ltmodem-8.30a3.tar.gz       kernels 2.4.21 and subsequent 2.4.2n kernels
        ltmodem-8.31a10.tar.gz     beginnig with 2.4.21 through and into 2.6.n kernels

 [http://linmodems.technion.ac.il/packages/ltmodem/](http://linmodems.technion.ac.il/packages/ltmodem/)
        has installers for older 2.4.n kernels moved from [http://ltmodem.heby.de](http://ltmodem.heby.de) 
        and subfolder kernel-2.6/  for 2.6.n  kernel support.  The latest resouc e is:
        ltmodem-2.6-7-alk-7.tar.bz2  from Alex Kondratenko
        ltmodem-2.6-7alk.src.rpm is a repackaging for by Stephan Puck.  After in stallation
            of a kernel-source package (not necessary for fedora releases) use b y:
            rpmbuild --rebuild ltmodem-2.6-7alk.src.rpm  , which will deposit an  installer at:
                /usr/src/rpm/RPMS/i586/ltmodem-kv_YourVersion.rpm          Check  with
            # ls -l   /usr/src/rpm/RPMS/i586/ltmodem*
            Then install with:
            # rpm -i /usr/src/rpm/RPMS/i586/ltmodem-kv_YourVersion.rpm

Support is effective at least into  2.6.11-1.14_FC3.
PCMCIA ltmodem support is still being  ported from 2.4.n to 2.6.n, as of May 200 5

 [http://dag.wieers.com/packages/kernel-module-ltmodem/](http://dag.wieers.com/packages/kernel-module-ltmodem/) for some 2.4.n installers 
 SuSE/Novell has some ltmodem installers at their repositories and newer install  CDs.
 More related output is below.



   A subfolder Modem/  has been written,  containing these files with more detai led Information:
 ------------------------------------------------------------------------------- -----------
 1stRead.txt DriverCompiling.txt InfoGeneral.txt ModemData.txt Rational.txt Slmo dem-ALSA.txt Slmodem.txt SoftModem.txt Testing.txt UNSUBSCRIBE.txt YourModem.txt 
-------------------------------------------------------------------------------- -----------
       Please read 1stRead.txt first for Guidance.

rob@ubuntu:~/Desktop $ cd Modem
rob@ubuntu:~/Desktop/Modem $ ls
1stRead.txt          InfoGeneral.txt  Rational.txt      Slmodem.txt    Testing.txt      YourModem.txt
DriverCompiling.txt  ModemData.txt    Slmodem-ALSA.txt  SoftModem.txt  UNSUBSCRIBE.txt
rob@ubuntu:~/Desktop/Modem $ General.txt ModemData.txt SoftModem.txt UNSUBSCRIBE .txt
bash: General.txt: command not found
rob@ubuntu:~/Desktop/Modem $ cat ModemData.txt


 DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 4.10 "Warty Warthog"  kernel 2.6.8.1-3-386
 Occassionally reponses are blocked by an Internet Provider mail filters.
 So do in a day also check the Archived responses at [email]DISCUSS@linmodems.org[/email]
Code updated on:  2005_June_21
------------ --------------  System information ------------------------
 Ubuntu 4.10 "Warty Warthog"
 on System with processor: i686
 currently under kernel:   2.6.8.1-3-386
 The kernel was assembled with compiler:  3.3.4
 a gcc-3.3  package must be installed to support driver compiling

A package kernel-kbuild-3.6 or later version must be installed to support compil ing

Checking for kernel-headers needed for compiling.
Checking /usr/src/ for compressed compressed headers or kernel-source

Kernel-header resources needed for compiling are not manifestly ready!
If compressed resources are present, expand and then configure them following Dr iverCompiling.txt
They may have to be installed.
Within your Linux distributions' installation CD or online resource (and mirrows ), search for :
  Distribution  PackageName                     OnLine
  ----------------------------------------------------------------------
 Debian                 kernel-headers-2.6.8.1-3-386            [http://www.debia](http://www.debia) n.org/distrib/packages or install CD
 Ubuntu                 linux-headers-2.6.8.1-3-386             [http://http://pa](http://http://pa) ckages.ubuntu.com/ or install CD
 Xandros
                        kernel-kbuild-3.6 are additionally required by  Debian, Ubuntu and Xandros
 Mandrake       kernel-source-2.6.8.1-3-386        If not present on install CDs  search
        [http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/](http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/) RPMS/
        [http://rpms.mandrakeclub.com/rpms/mandrake/official/LByName.html](http://rpms.mandrakeclub.com/rpms/mandrake/official/LByName.html), or oth er mirrors.
  SuSE          kernel-source-2.6.8.1-3-386              , kernels are named k_d eflt
One of which must be installed if compiling drivers to match kernel 2.6.8.1-3-38 6 proves necessary.
Within the output Modem/ folder, read CompilingDrivers.txt for details.


Please install the package WVDIAL for modem testing and dialout.

 A /dev/modem symbolic link is not set.
 USB modem not detected.

0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)

Modem candidates are at PCI_buses:  0000:01:08.0

Providing detail for device at  0000:01:08.0
  with vendor-ID:device-ID
            ----:----
Class 0780: 11c1:044c   Communication controller: Lucent Microelectronics LT Win Modem (rev 02)
  SubSystem 11c1:044c   Lucent Microelectronics LT WinModem
        Flags: bus master, medium devsel, latency 64, IRQ 209

                  -----PCI_IDs-------                    --CompilerVer-
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 11c1:044c 11c1:044c debian 2.6.8.1-3-386  3.3.4 none    i686

 == Checking PCI IDs through modem chip suppliers ==

 The modem has a supported Lucent/Agere DSP (digital signal processing) chipset
  with primary PCI_ID:  11c1:044c
 DSP=1

 Agere Systems, Inc provides periodic software releases for there DSP modems,
 which are made more Newbie friendly by volunteers.  There are some installer pa ckages
 and also resources for compiling drivers:
 [http://ltmodem.heby.de](http://ltmodem.heby.de)  is a repository for installers for later 2.4.2n and ear ly 2.6.n  kernels.
      Packages below are for compiling drivers:
            ResourceName                Use for kernel ranges
        ------------------------------------------------------------------------ --------------------------
        ltmodem-8.26a.tar.gz         kernels 2.4.21 and earlier
        ltmodem-8.30a3.tar.gz       kernels 2.4.21 and subsequent 2.4.2n kernels
        ltmodem-8.31a10.tar.gz     beginnig with 2.4.21 through and into 2.6.n kernels

 [http://linmodems.technion.ac.il/packages/ltmodem/](http://linmodems.technion.ac.il/packages/ltmodem/)
        has installers for older 2.4.n kernels moved from [http://ltmodem.heby.de](http://ltmodem.heby.de) 
        and subfolder kernel-2.6/  for 2.6.n  kernel support.  The latest resouc e is:
        ltmodem-2.6-7-alk-7.tar.bz2  from Alex Kondratenko
        ltmodem-2.6-7alk.src.rpm is a repackaging for by Stephan Puck.  After in stallation
            of a kernel-source package (not necessary for fedora releases) use b y:
            rpmbuild --rebuild ltmodem-2.6-7alk.src.rpm  , which will deposit an  installer at:
                /usr/src/rpm/RPMS/i586/ltmodem-kv_YourVersion.rpm          Check  with
            # ls -l   /usr/src/rpm/RPMS/i586/ltmodem*
            Then install with:
            # rpm -i /usr/src/rpm/RPMS/i586/ltmodem-kv_YourVersion.rpm

Support is effective at least into  2.6.11-1.14_FC3.
PCMCIA ltmodem support is still being  ported from 2.4.n to 2.6.n, as of May 200 5

 [http://dag.wieers.com/packages/kernel-module-ltmodem/](http://dag.wieers.com/packages/kernel-module-ltmodem/) for some 2.4.n installers 
 SuSE/Novell has some ltmodem installers at their repositories and newer install  CDs.
 More related output is below.


 Vendor 11c1 corresponds to Lucent Technologies or subsidiary Agere Systems, Inc .
 Information is at:  [http://www.agere.com/client/modem_dsp.html](http://www.agere.com/client/modem_dsp.html). Produced are bo th:
   1) modems identifiable from their primary PCI IDs and
   2) soft modem Subystem chips requiring identification through codec readouts.

 Call waiting specified by, +pcw=1, is not implmented in the ltmodem drivers.
Configuration with forcing is described in: [http://linmodems.technion.ac.il/arch](http://linmodems.technion.ac.il/arch) ive-fifth/msg00055.html
 0x044c -- Mars 3 Perseus data/fax only:North America and Global board
 0x044c -- Mars 3.2 Mercury data fax only when no eeprom is present, North Ameri ca DAA


 Add either of the following lines to the Debian  /etc/apt/sources.list
 to enable automatic updates on installer availability:
   deb [http://www.physcip.uni-stuttgart.de/heby/ltmodem/dists/debian/](http://www.physcip.uni-stuttgart.de/heby/ltmodem/dists/debian/) ./
   deb [http://www.sfu.ca/~cth/ltmodem/dists/debian/](http://www.sfu.ca/~cth/ltmodem/dists/debian/) ./


  The desired installer name is like:
========================================
ltmodem-2.6.8.1-3-386_8.nn_i386.deb
----------------------------------------
 ltmodem-kv-Kernel_FL-LTver--.CPU.rpm   explains the versioning.
 For your System
            Kernel_FL is 2.6.8.1-3-386 , the full kernel version displayed by: u name -r
                      LTver is 8.31a10, the release of the compiler kit
                               8.nn is the Agere core code designation.
       The proccesor type or CPU is:  i686      dispayed by:  uname -m
 used in compiling and assembling driver packages.


 A suitable installer is not available as of this 2005_June_21 update.
 Check in the section debian at  [http://ltmodem.heby.de/](http://ltmodem.heby.de/)
   for a subsequent Installer submission.
 Older releases have been archived at:
   [http://linmodems.technion.ac.il/packages/ltmodem/archive/](http://linmodems.technion.ac.il/packages/ltmodem/archive/)
 Also there is a RPM search engine at:   [http://rpm.pbone.net](http://rpm.pbone.net)
 The closest match to your   i686=CPU   is recommended.
   The closest match to your   i686=CPU   is recommended.
   For example replacements in order of preference for an
     i686 would be i586, i486 and i386
 If not present use the  ltmodem-8.31a10.tar.gz compiler kit.

 The list of available Installers for debian as of this 2005_June_21
 is inserted into to Modem/YourModem.txt
  ======= PCI_ID checking completed ======
 Update=2005_June_21
A PCMCIA CardBus is not detected on this System.
GCCversion=none

For information on modem port creation under the UDEV device file system see:
   [http://linmodems.technion.ac.il/archive-fourth/msg03299.html](http://linmodems.technion.ac.il/archive-fourth/msg03299.html)  for Conexnant m odems
   [http://linmodems.technion.ac.il/archive-fifth/msg01177.html](http://linmodems.technion.ac.il/archive-fifth/msg01177.html)  for Lucent/Agere  DSP modems

The following information blocks just query some ppp support items.

====================================================
   grep -rs ppp /etc/modprobe.*
-------------------------------------
/etc/modprobe.d/aliases:alias net-pf-24 pppoe
/etc/modprobe.d/aliases:alias char-major-108 ppp_generic
/etc/modprobe.d/aliases:alias tty-ldisc-3  ppp_async
/etc/modprobe.d/aliases:alias tty-ldisc-14 ppp_synctty
/etc/modprobe.d/aliases:alias ppp-compress-18 ppp_mppe
/etc/modprobe.d/aliases:alias ppp-compress-21 bsd_comp
/etc/modprobe.d/aliases:alias ppp-compress-24 ppp_deflate
/etc/modprobe.d/aliases:alias ppp-compress-26 ppp_deflate
-------------------------------------
 Resident PPP support modules are properly uncompressed .
 COMM services are not active
Be sure to read the section about ppp related modules and aliases in Modem/YourM odem.txt
DEVPPP=crw-rw---- 1 root root 108, 0 2005-06-22 15:39 /dev/ppp
A /dev/modem symbolic link is not present

 No devfsd.conf file found, indicated absense of the devfsd daemon package
 for device file system (devfs) symbolic link support.

DEVFSD=
 ---- dmesg queries -------
  debian is not yet providing pre-compiled drivers for WinModems

rob@ubuntu:~/Desktop/Modem $

---

### Post by az on 2005-06-22
Oops.  You have a lucent modem:
[https://wiki.ubuntu.com/forum/hardware/lucent](https://wiki.ubuntu.com/forum/hardware/lucent)

---

### Post by CoriolisSTORM on 2005-06-22
What the heck?  Can someone put that all in English or maybe in a guide format?  I rebooted to try it, and all i did was succeed in confusing myself.

---

### Post by az on 2005-06-22
[QUOTE=CoriolisSTORM]What the heck?  Can someone put that all in English or maybe in a guide format?  I rebooted to try it, and all i did was succeed in confusing myself.[/QUOTE]


It is awful, isn't it?  I just read it again and I see your point...


Try:
sudo modprobe lt_serial 
sudo modprobe lt_modem

You should then be able to use your modem as /dev/ttLTM0

They other crap there is if you want to use KPPP as your dialing program...

---

### Post by CoriolisSTORM on 2005-06-22
Uhoh, azz, I think this might be a problem on my account here.  it is ubuntu 4.10.  I got the error upon running those commands:

rob@ubuntu:~ $ sudo modprobe lt_serial
FATAL: Module lt_serial not found.
rob@ubuntu:~ $ sudo modprobe lt_modem
FATAL: Module lt_modem not found.
rob@ubuntu:~ $

---

### Post by az on 2005-06-22
Correct!  Those modules are only in Hoary.  You can compile them yourself, if you have a way of getting a file onto your Ubuntu system (like a usb pen drive)

Another thing you can do, if you can get a copy of Hoary is just use the Hoary kernel.



1- (Warty)[http://www.sfu.ca/~cth/ltmodem/ltmodem-8.31a10.tar.gz](http://www.sfu.ca/~cth/ltmodem/ltmodem-8.31a10.tar.gz)
Install build-essential and linux-headers-2.6.8-1-386 (from the Warty install cd)

copy the file from above into a directory and open a terminal there.

tar xvzf ltmodem*
cd ltmodem*
( I am not at home, so the build procedure is fuzzy - sorry.  It is detailed in the readme and is quite straightforward.  Should take you a minute or two)

2-  (Hoary) insert your Hoary cd into your cdrom and do (from a terminal)
sudo apt-cdrom add
sudo apt-get update
sudo apt-get dist-upgrade

When all the dust settles, you should have a Hoary system.  I know you may not have access to the Hoary cd (or you would have already installed it!) but this is a much more elegant solution than compiling the module yourself.   If you ever update your kernel, you will have to compile it all over again....   this is not the case with the precompiled modules in Hoary...

---

### Post by mtron on 2005-06-22
did you install the restricted modules for your kernel?

---

### Post by CoriolisSTORM on 2005-06-22
aw no, I just ordered my Hoary CDs today, and well dont really have a way to download the entire update.  How would I go about compiling it myself? (I figure I still have a few weeks at the least to wait on the CDs.)  The computer has 'net access as it is what I'm on now, I just have to reboot to get back on here to fix it, and I save the directions to a FAT32 directory to read and write to.
Uh, nevermind.  I just reread your post.  We'll see if this does it.
And no, as far as I know I did not install the restricted modules for it.  Do I need to?

EDIT: I just checked my device manager in windows and under linux, and it detects my modem as an Agere Winmodem.  The package I just downloaded says it will not work with them.   I might try it anyway to see if it works.

---

### Post by CoriolisSTORM on 2005-06-23
How do I install the restricted modules?  I have them on my desktop, and did apt-get, but that doesen't work.  What do I do?  Okay, and finally, I have an Agere Modem actually.  It just detects it as a Lucent modem.  Will it make any difference?  I figured it probably uses a Lucent chipset.

---

### Post by CoriolisSTORM on 2005-06-24
Any ideas?

---

### Post by az on 2005-06-24
The restricted modules in Hoary has the drivers you need, but not the restricted modules from Warty.  Forget about it.

You can only get it working by compiling from source.  Did you try that?

---

### Post by CoriolisSTORM on 2005-06-24
How do i go about that?  I'm so confused.  I'm sorry I'm making this so hard.
Are you talking about doing this?:

> 1- (Warty)[http://www.sfu.ca/~cth/ltmodem/ltmodem-8.31a10.tar.gz](http://www.sfu.ca/~cth/ltmodem/ltmodem-8.31a10.tar.gz)
Install build-essential and linux-headers-2.6.8-1-386 (from the Warty install cd)

copy the file from above into a directory and open a terminal there.

tar xvzf ltmodem*
cd ltmodem*
( I am not at home, so the build procedure is fuzzy - sorry. It is detailed in the readme and is quite straightforward. Should take you a minute or two)

---

### Post by CoriolisSTORM on 2005-06-26
Well, I compiled it and tried that, but modem lights will not connect.  When I use $modprobe lt_serial to get the serial and everything like the thing suggests after installing it, it says the module can not be found.  However, I installed both modules suggested.  What now?  Do I not have modem lights configured correctly, or do I need to do something else?
here's what part of the installer says:
> The modem has a supported Lucent/Agere DSP (digital signal processing) chipset
  with primary PCI_ID:  11c1:044c
 DSP=1
grep: /etc/modprobe.conf: No such file or directory
grep: /etc/modprobe.conf: No such file or directory


To continue:    Enter
==================================================

Checking for any preliminary complications.
The kernel supports only single processor motherboards.

To continue:    Enter
==================================================

OK thus far.
To begin acquisition of compiling information:  Enter

Removing old makings and expanding a clean source.tar.gz
Setting BLDrecord.txt link within source/ folder.
lrwxrwxrwx    1 root     root           16 2005-06-26 13:18 BLDrecord.txt -> ../BLDrecord.txt
Setting ./tmpfile link within source/ folder.
lrwxrwxrwx    1 root     root           12 2005-06-26 13:18 ./tmpfile -> .././tmpfile
Following a successful check for matching kernel-headers,
the modem drivers will be compiled for the current kernel version: 2.6.8.1-3-386To start resource tests:        Enter

Performing a configure trial and capturing the report to ../conf-report.txt.
Parsing the report:
error
A sample successfull conf_out.txt is in the folder DOCs/
Basic utilities required for compiling have not been installed on your System.
Read in DOCs/ ForNewbies, Compile-Properly.txt and Flavor.txt

ls: /usr/src/linux: No such file or directory
Here is the report from ../conf-report.txt
------------------
creating cache ./config.cache
Checking OS
Checking machine type
Processor i686 is supported.
checking for gcc... no
checking for cc... no
configure: error: no acceptable cc found in $PATH

------------------

Read instructions at the end of BLDrecord.txt

rob@ubuntu:~/Desktop/ltmodem-8.31a10 $


-----------BLDrecord.txt----------------------

 Together with information included in DOCs/
 this report may enable you to solve problems.
 But if further help is needed, send BLDrecord.txt to [email]discuss@linmodems.org[/email]
 Please use the following in the email Subject Line:
   SUBJECT=Lucent modem, debian testing/unstable 2.6.8.1-3-386
  
 DISTRO=debian_version 
 DISTR=debian
 DVERSION=testing/unstable
 ACTION="./build_module     
 WHOAMI=root
 TARGET_CPU=i686
 Sun Jun 26 13:18:24 CDT 2005 
 Linux ubuntu 2.6.8.1-3-386 #1 Tue Oct 12 12:41:57 BST 2004 i686 GNU/Linux
 

------------ beginning SCANMODEM section ------
 assembled with compiler:  3.3.4
 no gcc compiler installed
 A /dev/modem symbolic link is not set.
Path to lspci is: /usr/bin/lspci
--------- lspci scan ----------------
 PCI_bus
0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev a2)
0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev a2)
0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)
0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)
0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)
0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)
0000:00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
0000:00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
0000:00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
0000:00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
0000:00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
0000:00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394) Controller (rev a3)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2)
0000:01:08.0 Communication controller: Lucent Microelectronics LT WinModem (rev 02)
0000:02:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX - nForce GPU] (rev a3)
-------------------------------------

Modem candidates are at PCI_buses:  0000:01:08.0
    
Providing detail for device at PCI_bus 0000:01:08.0
  with vendor-ID:device-ID
	    ----:----
Class 0780: 11c1:044c   Communication controller: Lucent Microelectronics LT WinModem (rev 02)
  SubSystem 11c1:044c   Lucent Microelectronics LT WinModem
	Flags: bus master, medium devsel, latency 64, IRQ 209
	Memory at fb800000 (32-bit, non-prefetchable)
	I/O ports at dc00 [size=8]
  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 11c1:044c 11c1:044c debian 2.6.8.1-3-386 3.3.4     i686

 == Checking PCI IDs through modem chip suppliers ==

 The modem has a supported Lucent/Agere DSP (digital signal processing) chipset
  with primary PCI_ID:  11c1:044c
 DSP=1

 Vendor 11c1 corresponds to Lucent Technologies or subsidiary Agere Systems, Inc.
 Information is at:  [http://www.agere.com/client/modem_dsp.html](http://www.agere.com/client/modem_dsp.html). Produced are both:
   1) modems identifiable from their primary PCI IDs and 
   2) soft modem Subystem chips requiring identification through codec readouts.
 
 Call waiting specified by, +pcw=1, is not implmented in the ltmodem drivers.

 Support has been extended to 2.6.n kernels by Rajesh K. Balan and
 Aleksey Kondratenko <alk@tut.by>, with official support from AgereSystems later following.
 Functionalirt requires serial_core support, either as a module or integral to the kernel.
 The resources are [http://ltmodem.heby.de](http://ltmodem.heby.de) are more automated and can utilize kernel-headers.
 The ltmodem-2.6-alk-6.tar.bz2 is a leaner package and can be downloaded from:
   [http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/) 
   with low bandwidth alternate: [http://alk.at.tut.by/ltmodem-2.6-alk-6.tar.bz2](http://alk.at.tut.by/ltmodem-2.6-alk-6.tar.bz2)
   A full kernel-source configuration is required, or the kernel-headers as provided with fedora 2. 


 Drivers compiled with ltmodem-2.6-alk-6.tar.bz2 have been effective with Mandrake 10
 kernel versions 2.6.8.1-* . See within [http://linmodems.technion.ac.il/packages/ltmodem/](http://linmodems.technion.ac.il/packages/ltmodem/)
 ltmodem-2.6.8.1-10mdk.tar.gz  
  


 Add either of the following lines to the Debian  /etc/apt/sources.list
 to enable automatic updates on installer availability:
   deb [http://www.physcip.uni-stuttgart.de/heby/ltmodem/dists/debian/](http://www.physcip.uni-stuttgart.de/heby/ltmodem/dists/debian/) ./
   deb [http://www.sfu.ca/~cth/ltmodem/dists/debian/](http://www.sfu.ca/~cth/ltmodem/dists/debian/) ./


  The desired installer name is like:
========================================
ltmodem-2.6.8.1-3-386_8.nn_i386.deb
----------------------------------------
 ltmodem-kv-Kernel_FL-LTver--.CPU.rpm   explains the versioning.
 For your System
            Kernel_FL is 2.6.8.1-3-386 , the full kernel version displayed by: uname -r
                      LTver is 8.31a9, the release of the compiler kit
                               8.nn is the Agere core code designation.
       The proccesor type or CPU is:  i686      dispayed by:  uname -m
 used in compiling and assembling driver packages.

 A suitable installer is not available as of this 2004_Nov_26 update.
 Check in the section debian at  [http://ltmodem.heby.de/](http://ltmodem.heby.de/)
   for a subsequent Installer submission.
 Older releases have been archived at:
   [http://linmodems.technion.ac.il/packages/ltmodem/archive/](http://linmodems.technion.ac.il/packages/ltmodem/archive/)
 Also there is a RPM search engine at:   [http://rpm.pbone.net](http://rpm.pbone.net)
 The closest match to your   i686=CPU   is recommended.
   The closest match to your   i686=CPU   is recommended.
   For example replacements in order of preference for an
     i686 would be i586, i486 and i386
 If not present use the  ltmodem-8.31a9.tar.gz compiler kit.

 The list of available Installers for debian as of this 2004_Nov_26
 is inserted into to /dev/null
  ======= PCI_ID checking completed ====== 
 Update=2004_Nov_26
A PCMCIA CardBus is not detected on this System.
GCCversion=
The following information blocks just query some ppp support items.

====================================================
   grep ppp /etc/modprobe.conf
-------------------------------------

-------------------------------------
 Resident PPP support modules are properly uncompressed .
 COMM services are not active
Be sure to read the section about ppp related modules and aliases in /dev/null

  A port needed for the PPP protocol is absent!!!
  echo "  crw-------    1 root     root     108,   0 Dec 31  1969 /dev/ppp"

A /dev/modem symbolic link is not present

 No devfsd.conf file found, indicated absense of the devfsd daemon package
 for device file system (devfs) symbolic link support.

DEVFSD=
 ---- dmesg queries -------
ACPI: PCI Interrupt Link [LNKA] (IRQs 16) *0, disabled.
ACPI: PCI Interrupt Link [LNKB] (IRQs 18) *0, disabled.
ACPI: PCI Interrupt Link [LNKC] (IRQs 18) *0, disabled.
ACPI: PCI Interrupt Link [LNKD] (IRQs 19) *0, disabled.
ACPI: PCI Interrupt Link [LAPU] (IRQs 20 21 22) *0, disabled.
ACPI: PCI Interrupt Link [LKMO] (IRQs 20 21 22) *0, disabled.
ACPI: PCI Interrupt Link [LETH] (IRQs 20 21 22) *0, disabled.
  debian is not yet providing pre-compiled drivers for WinModems

 No false /usr/include/  symbolic link
BASE=source
# ===SETTINGS===
LT_SERIAL_MODULE="lt_serial"
LT_PROPRIETARY_MODULE="lt_modem"
DOCS="1ST-READ CHANGELOG UPDATES-BUGS DOCs utils"
LT_VERSION="8.31a10"
CPU="i686"
KPKG="kernel"

FV=
Read in DOCs/ ForNewbies, Compile-Properly.txt and Flavor.txt
Properly configuring your sources may be aided by:	 utils/ksp.sh

---

### Post by CoriolisSTORM on 2005-06-26
Well, I got past that, and got it to install and everything.  Now i get this.


> rob@ubuntu:~ $ sudo pon
/usr/sbin/pppd: In file /etc/ppp/peers/provider: unrecognized option '/dev/modem'

and this:
----------------

> rob@ubuntu:~ $ sudo tail -f /var/log/messages
Jun 26 14:44:29 localhost kernel: ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[ 201]  MMIO=[fe500000-fe5007ff]  Max Packet=[2048]
Jun 26 14:44:29 localhost kernel: ACPI: Power Button (FF) [PWRF]
Jun 26 14:44:32 localhost kernel: NET: Registered protocol family 10
Jun 26 14:44:32 localhost kernel: Disabled Privacy Extensions on device c02cc0c0 (lo)
Jun 26 14:44:32 localhost kernel: IPv6 over IPv4 tunneling driver
Jun 26 14:44:57 localhost gconfd (rob-4658): starting (version 2.8.1), pid 4658 user 'rob'
Jun 26 14:44:57 localhost gconfd (rob-4658): Resolved address "xml:readonly:/etc /gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jun 26 14:44:57 localhost gconfd (rob-4658): Resolved address "xml:readwrite:/ho me/rob/.gconf" to a writable configuration source at position 1
Jun 26 14:44:57 localhost gconfd (rob-4658): Resolved address "xml:readonly:/etc /gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jun 26 14:45:10 localhost gconfd (rob-4658): Resolved address "xml:readwrite:/ho me/rob/.gconf" to a writable configuration source at position 0




---

### Post by az on 2005-06-26
When you do pppconfig, you must tell it to use the proper modem device.  Do not forget to save.  Use "provider" as the connection name.

/dev/ttLT0
(I think...  Double check to be sure on the device name...)

---

### Post by CoriolisSTORM on 2005-07-04
Well, I havent had time to get out and buy a USB modem yet, so I checked up on my winmodem.  It is set as COM3 in Windows, so in Ubuntu that would be /dev/ttLT2 right?  So I need to set it as such and set up a connection as /dev/ttLT2 right?  And while looking at my install file, it says something about a .k file not installing right.  Should I be worried?  I'll get the exact error when I reboot again.

---

### Post by ShaneR on 2005-07-04
Well, I can't help you with most of what you ask.

But, I can explain the /dev/tty** deal.  After you modprobe lt_serial and lt_modem, type dmesg at the prompt.  One of the last lines will show you were the device was dtected.  It is most likely /dev/ttLTM0 (it is in mine).  Use that as the device location and you should be fine.

I can get mine to dial out now, just not connect.  One step at a time..lol

---


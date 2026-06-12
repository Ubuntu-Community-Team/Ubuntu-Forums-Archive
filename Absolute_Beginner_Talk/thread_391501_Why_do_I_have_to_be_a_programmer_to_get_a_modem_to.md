---
title: "Why do I have to be a programmer to get a modem to work on Ubuntu?"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by linuxjerk on 2007-03-23
Why do I need to be a programmer to get my modem driver to work on ubuntu? I have the driver for my modem but you have to be a programmer to figure out how to attach it to ubuntu.
I realize my mother board is antique junk but it should be able to work with ubuntu if windows XP has no problem.

My install is Ubuntu Edgy 6.10. The mother board is pcchips m748lmrt.

I ran the scanmodem program and I'll include some info from that below.

Also below that is some compiling information. Maybe someone can help me out
with trying to make some sense of this stuff.
Thanks in advance 

```
*************************************************************************

Only plain text email is forwarded by the  [email]DISCUSS@linmodems.org[/email] List Server.
 Do use the following as the email Subject Line:
           SomeName, YourCountry Ubuntu 6.10  kernel 2.6.17-10-generic 
 This will alert cogent experts, and  distinguish cases in the Archives.
 YourCountry will enable Country Code guidance.
 Occassionally responses are blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) .
 Local Linux experts can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html)
--------------------------  System information ----------------------------
CPU=i686,  Ubuntu 6.10 
Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
 scanModem update of:  2007_March_15


USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:0f.1	13f6:0211	13f6:0211	Communication controller: C-Media Electronics Inc CM8738 

 Modem interrupt assignment and sharing: 

 --- Bootup diagnositcs for card in PCI slot 00:0f.1 ----

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

 For candidate modem in PCI bus:  00:0f.1
   Class 0780: 13f6:0211 Communication controller: C-Media Electronics Inc CM8738
      Primary PCI_id  13f6:0211
 Support type needed or chipset:	PCTEL
 

    At [http://linmodems.technion.ac.il/pctel-linux](http://linmodems.technion.ac.il/pctel-linux)
 Get the pctel-0.9.7-9-rht-7.tar.gz
 Unpack under Linux with:
    tar zxf pctel*.tar.gz
 and read instuctions therein.
  Read Pctel.txt and Modem/YourSystem.txt for follow through guidance.

 Writing Pctel.txt

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.1.2
             and the compiler used in kernel assembly: 4.1.2


 
 Compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.1
   kernel_headers base folder /lib/modules/2.6.17-10-generic/build


Checking pppd properties:
	-rwsr-xr-- 1 root dip 260920 2006-07-10 15:13 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    [http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html](http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html)

To enable dialout without Root permission do:
	$ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
	sudo chmod a+x /usr/sbin/pppd

Checking settings of:	/etc/ppp/options
asyncmap 0
auth
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
/etc/udev/rules.d/60-symlinks.rules:# Create /dev/modem symlink
/etc/udev/rules.d/60-symlinks.rules:KERNEL=="ttyLTM[0-9]*",			SYMLINK+="modem"
     Within /etc/modprobe.conf files:
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------

**************************************************************************

COMPILING INFORMATION:

**************************************************************************


 =======================================================
          COMPILING DRIVERS, for Linux Newbies
	  
Within the workshop there is an instruction set, the Makefile, and a few tools.   You command:
	make clean
An elf named "make" comes in, reads Makefile and then cleans up any debris of previous efforts.  
Do ALWAYS command "make clean" as a first step before new driver compilations.
The major work of compiling drivers and any associated tools is commanded with:
	make  
or perhaps  
       make DriverName
There only remains to command installation of the modem driver(s) and tools with:
 	make install
Configuration of a dialout utility is done elsewhere, and you can access the Internet.

It is really that simple, once the workshop with tools has been prepared.
But new drivers have to be compiled with every operaing system update.
The remainder of this text is thus aids you in the preparations, dealing with a variety of special cases.
Most  points are covered in much more detail in the Linux Kernel-HOWTO, likely included among the
HOWTO documentation set installed within /usr/share/doc/ folders.

The core operating system of a PC is comprised of a motherboard, the software kernel, 
and its auxilliary code modules.  The kernel is the file  /boot/vmlinuz-2.6.17-10-generic. 
Modules located in subfolders of /lib/modules/2.6.17-10-generic/  .  They can be inserted into or removed 
from the acting kernel upon demand. This provides adaptablity to the diverse 
hardware components of PCs and changing requirments. 

Modem drivers are one type of module.  As contrasted to most Linux software, modem driver codes have
some non-public code components. That is the drivers are not fully Open Source, to protect 
Intellectual Property of the providing companies.   This has a consequence that many Linux distributions
will not or cannot legally  supply proprietary  modem drivers.  Rather the Users must get the 
modem code package and direct  compiling of the code and driver installation.

A complementary resource for compiling is a family of FileNames.h, collectively called kernel-headers.
They are both code bits themselves and also call for other code bits their functioning depends on.
Depending on the Linux distribution, kernel-headers may not be automatically installed.
If not they will always be made available on installation media or some Linux repository.
They can be searched for by package names including:  kernel-source, linux-source, kernel-headers and 44
There are always some kernel-headers in afolder /usr/include/.   But these are an INCOMPLETE, too small collection 
and DO NOT suffice for compiling processes.

In addition some software utilities may have to be installed.  The instructions for compiling are read by make.
A set of compiler tools are installed as a  gcc-SomeVersion package.  After compiling, the various pieces 
and linked dynamically together with "ld". Together wiith some simpler software tools, the ld will 
already be installed on Linux systems.  Systems using the Debian style maintanence system
additionally require a package "kernel-kbuild-3.n" to properly utilize kernel-headers or 2.6.n kernels.

The  "kernel-headers" are matched with an installed kernel, or must be generated from a kernel-source package. 
These are provided in different ways by the various Linux distributions, under 2.6.n kernels:
     Redhat and Fedora - installation is coincident with kernel installation, 
         with placement of the kernel-header base folder in /lib/modules/2.6.17-10-generic/build/
    Mandrake and SuSE/Novell - installation as part of a kernel-source or linux-source  packages,
         with location at /usr/src/kernel-headers-2.6.17-10-generic  or /usr/src/linux-2.6.17-10-generic 
    Debian and distros using its Package.deb format have names:
          kernel-headers-2.6.17-10-generic
	  linux-headers-2.6.17-10-generic  for Ubuntu
	  and installation is into  /usr/src/
	  for Xandros, there is a xandros-kernel-source-version.deb  which has to be installed
	      Unpack if necessary with 
	         # cd /usr/src/
		 # ls
	         # tar jxf xandros-kernel-source-version.tar.bz2
	      see   [http://support.xandros.com/kb-view.php?topic=64](http://support.xandros.com/kb-view.php?topic=64)  for details
	         but for 2.6.n kernels, the step after:
		 # make EXTRAVERSION=-x1 oldconfig
	         should be
		 # make EXTRAVERSION=-x1 bzImage
    Others - ???

For  the prior generation of 2.4.n kernels, there are special cases.  Skip this if your kernel is a 2.6.n or a Debian type.
For RPM using distros, the kernel-source-2.6.17-10-generic or linux-source-2.6.17-10-generic packages must be installed and configured as described below:
 1) SuSE with KernelVersion 2.4.21-144-* or later - install the matching kernel-source package, which does also contain the kernel-headers;
2) for Fedora II or later, kernel-headers are/were coinstalled with the kernel package;
3) for all other cases of 2.4.n kernels, the kernel-headers must be prepared from kernel-source.      
  The preparation can be summarised in a few steps/actions:
  Install a kernel-source package representing your kernel.
  Change directory (cd) into its base folder. The kernel-source in general
  will match only one of several kernels that could have been installed
  and NOT necessarily yours. Thus clean out any remnants of earlier usages with:
  	make mrproper
  Copy in your kernel configuration file and have it read with:
	make oldconfig
  If necessary edit ONLY the fourth line of the Makefile, which completes
  the specification of where drivers will be installed to (details below).
  The kernel-headers are then assembelled by either: 
  a) for 2.4.nn kernels by
	make dep
  b) for 2.6.n kernels,
        make bzImage
which includes an integral "make dep" step. 

Modem related resources may or may not have been installed during the primary Linux installation,
as WinModem hardware is often NOT recognized.  Search your Distro's package
descriptions for "modem" to reveal the status of related resources.  Read
the package description to determine whether pre-compiled modem drivers were provided.
RESOURCES of a few types are needed to get on line. Do PREFERABLE use your System's
package maintenance system for the installation. This should guarantee that
any DEPENDENT packages will be called into the installation process. As a preliminary
1) Install your distributions package providing the KPPP, WVDIAL and MINICOM dialer utilities.
Dependencies within such packages will also drive the unpacking of ppp related modules
from compressed to a functional form :
   module.o.gz --> modules.o
or for 2.6.n kernels
   module.ko.gz --> module.ko
In addition these dialers will later aid testing and configuration,
which is to be performed only AFTER, the modem's drivers are installed.

2) Download if necessary and modem driver package specific to your modem hardware.
3a) Install if necessary your distrbution's kernel-source package, necessary for preparing kernel-headers under 2.4.n kernels
Or for Debian style distributions,
3b) install the kernel-header-2.6.17-10-generic.deb package matching your kernel version 2.6.17-10-generic.

A KERNEL-SOURCE package must be installed, if a full kernel-header set
is not otherwise provided. Kernel-source packages are now some 30-40 MB now even in compressed form.
The package provided by your Linux Distro SHOULD preferentially be used.
It will usually have some differences from that initially released at [http://www.kernel.org](http://www.kernel.org) .
Typically the installation process will set two symbolic links:
  /lib/modules/2.6.17-10-generic/build -->  PATH_to/kernel-source-version/
  /usr/src/linux --> PATH_to/kernel-source-version/
These later enable access to the kernel-headers needed during the modem driver compiling. Check with:
  ls -l /lib/modules/2.6.17-10-generic/build
  ls -l /usr/src/linux
The former link is more usefull for Systems with alternative boot kernels,
and is mandatory for some modem compiler packages.

HIGHLY IMPORTANT: the kernel-source as installed in generally does NOT
represent your current kernel version, EVEN if the kernel-version is the same.
Only one of several possible kernels was installed on your System,
and the unpacked kernel-source need NOT represent it exactly!!!
For example, in the RedHat Distro there is a set of kernel-configuration files within
   /usr/src/linux/configs/
Each is specialized for a different CPU (i586, i686, K6, etc),
Yet each will be represented by the VERY SAME version name: "uname -r" .
!!!! Thus a PROPER CONFIGURATION MUST BE DONE by You, before compiling drivers !!!!

Examples provided below are partially customized from your System settings.
CONFIGURATION is started by moving into the kernel-source folder with one of:
  cd  /lib/modules/2.6.17-10-generic/build
  cd /usr/src/linux

 There is a Makefile on your System at:  /lib/modules/2.6.17-10-generic/build/Makefile
 with first few lines:

VERSION = 2
PATCHLEVEL = 6
SUBLEVEL = 17
EXTRAVERSION=-10-generic
NAME=Crazed Snow-Weasel

ifdef UBUNTUBUILD

For your current kernel, the fourth line should be
   EXTRAVERSION = 
where  has been read from your current kernel version: 2.6.17-10-generic.
But it this does not match what is Actually in the Makefile,
then it represents a Different kernel-header set then that of your kernel!!!

For Mandrake Linux their will generally be an included "mdk", such as:
 EXTRAVERSION = -3.1mdk
SuSE 9.0 had:
 EXTRAVERSION = -99-default
The first four makefile lines specify that:
a)  the compiled kernel modules/drivers will have encoded version labels such as:
   2.4.21-3.1mkd  OR   2.4.21-99-default
b)  such modules including modem drivers are installed into sub-folders of
   /lib/modules/2.4.21-3.1mkd/
   /lib/modules/2.4.21-99-default/
The major points are that compiled drivers must be both
kernel-release (the 2.4.21) AND EXTRAVERSION matched with the installed kernel.
Otherwise they may be installed uselessly and not be detected by the kernel
OR there will be a failure upon attempted insertion, with message including:
  a list of "unresolved symbols ".

Kernel-headers may be resident from a prior usage of the kernel-source/.
Check with:
  ls include/linux/
which may display abundant FileNames.h
The version of these headers will be in the UTS line displayed by
  cat include/linux/version.h
     #define UTS_RELEASE "2.4.21-3.1mdk" (as an example)

Next, list completely the contents of the kernel-source  with:
  ls -a
Where the " -a " additionally reveals ".dot-prefixed-confguration-files" such as
    .config  .hdepend .depends
which may be left over from the prior usage of the kernel-source. Below is an example:
 -------------------
    .config  .hdepend .depends
COPYING        Makefile        Rules.make    init    mm
CREDITS        README          arch        drivers  ipc     net
Documentation    conf.vars   fs       kernel  scripts
MAINTAINERS    REPORTING-BUGS  crypto      include  lib

Configuration of the kernel-source is where almost all the Mistakes occur!!!
Here is a way to do it correctly (but read through EXCEPTIONAL CASES below).
1)Within kernel-source/ folder, browse the README file for general guidance.
It will relate that the command:
#    make mrproper
cleans up leftovers from any previous usage .dot-files and the include/linux/ folder.
Additionally you may need to do an edit within Makefile, but ONLY that 4th line.
2) If necessary to edit, FIRST make a backup:
  cp Makefile Makefile.backup
then edit ONLY the 4th line of Makefile to match the EXTRAVERSION of 2.6.17-10-generic
   EXTRAVERSION = -
NEVER change anything else within the Makefile.

3) Set the dependencies of the current kernel.
For SuSE 9.0 and later, there is a command which does the following steps
   #  make cloneconfig && make dep
   Also browse the excellent README.SuSE in the kernel-source/ folder
For other Distros, the following steps are necessary, within the kernel-source/ folder
  copy the kernel-config file to  .config
          and DO SPECIFY that " . "
But where is it? For many Distros, it will be the file like
   /boot/config-2.6.17-10-generic
matching the output of:
  uname -r
Or it may be the target of a symbolic link:  /boot/config -->
So
  cp /boot/config-2.6.17-10-generic .config
For SuSE 8.0 and earlier versions it is:
  cp /boot/vmlinuz.config  .config
PLEASE do not omit that "." in  .config as it is crucially necessary.
View .config with a text browser.
It is simply a listing of the code components used in the kernel and its modules:
  #
  # Automatically generated make config: don't edit
  #
  CONFIG_X86=y
  # CONFIG_SBUS is not set
  CONFIG_UID16=y
etc.

4) The  .config file will be read during
#  make oldconfig
which feeds its specifications through a process specifying
the SAME inter-dependencies previously used in compiling your kernel,
and may generate additional .dot-config files . They can be displayed with:
#   ls -al

5) Though it may be redundant after "make mrproper", it will do no harm to:
   make clean
5a) For the SuSe Linux versions 8.0 and previous , there will exist files:
  /boot/vmlinuz.autoconf.h
  /boot/vmlinuz.version.h
They MUST be copied as:
  cp /boot/vmlinuz.autoconf.h  /usr/src/linux/include/linux/autoconf.h
  cp /boot/vmlinuz.version.h    /usr/src/linux/include/linux/version.h

6) Now build kernel-headers with:
	make dep
for 2.4.n kernels or for 2.6.n kernels
	make bzImage 
during which you can walk your dog, take a shower, have tea, etc.
7) Check for resultant FileNames.h with:
	ls  include/linux/
and
	cat include/linux/version.h
to verify the version.

COMPILING the MODEM DRIVERS can now finally be done.
Unpack the compiler kit for your modem drivers,
cd into its folder, read any README or INSTALL files,
   make clean
FINALLY, your modem drivers will compiled by a command like
   make OR  make ModuleName
or perhaps
   make all
During this process, some of the kernel-header code with be joined
with the supplied modem specific code, and ModemDrivers.o will be produced.
Follow and further instructions in the modem code resource
to install the drivers, often with:
   make install

		THEORETICAL ISSUES	

WinModem driver packages commonly include:
1) a readible Open Source component, which can be readily debugged by
experts in code. This component provides "wrappers" to common
kernel functions for an already complied, or BINARY format, component of the modem code.

2) A Closed Source component compiled into the binary form, in which
proprietary information is encrypted. This will include the copyrighted Vn.nn compression algorithms.
In 2004, pre-compiled modem drivers are beginning to be included
for a few winmodems by some Linux distributions.
But the binary format precludes incorporation of the modem drivers in some Linux distributions
for legal reasons, practical reasons, and/or reasons of principle.

Since almost all the newer PCs are now equipped with WinModems,
many users will have to compile their own linux modem drivers.
Exceptions are the more expensive modems with Controller chipsets,
characteristic of the earliest modems.
They are supported by Open Source serial code included in Linux
distributions (Distros hereafter).

Winmodems are less expensive because of greatly reduced hardware costs.
They lack Controller chips of the earliest modems, and may additionally lack Digital Signal Processor (DSP) chips of second generation modems.
Functions of Controller based chipsets are replaced by a combination of 
software code and/or other System hardware.

Modems without a controller chip are referred to as "controllerless modems" and
modems lacking both a DSP and controller chips are referred to as "soft modems".
With faster central processor units (CPU), some processing tasks are performed
by the CPU for the controllerless modems. The CPU does nearly all
the signal processing for the "soft modems" lacking a DSP. 

AC97 or MC97 soft modems conform to an ac97_codec, and can host a variety of Subsystems It is the CODEC of the Subsystem which determines which software should be utilized!! 
and any modem controllers can host one of a variety of soft modem Subsystems.
There are additionally soft PCI modems without such controllers, which still utilize
the common ac97_modem.o driver. In general it will be YOUR task to identify
the Subsystem codec and compile the needed driver.
   
## end Modem/DriverCompiling.txt
```

---

### Post by lyceum on 2007-03-23
That is a lot of info, and will admit that I did not real all of it. Here is the thing, I am not a programer in any way and I use Ubuntu as my main PC. It runs with a 160 gig hard drive, pentium 4 processor almost a gig of ram and a nice ATI video card. The thing about Linux vs XP is that not all hard ware works for Linux. If the makers of the hardware will not give the code to the Linux develpoers, it will not work. There are programs that try to fix that, but they can take time. Also, installing things in Ubuntu or any Linux OS. 

You may want to check out the links in the first line of my signature before going any farther. Psycocat's Ubuntu page is great, and how to install anything may really help you here.

Good luck.

-edit-

Forgot to mention that the next Ubuntu, 7.04 due out next month, will have better dial-up support.

---

### Post by justleen on 2007-03-23
ehm.. since 1996 im on Cable/DSL connection, so im not very familiair with modems.. but if i read your post, it actually gives you step-by-step how to?

Yes, i agree, its not plug and pray like windows, but as said, some hardware is not very well supported and requires a bit more effort.. (believe you me, i have a tv tuner card, which works like charm in ubuntu, and is a pain in the **** to install on windows :) )

---

### Post by Jason_25 on 2007-03-23
Wow your post was so long I couldn't bear to read it.  If your still using a modem then maybe ubuntu , any linux or any modern OS for that matter is not for you.

Do you understand how long it's going to take to apt-get simple items?  And that the entire concept of installing software in ubuntu is based on downloading it?

Generally, when you run into things like this that tend to take a while and no one can help, it's because it's not a very popular/modern solution.

There are alot of alternatives for broadband today if you can't get DSL/Cable/Fiber.

1.Digital Cellular Internet (EVDO).  I use it always when I'm helping someone that has internet problems.  Configuration time : 1 minute.

2.Satellite.  Not the best solution but infinitely better than dial up.  Configuration time: unknown

3.Public wireless / Commercial Wireless ISP.  Some very wooded remote areas around here have these if they don't have any other infrastructure.  Configuration time: significant?

Good luck with it though.

---

### Post by daxumaming on 2007-03-23
Softmodems really wont work unless you devote a few hours troubleshooting it. Justleen is right, it does contain a step-by-step instructions on how to get it working, but you still need to devote time and effort to make it work. You don't have to be a programmer, but you need to be vigilant with what hardware you buy. Why won't it work? Because the manufacturer of your modem did not intend it to work on any other operating system besides Windows. What can we do about this? Send them an email and either request for support or have them point you to the right direction. It's not Linux fault and it's definitely not our programmers fault. Have you noticed how easy it is to install Ubuntu as compared to Windows?

Oh, and my "Windows Certified" Genius webcam and scanner doesn't work well in Windows but works without a hitch in Ubuntu. And I don't need to install any webcam drivers 'coz it just worked without any configuration on my part! As for my scanner, i only need to download and install 2 sane apps, and it just worked! 

Also, is there anyway we can influence you to use a broadband connection? Easier and much cheaper in the long run as compared to a dial-up connection.

---

### Post by dptxp on 2007-03-23
It will be difficult for you to use UBUNTU with dial-up Modem unless your needs are not much, you do not need much additional to load.
An external modem can be cheaper than expensive, recursive subscription. Depends on your need for net access.

---

### Post by linuxjerk on 2007-03-23
Thanks for all the replies. No I can't get broadband. I'm too far from the tel for dsl and sat is way to expensive.
Believe me I wouldn't be doing this if I didn't have to.
Yes that is a lot of junk!! If it was that straight forward they wouldn't
need all that stuff.
I did try their installation instructions. Here is the error report. Tell me I don't need to be a programmer to figure this out!

desktop:~/Desktop/pctel/pctel-0.9.7-9-rht-7$ ./setup
checking for running kernel version...2.6.17
checking for ptserial...ptserial-2.6.c
checking for gcc...4.1.2
checking for kernel gcc version...4.1.2
searching for kernel includes...found at /lib/modules/2.6.17-10-generic/build/include
checking for autoconf.h.../lib/modules/2.6.17-10-generic/build/include/linux/autoconf.h
checking for asm/mach-default...yes
checking for kernel version in version.h...t.c:1:19: error: stdio.h: No such file or directory
t.c: In function â&#8364;&#732;mainâ&#8364;&#8482;:
t.c:4: warning: incompatible implicit declaration of built-in function â&#8364;&#732;printfâ&#8364;&#8482;
./configure: line 476: ./t: No such file or directory
rm: cannot remove `./t': No such file or directory
** error
could not determine a proper UTS_RELEASE
** compilation error
please read the FAQ about reporting compilation problems
and report this problem.  A transcript of the build process
has been saved in src/make.log.  When reporting problems to
the development team, please send us this file.

---

### Post by aysiu on 2007-03-23
I've retitled the thread to more accurately reflect the situation. You don't have to be a programmer to get Ubuntu working. Most of us Ubuntu users are *not* programmers.

I've also edited the original post so that it doesn't appear as long--all the information is still there, though.

In answer to your question (from Debian's documentation): > 13.4.2 Checking a Modem Connection

Modems are useful for dialup connections to the internet, or for receiving faxes on your system.

Modems are probably the most difficult piece of hardware to work with under Linux. **The problem is that many modems today, especially internal ones, are winmodems. That is, most of them require a running copy of Windows to work.** While a few winmodems have Linux drivers available, these drivers are usually written for a specific kernel, and may not work if you upgrade the kernel.

An external modem or a pcmcia card should generally work. However, research brands on the internet to see if they are Linux compatible before you buy.

To check that Linux recognizes your modem, type dpkg-reconfigure pppconf at the command line. pppconf is a tool for setting up a dialup connection. It starts by detecting the modem, then going on to configure a dialup connection.

If your modem does not respond:

    * Check that it is not a winmodem.

    * Check that it is properly connected to your system and to a live phone jack.

    * To ensure that your system can find the modem, create a symbolic between the serial port to the /dev/modem device. Type : ln -sf / dev/port /dev/modem.

---

### Post by yabbadabbadont on 2007-03-23
```
sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`

```
That should probably get you what you need to build the driver.

---

### Post by moore.bryan on 2007-03-23
[I]i don't know if this is true, but i've been told linux in general is more suited to broadband than dial-up.  i was never able to get my broadcom modem working (even though [linmodems.org]("http://linmodems.org") said it was supported), so i dumped it and got high-speed.
[/I]

---

### Post by andrew_howlett on 2007-03-23
Why do you have to be a programmer to get your modem to work?

Simple,  because your modem manufacturer doesn't support linux.

Some more useful comments:

I build a lot of Ubuntu machines from old components for charities. Every PC must have a modem. I have a four or five useless PTel modems, because only one PCTel modem chip is supported in kernel 2.6. Connexant linux drivers cost $19US each which is out of range of our charity. 

My solution is to use old 33.6 kbps hardware modems. I often find them at the dump.

later,
andrew.

---

### Post by Tomosaur on 2007-03-23
If you're not doing any programming, then you're not a programmer. I see nothing to do with programming in your post.

The reason it is complicated is because the manufacturer sucks, basically. You probably don't want to hear it, but getting Linux up and running is going to be hard work without broadband.

There **is** a solution, though. Get the Ubuntu repository DVDs, which will save you the hassle of downloading programs.

Also, it's probably much less frustrating to go and invest in some hardware which works. Not an ideal solution, but if you want the simplest answer, well there it is.

---

### Post by linuxjerk on 2007-03-23
yabbadabbadont

I got this error message on the second command. Maybe I'm not reading it correct. Are those single quotes?

E: Couldn't find package linux-headers-uname -r

---

### Post by yabbadabbadont on 2007-03-23
> **linuxjerk said:**
> yabbadabbadont

I got this error message on the second command. Maybe I'm not reading it correct. Are those single quotes?

E: Couldn't find package linux-headers-uname -r

They are back-tick marks.  The unshifted tilda key.  If possible, just copy and paste the command.

Edit: If that doesn't work, try this command instead:
```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by ricardisimo on 2007-03-23
Just one thought from me, which is that Edgy is probably not where you want to be if you're also fighting with setting up your modem. Go with one of the stable releases; either load Dapper, or wait a month for Feisty to come out (probably your best bet, since the bundled drivers are going to be much more comprehensive and up-to-date).

I never got my modem to work under Edgy, which was just the kick I needed to get DSL... that, and it actually became cheaper than dialup where I live.

---

### Post by linuxjerk on 2007-03-23
ok now that worked with the back ticks. :) 
Here is the latest terminal text from the comple.
Looks like there is some install error.

desktop:~/Desktop/pctel/pctel-0.9.7-9-rht-7$ ./setup
checking for running kernel version...2.6.17
checking for ptserial...ptserial-2.6.c
checking for gcc...4.1.2
checking for kernel gcc version...4.1.2
searching for kernel includes...found at /lib/modules/2.6.17-10-generic/build/include
checking for autoconf.h.../lib/modules/2.6.17-10-generic/build/include/linux/autoconf.h
checking for asm/mach-default...yes
checking for kernel version in version.h...UTS_RELEASE is 2.6.17-10-generic
checking type of tty_struct.count...int
checking for presence of udev...present (kernel version 2.6.13 or later)
detecting your modem...found. Your modem is a cm8738 type modem.

compilation done
** installation error
please read the FAQ about reporting installation problems
and report this problem.  A transcript of the install process
has been saved in src/make.log.  When reporting problems to
the development team, please send us this file.

---

### Post by yabbadabbadont on 2007-03-23
Ok, it looks like the driver was compiled successfully, but the installation step failed.  This is most likely because your normal user doesn't have permission to copy the driver files to where they need to be.  Run the setup script again, only use sudo to run it this time.
```
sudo ./setup
```

---

### Post by compmodder26 on 2007-03-23
navigate to src/make.log post the contents of that file for us.  I'm going to take a wild guess here, but it seems the command ./setup is just wrapper for the whole ./configure, make, make install process.  If it is, you will need to run ./setup with sudo (e.g. "sudo ./setup").

---

### Post by Ptero-4 on 2007-03-23
or better yet, run sudo make install (since it`s the step that failed, the other two probably worked and you only need to install it.)

---

### Post by linuxjerk on 2007-03-23
Fantastic :guitar:  Wow what a trip!!

Installation successful
Modem detected and initialized.

I still don't know what I'm doing though. I ran wvdial and got a message that
the configuration does no specify a calid phone number, login name, passoword.
I know I set those up in the networking menu. Must be a wvdial conf file.
I don't even know if I need to run wvdial??

Great!!!!!!

---

### Post by yabbadabbadont on 2007-03-23
```
sudo wvdialconf
```
Then answer the questions as best you can.

---

### Post by linuxjerk on 2007-03-23
When I did "sudo wvdialconf" a bunch of setting scrolled by. Didn't ask any questions.
I edited the wvdial.conf file directly.
In the mean time I rebooted the computer. I guess you need to reinstall the modem
driver everytime you boot up?
Well anyway when I ran sudo ./setup this time I got this error: *** error activating modem driver via insmod.
What does this mean?

---

### Post by linuxjerk on 2007-03-23
Here is the latest error. Seems the driver disapeared after rebooting and now I always get this error.

-desktop:~/Desktop/pctel/pctel-0.9.7-9-rht-7$ sudo ./setup
checking for running kernel version...2.6.17
checking for ptserial...ptserial-2.6.c
checking for gcc...4.1.2
checking for kernel gcc version...4.1.2
searching for kernel includes...found at /lib/modules/2.6.17-10-generic/build/include
checking for autoconf.h.../lib/modules/2.6.17-10-generic/build/include/linux/autoconf.h
checking for asm/mach-default...yes
checking for kernel version in version.h...UTS_RELEASE is 2.6.17-10-generic
checking type of tty_struct.count...int
checking for presence of udev...present (kernel version 2.6.13 or later)
detecting your modem...found. Your modem is a cm8738 type modem.

compilation done

installation done
** error activating modem driver via insmod
please read the FAQ about reporting problems and report
this problem.  A transcript of the attempted activation
has been saved in src/make.log.  When reporting problems to
the development team, please send us this file.

---

### Post by linuxjerk on 2007-03-23
I may have been wrong about the driver disapearing with reboot.
Also the error message in the above post may have been telling me it was still installed.
Right now I am having trouble with getting wvdial's conf file. I am editing it with my
phone,password and username info but it doesn't seem to be finding it.
Anyone familiar with the working of wvdial?

---

### Post by linuxjerk on 2007-03-23
Well finaly. This post is actually comming from my linux box with dial up linmodem.
I will probably need some refinements but it looks like it's working.
Thanks to all who helped me. Especialy yabbadabbadont :) 
Great job

---

### Post by Michl on 2007-03-23
Well, as you discovered, you can use dial-up with ubuntu and once
running it works as well as MS if not better.  I download overnight
without problems.  The HowTo for dial-up modems is helpful --
has perfect directions for wvdial except as I remember, it does
not mention to remove the semi-colons.

Another hint:  add S19=0 to your initial strings.  This will keep the
modem from disconnecting.

ALso, gnome-ppp is a very fine tool.  Download the multiverse
packages and then in Synaptic search for gnome-ppp.  It makes
life very easy.  Add the gnome-ppp telephone to your panel.

Now, there is a problem with ubuntu and that's the network-admin-system
module.  The modem piece of this just does not work, and it's a
recognized bug.  Unfortunately, it is not a priority for development because
it seems there are too few dial-up users.

Michael

---

### Post by linuxjerk on 2007-03-23
Thanks Michael for your input.
Yes those semicolons had me guessing for quite a while. Once removed wvdial found my settings.
I'll look into some of your suggestions. I'm so green to this stuff though I would
probably need some help.

---

### Post by kratos1963 on 2007-03-26
> **Jason_25 said:**
> Wow your post was so long I couldn't bear to read it.  If your still using a modem then maybe ubuntu , any linux or any modern OS for that matter is not for you.

Do you understand how long it's going to take to apt-get simple items?  And that the entire concept of installing software in ubuntu is based on downloading it?

Generally, when you run into things like this that tend to take a while and no one can help, it's because it's not a very popular/modern solution.

There are alot of alternatives for broadband today if you can't get DSL/Cable/Fiber.

1.Digital Cellular Internet (EVDO).  I use it always when I'm helping someone that has internet problems.  Configuration time : 1 minute.

2.Satellite.  Not the best solution but infinitely better than dial up.  Configuration time: unknown

3.Public wireless / Commercial Wireless ISP.  Some very wooded remote areas around here have these if they don't have any other infrastructure.  Configuration time: significant?

Good luck with it though.

There are other uses for modems than just internet.  Fax , voice mail and automated phone services come to mind, and I'm sure there are other uses.

---

### Post by daxumaming on 2007-03-26
> **linuxjerk said:**
> Thanks for all the replies. No I can't get broadband. I'm too far from the tel for dsl and sat is way to expensive.
Believe me I wouldn't be doing this if I didn't have to.


If you have a spare $40 cash, the I would highly suggest you buy a serial modem like D-Link DFM 560EL.

From: [http://www.dlink-intl.com/Web/intl.nsf/f9a463de12d8035e48256a0d000d2620/c9479a33b045efad48256a70001d2ff7?OpenDocument](http://www.dlink-intl.com/Web/intl.nsf/f9a463de12d8035e48256a0d000d2620/c9479a33b045efad48256a70001d2ff7?OpenDocument)
> 16th April 2001 &#8211; D-Link
one of the largest True Manufacturers of data communications
and digital technology launched a new 56kbps external modem to re-capture the dial-up market. The new modem
D-Link DFM-560EL
is a serial modem that is smaller and lower cost yet high in performance and features.
High-Speed Analog Modem
The D-Link DFM-560EL is a high-speed 56kbps analog modem that is V.90 compatible. This allows users to connect to the ISP and download files or surf the web at high speeds.
Data
Fax and Voice Capabilities
The DFM-560EL is not only a data modem
it also has fax and voice capabilities. This mutli-purpose modem comes bundled with all the necessary software to fully utilize the features.

This only costs around $40 (depending on where you are located) and will work without any driver configurations. I've used this only once for 5 days before my ISP hooked up my broadband.

---

### Post by Robfuscate on 2007-05-14
> **Jason_25 said:**
> Wow your post was so long I couldn't bear to read it.  If your still using a modem then maybe ubuntu , any linux or any modern OS for that matter is not for you.

Do you understand how long it's going to take to apt-get simple items?  And that the entire concept of installing software in ubuntu is based on downloading it?

Generally, when you run into things like this that tend to take a while and no one can help, it's because it's not a very popular/modern solution.

There are alot of alternatives for broadband today if you can't get DSL/Cable/Fiber.

1.Digital Cellular Internet (EVDO).  I use it always when I'm helping someone that has internet problems.  Configuration time : 1 minute.

2.Satellite.  Not the best solution but infinitely better than dial up.  Configuration time: unknown

3.Public wireless / Commercial Wireless ISP.  Some very wooded remote areas around here have these if they don't have any other infrastructure.  Configuration time: significant?

Good luck with it though.

Ah yes. Standard answer number six. "Aren't you the stupid one for expecting Ubuntu to work as promised. You should have bought better equipment / got a better connection - what are you some sort of moron who doesn't understand that, despite the promise of equity, Ubuntu only works in Western countries with fast 'net access and for people who have enough money to buy the the right equipment, and have a second computer on which they can access the 'net to find you how to do basic things that the installation process *should* have done.

R

Wait a moment  'Ubuntu? Isn't that an ancient African word for 'Sucked in'?'

Oh, and I loved this - 
> **Jason_25 said:**
> Wow your post was so long I couldn't bear to read it.  If your still using a modem then maybe ubuntu , any linux or any modern OS for that matter is not for you.

Given that Ubuntu advertise itself as 'for human beings'; I'm really pleased to know that you consider anyone without the latest all singing all dancing technology as an unter-mensch. I bet I can guess where you're posting from.

---

### Post by Robfuscate on 2007-05-14
> **daxumaming said:**
>  Have you noticed how easy it is to install Ubuntu as compared to Windows?.

This is simply semantics. Sure it's easy in some ways to get yourself an Ububtu super typewriter;
but at the end of the day, if you have no 'net connection, then it actually ** hasn't ** installed, since anything beyond simply typing requires 'net access.

So, in short - NO!

R

---

### Post by Bartender on 2007-05-22
Robfuscate -
You need three things to use dial-up with as little pain as possible.

#1 -  A Linux-friendly ISP, such as Copper.net or BasicISP or ISP.com.  No ISP's with proprietary software, like Juno or PeoplePC or AOL

#2 - An external full hardware serial modem (and of course a serial connection on your computer - no longer a given with newer machines).

#3 - The most dial-up friendly Linux OS you can find.  Due to the idiotic need to create/edit the resolv.conf file and the fact that the GUI dialer has been broken since Dapper, none of the Ubuntus qualify.  PCLOS or MEPIS does.  There are probly others but those are the only two I've used.

---


---
title: "Hallo everybody: I'm new and got a prbl"
date: 2005-12-18
forum: Absolute Beginner Talk
---

### Post by Soran on 2005-12-18
Hi guys!

I recently moved to Linux Ubuntu and I'm quite confused: most of the time everything is ok. But in some occasions I feel just so stupid! I'm not sure of anything... Is this the typical attitude when one moves from Win to Linux?

Btw, I've got a small prbl: I use my laptop with two different internet connections. When I want to use the optical fiber I just have to use an Ethernet cable and everything works smoothly. But when I've to use the ADSL connection I've at home, the laptop doesn't recognize my modem. I know it's the driver, but I don't know how to install it. This is the full name of the driver I downloaded: bapst-0.7.4.tgz

I think it's not compiled and I don't really know what to do as a next step. Can anybody help me? Thanks a lot!

---

### Post by Iandefor on 2005-12-18
Open up a terminal and type in ```
sudo apt-get install build-essential
``` and then see if there's a file in the archive called
"INSTALL" which should contain installation instructions. If not, post a copy of 
bapst-0.7.4.tgz and I'll take a look at it.

---

### Post by bscbrit on 2005-12-18
The feeling confused feeling is not uncommon.  Don't worry - it will pass.  Just don't keep trying to do things the way you might have become used to doing them under a different OS.  Experiment, and read everything you can find in the forums.  Also try to find how to do things with ubuntu by reading this:

[http://makuchaku.info/amnesty/#](http://makuchaku.info/amnesty/#)

As for your modem problem, it is now way past my bedtime and I have got to go to work tomorrow.  But I'm sure someone will be able to help you soon.

---

### Post by Soran on 2005-12-18
I typed the code you gave me, Iandefor, and the terminal told me that build-essential has already the most recent version. So the next step would be to check in the archive, but I don't know how... :( 

Thanks for the support!

---

### Post by r4ik on 2005-12-18
[QUOTE=Soran]Hi guys!

I recently moved to Linux Ubuntu and I'm quite confused: most of the time everything is ok. But in some occasions I feel just so stupid! I'm not sure of anything... Is this the typical attitude when one moves from Win to Linux?

Keep in mind how long it took to get your way around in Windows. 
You will learn to handle Ubuntu in a much more faster way.
Read around and feel free to ask questions (probebly not answered by me at this moment :)
But others will.
Good luck !

---

### Post by Wolki on 2005-12-18
[QUOTE=Soran]So the next step would be to check in the archive, but I don't know how... :( 
[/QUOTE]

Right-click it and select "extract here". Then you can enter the directory and look at the files. :)

(of course, it's also possible from the command line: "tar -xvzf <filename>")

As Iandefor said, it should contain a file called INSTALL (or, if not, at least README). See if the info there helps you, if not, ask again with the problems you're encountering.

---

### Post by Soran on 2005-12-19
Ok, I extracted the file and checked: no install, but there is the read me.

I've to copy and paste it cause when tried to attach it, there was an error... :confused: 

I know that with this last post I'll loose the empathy of all of you ;), but I really don't know how to solve this. If you have time to help me, this is what I've found:

=^=^=^=^=^=^=^=^=^=^=^=^=^=

INTRODUCTION:

The software for the UNICORN ADSL PCI card consists of two loadable drivers, 
the unicorn_atm.o and unicorn_pci.o. The unicorn driver is a standard Linux 
ATM driver, that performs segmentation and reassembly (SAR) and flow control.
The unicorn_pci driver contains the ADSL modem software and hardware related
functions. It has been tested with the Linux 2.4.x kernels. Note that to use
PPPoE, PPPoA or RFC2684 protocols, the kernel may need to be patched.

COMPILATION:

To compile the drivers, unzip and untar the file. In the unicorn directory you 
will find the two subdirectories unicorn_atm and unicorn_bus.
You may compile the drivers based on the include files in the kernel source
or standard kernel include files. Set the variable KERNELDIR in the Makefile's
to point to your kernel sources if the first option in chosen. 
If you choose the latter, you may need to copy the contents of the kernel 
source "include/net" directory into "/usr/include/net/".
Go into these subdirectories and do a "make" and a "make install".
If the compile option "USE_HW_TIMER" is set, the performance is increased, 
but the CPU load increased. 
Use the same compiler as you use when compiling the linux kernel. The driver has
been tested using gcc-2.96, gcc-2.95.2, gcc-2.91.66 and gcc 3.0.3.


INSTALLATION:

To start the ADSL software, do a "modprobe unicorn_pci". Check in the syslog that
the drivers are started OK. The ADSL line should come up automatically. The status
can also be checked using the "proc" interface (/proc/net/atm/UNICORN\:0". 
SHOWTIME in the log or in the status means that ADSL connction is up and ATM cells
may be transmitted and received.
Depending on your network setup, you will need additional software as with any other
ADSL ATM card. For bridged ethernet (RFC2684), the br2684.o module and brctl is needed.
For PPPoE, any pppoe client over the bridged interface (nas0) should work 
(Roaring Penguin pppoe client has been tested).
The scripts directory contains some example startup scripts.

Bridged (RFC2684) and PPP over Ethernet:
Depending on your kernel, you may need to patch the kernel and enable the option
"RFC1483/2684 Bridged protcols" under "Networking options". Also ATM support needs
to be enabled.
Also the user space daemon "brctl" is needed. Instructions on how to apply the
patch and the brctl and patch sources can be found at [http://www.zoftware.org/adsl-pppoe](http://www.zoftware.org/adsl-pppoe).

PPP over ATM:
For PPP over ATM, the module pppoatm.o is needed, together with the pppd plugin
pppoatm.so and a version of pppd that supports plugins.
Currently version ppp-2.4.0b2 supports PPPoATM plugins. A patched version ready for
PPPoATM can be found at [http://www.sourceforge.net/](http://www.sourceforge.net/).

PPPoATM specific pppd options:
llc-encaps: use LLC encapsulation for PPPoATM
vc-encaps: use VC multiplexing for PPPoATM (default)


MODULE PARAMETERS:

Some ADSL paramters can be controlled by setting the moule paramters.

unicorn_pci.o:
--------------

ActTimeout: Timeout in ms on the duration of the activation state.

ActivationMode: This parameter sets in what mode the ADSL modem should be activated.
ANSI mode is 1, G.lite is 2, G.dmt is 4 and MULTI mode is 3.
If you know what mode your DSLAM operates in, use this mode. If not select either
ANSI or MULTI mode.

DownstreamRate: The maximum downstream rate in Kbit/sec.

AutoActivation: Set this to 1 if you your ADSL modem to start auotmatically (default 1).

DebugLevel: To debug the driver, set this to a value different from 0 and enable DEBUG
when compiling.

MswDebugLevel: 0 - High level, all traces enabled, 1 - Medium level, info and warnings
enabled, 2 - Low level, only warnings and errors are traced. 

LCD_Trig: Persistency time (in msec) of Loss of Cell Deliniation defects before
disorderly shutdown (15000 default).

LCD_LOF_Trig: Persistency time (in msec) of Loss of Signal and Loss of Frame defects before
disorderly shutdown (5000 default). 

TrainingDelay: Delay in msec used in training sequence. Default 80.

useRFCFixedRate: If 1, rate adaptive disabled. To use with ECI DSLAM in ITU mode.

_no_TS652: If set to 1, enable gain table for use without TS652.

unicorn_atm.o:
--------------

mac_address: If this is specified, the bridged ethernet (RFC2684) will use this
mac (ethernet) address instead of a randomly generated address. Specified as a 
12 character ASCII string of hexadecimal numbers.

atmready_timeout: The time in seconds to wait for ADSL link up when opening the ATM
socket (default 20 seconds).

DebugLevel: Set this if you need to debug the driver.

DIV:

mswtest contains a simple program to start/stop and get statistics from the ADSL card.
Depending on your distribution, you may need to install atm support (atm-2.4.0) to
compile this program.

RELEASE NOTES:

Version 0.0.5: 
- first working version.

Version 0.0.6: 
- Corrected an error when performing shutdown of the machine. 
- The modem sw compiled with CPU option 386. 
- Cleanups in the Makefile's.
- Removed un-compiled code in the ATM driver.

Version 0.0.7:
- Internal version.

Version 0.0.8:
- Simplified the Makefile's.

Version 0.0.9:
- Locking the module (MOD_INC_USE_COUNT) in unicorn_atm_open to be sure that module is
not removed while in use.
- New version of modem software.

Version 0.1.0:
- New modem software (1.0.7D) with fixes for ECI DSLAMs.
- The ActivationMode parameter values has changed. Please update your scripts !

Version 0.1.1:
- Added the _assert_fail function in linrapi.c to support certain versions of 
libm.a.
- Fixed a bug where timer structures were allocated but never released that may
cause failures after several hours of operation.
- Cleaned up and added debug code to memory allocation functions is linrapi.c.

Version 0.1.2:
- Initialize timer structure in xsm_create to avoid error when unloading driver.
- Conditionally call complete_and_exit depending on kernel version.

Version 0.1.3:
- New modem software (1.0.7E) with fixes for ECI DSLAMs.
- Test program (cmdtest) added.
 
Version 0.2.0:
- New modem software (1.0.7e-B-LINUX) that fixes the interoperability problems with ECI DSLAMs
and works in G.dmt mode.
- A kernel panic when halting the machine has been fixed.
- The OBC semaphore in the PCI_xxx functions is only released after PCI bus read.
- Added C++ support for gcc 3.0.

Version 0.2.1:
- Using xtime instead of get_fast_time(), since this function is not longer
exported in kernel 2.4.18.

Version 0.2.2:
- Using del_timer instead of del_timer_sync. This version works with SMP enabled.
- More tracing of MSW parameters.
- Removed some compiler warnings in unicorn_atm.
- New modem software (PCI_1.0.7f).

Version 0.2.3:
- Return an error in unicorn_atm_send if ADSL link is down. This avoids a kernel freeze with pppd.
- Add a prefix to KERN_INFO log messages.
- The "pilot tracking error" is a PRINT_WARNING instead of PRINT_ERROR.

Version 0.2.4:
- Set the PCI DMA access grant timeout to maximum to avoid a problem on ASUS motherboards.
- Use the writel/readl macros to access PCI registers.
- Modem software with UseVCXO to 0 as default in order to connect in ANSI mode.
- Fix a problem detecting linux version.
- Renamed the "cmdtest" folder to "unicorntest".

Version 0.2.6:
- The upstream cell rate calculation has been fixed. The actual link rate should now be quite close
to the theoretical max. This is very important for low speed links.
- New modem software (1.0.7i2).

Version 0.2.7:
- Ooops, forgot some debug code in unicorn_atmdrv.c.

Version 0.2.8:
- Undefined symbol fwrite when using a certain version of libm.a.

Version 0.2.9:
- Cleanups due to porting to PowerPC.
- In timer_callback, restart timer before put_msg to avoid race condition (and kernel panic).
- Make the driver ready for ST70136 AFE.
- OBC timer increased to 250ms.

Version 0.3.0:
- Removed a syslog when calling xtm_stopmsgtimer with invalid timer.
- Do not modify nice value, since the task_struct is dependent on the kernel version.

Version 0.3.1:
- Changed the values of the DMA max burst size.
- Modifications to Makefile.


Version 0.3.2:
- The modem software used by default is the 1.07f version, since this has proved to
be the most stable. This can be changed in the Makefile if needed.
- There was a divide by zero panic if the HZ was greater than 1000.
- Modifications to Makefile.

Version 0.3.3:
- Setting the PCI latency timer to 255 (correctly this time..).

Version 0.3.4:
- Remove #include <libiberty.h> from collect_tors.c
- DBG macro changed to KERN_DEBUG log level.

Version 0.3.5:
- New modem software (1.0.8) that works with Alcatel DSLAM v 4.2.13.
- Using mutex'es to protect access to OBC.
- Compile options moved to Makefile's.

Version 0.3.6:
- Implemented retry in the OBC access functions.
- Do not return error if not SHOWTIME in unicorn_atm_open (compile option).
- The compile option USE_HW_TIMER not defined by default.

Version 0.3.8:
- First working version of USB driver. It only works with the "uhci" host controller driver.
- Some small fixes in unicorn_atmdrv.c to correctly display the link speed.
- Included the libm.a with the modem SW library, since this library is not installed on some recent Linux distributions.
- Simplified the Makefile's and moved the binaries into the arc/i386 subfolder. 

Version 0.3.9:
- First version that works with usb-uhci driver. In this case FrameNumber=12 must be passed as module parameter.
- Added a script to establish Routed IP over ATM connections. Note that this script has not been tested.

Version 0.4.0:
- Automatically detect the type of USB Host Controller driver and set FrameNumber accordingly.
- New version (1.0.9) of modem software with new pilot tone detection algorithm.
- Use INT instead of OBC ISOC usb pipes in SHOWTIME.

Version 0.4.1:
- The USB bandwidth needed reduced from 90% to about 30% (512Kbits downstream).
- The driver is now ready for cards and adapters with new Analog Front Ends (20174).

Version 0.4.2:
- Licence added.

Version 0.4.3:
- The unicorn_usbdrv.c now compiles with kernel 2.4.20.

Version 0.4.4:
- Wrong fix in unicorn_usbdrv.c with kernel 2.4.20.
- Removed a few warning printks that are not really errors.

Version 0.4.5:
- Another wrong fix in unicorn_usbdrv.c with kernel 2.4.20.
- Ignoring errors in USB Interrupt Read if length is OK.

Version 0.4.7:
- Added support for AAL0 (raw) cells.
- Added a few ioctl's for the status application (coming later).
- The modem software library has been patched to remove strings containing "gcc2_copmpiled".
The driver now loads correctly on RedHat 8.0.
- The floating point library libm.a is no longer in the package. Please install it if with
your distribution (Mandrake 9.0) it is not installed. It is normally in /usr/lib/.
- There are two transmit queues with different priorities. This is in order to add support
for CBR,VBR streams. This is very preliminary and if you have any comment, please contact me.

Version 0.4.8:
- New graphical application "bewan_adsl_status" that shows the adsl state.
- Automatic detection of of adsl parameters using TR-037 or trial and error ("adsl-autoconfig").
- New start/stop script ("unicorn-adsl") that is using adsl-autoconfig.

Version 0.5.0:
- The source for the graphical application "bewan_adsl_status" included.
- New top-level Makefiles. To build the complete package, go to unicorn and type:
make,make install, make -f Makefile.modules, make -f Makefile.modules install.
- New modem software library compiled with GCC3.
- Correctly handing module versioning.

Version 0.5.1:
- C++ stubs added that was needed if the modules are compiled with GCC 2.
- Changes in the Makefile's, it now checks the PCI register and if there is a unicorn PCI card, 
it builds the PCI module else the USB module is built. 

Version 0.5.2:
- French localization of bewan_adsl_status finished.
- The unlock_kernel is now called before running the kernel thread.
- Some changes in the Makefile's. If you have both PCI and USB adapters, you can force building
the USB adapter by: make -f Makefile.modules pci install_pci

Version 0.5.3:
- Patches against the latest kernels in "patches" directory.
- Small fix in adsl-autoconfig to not write the config file if VPI,VCI not found.
- README for adsl-autoconfig added.

Version 0.5.4:
- Small modification in unicorntest.
- Small modification in unicorn_atmdrv.c to make it compile on new kernels.

Version 0.5.5:
- Script unicorn-ipoatm, unciorn-adsl and adsl autoconfig modified to work with provider free.

Version 0.6.0:
- New driver with Ethernet (instead of ATM) interface added to project. This driver supports 
RFC2684 routed (ipoatm), RFC2684 bridged (br2684,pppoe), and PPP over ATM with standard pppoe 
dialers. Note that this driver is in developement and the bewan_adsl_status application
and unicorntest does not work with this driver yet.

Version 0.6.1:
- Small modification in linrapi.c to make it compile with gcc 3.3.
- Added /proc entry for the unicorn_eth driver.

Version 0.6.2:
- Do not wake up tosca thread when disabling tosca soft interrupts.

Version 0.6.3:
- Added lock in CopySoftIntrTable since there are problems on SMP machines.
- The status application is now redimensioanable.

Version 0.6.4:
- Status and unicorntest application works with unicorn_eth drivers.
- Verify encapsulation in unicorn_eth driver.

Version 0.7.0:
- The bus drivers are now statically linked with the net drivers to simplify things. 
For example, the PCI ATM driver is now called "unicorn_pci_atm.o",and can be loaded by doing
 "insmod unicorn_pci_atm.o".
- Reorganized the files so that source files are not shared between PCI and USB drivers, except
when identical
- The Makefile's has been simplified. To compile and install all drivers and applications,
it is enough to do "make install" as root.
- The scripts has been simplified and will use the ethernet driver for PPPoE, Bridged and
IP over ATM.

Version 0.7.1:
- Implemented OAM loopback in the drivers. This is necessary in order to work with Telecom Italia lines.

Version 0.7.2:
- Removed the 'autoconfig', since I don't think it is used and did not work with the
new OAM loopback in the drivers.
- Added a new 'tools' directory. This contains simple tools to get the status, get the status as a  
cgi application and send OAM pings.
- Force the threads to run on CPU #0 only. Hopefully this hack will make it work on SMP.
- Some changes to the Makefile's.

Version 0.7.3:
- unicorntest compiled with DEBUG.
- Remove old versions of the files unicorn_atm.o,unicorn_pci.o and unicorn_usb.o in lib/modules/.

Version 0.7.4:
- Fixes in the Makefiles.
- Workaround for SMP disconnection.
- Lock around TOSCA interrupts (for SMP).
- Setting useAFE based on board id.
- Minor changes in adsl parameters.

IMPORTANT USB NOTES:
For USB to work correctly, I recommend using kernel 2.4.22 or later, since a lot of bugs has 
been fixed in the UHCI and OHCI drivers since early 2.4 kernel releases.
If you have a 2.4.21 kernel (Mandrake 9.1 or 2.4.21-xx) you need to patch the
usb-uhci and usb-ohci drivers to avoid a freeze when starting the unicorn_usb_xxx module. 
Copy the patches to the linux source directory and do:
patch -p0 < usb-uhci.patch
patch -p0 < usb-ohci.patch

---

### Post by Soran on 2005-12-19
I think I must add something. My ADSL modem is a usb one. ;)

Thanks all!

---

### Post by Deaf_Head on 2005-12-19
lniux hurts for a few days .. until you stop feeling lieka  newb .. once you know a little it's like AWSOME and stuff.

---

### Post by az on 2005-12-19
"It has been tested with the Linux 2.4.x kernels"

That is too old.

Install these:
[http://packages.ubuntu.com/breezy/net/unicorn-source](http://packages.ubuntu.com/breezy/net/unicorn-source)
[http://packages.ubuntu.com/breezy/net/unicorn](http://packages.ubuntu.com/breezy/net/unicorn)

Just enable multiverse and install unicorn-source and unicorn

You need build-essential, linux-headers-2.6.12-(whatever - see the kernel you are running; 386 is the default) and gcc-3.4 to compile stuff for your kernel.

Read the README here (after you install the package):
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=unicorn-source&version=breezy&arch=all](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=unicorn-source&version=breezy&arch=all)

You probable have to open a terminal and run

cd /usr/src
tar xvzf unicorn.tar.gz
cd unicorn
and make it (or make a deb package out of it -  read the readme)


The utilities it installs:

[http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=unicorn&version=breezy&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=unicorn&version=breezy&arch=i386)

---

### Post by Soran on 2005-12-19
Thanks for the tips.

Ok, I've installed Unicorn. But now, I don't know what to do once more... :-\"

---

### Post by Soran on 2005-12-20
I have to post again to catch your attention: I've still the same problem and I'm not able to solve it...

Please, help me or I won't use internet during Christmas vacations!!! [-o< :shock:

---

### Post by zasf on 2006-03-29
[QUOTE=Soran]I have to post again to catch your attention: I've still the same problem and I'm not able to solve it...

Please, help me or I won't use internet during Christmas vacations!!! [-o< :shock:[/QUOTE]

I recently installed unicorn driver for a bewan modem on Dapper, you may want to check this [http://battlehorse.homelinux.net/w/Wiki.jsp?page=UnicornDriverUSBADSLModem](http://battlehorse.homelinux.net/w/Wiki.jsp?page=UnicornDriverUSBADSLModem)

---

### Post by www.rzr.online.fr on 2007-12-24
> **zasf said:**
> I recently installed unicorn driver for a bewan modem on Dapper, you may want to check this [http://battlehorse.homelinux.net/w/Wiki.jsp?page=UnicornDriverUSBADSLModem](http://battlehorse.homelinux.net/w/Wiki.jsp?page=UnicornDriverUSBADSLModem)

I did too on dapper and it worked
.. trying on gutsty now
--
[http://rzr.online.fr/q/unicorn](http://rzr.online.fr/q/unicorn)

---


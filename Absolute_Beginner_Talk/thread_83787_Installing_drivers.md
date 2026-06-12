---
title: "Installing drivers"
date: 2005-10-29
forum: Absolute Beginner Talk
---

### Post by Matt Houston on 2005-10-29
Hi,

Fairly new to Linux, I initially jumped in the deep end and installed Slackware which was probably a bit ambitious, gave up on that and have just installed Ubuntu which seems a lot more user friendly.

I am trying to get my ZOOM ADSL modem working, I tracked down a Linux driver here: [http://sourceforge.net/projects/accessrunner](http://sourceforge.net/projects/accessrunner).

1. Problem is as far as I can tell it is the source code and I have no idea how to compile this, can somebody help?

2. Is there an advantage to compling the source code when installing drivers and software as opposed to the 'Windows' way, ie double clicking an install file?

3. Am I correct in thinking it is best to install all programs as root? 

Help would be greatly appreciated, thanks.

---

### Post by davmac on 2005-10-29
I've had a look through this package and it is not like any other I've seen. In general though, answering your questions...

1. You'll often find instructions for compiling in a README file with the package but if it doesn't include this you can usually do the following. Open up a terminal and;

sudo apt-get install build-essential       (This make sure you've got most of the compilers etc)
cd <directory where download is>
tar -xvzf <name of tar.gz file>             (To unpack the source code)
or
tar -xvjf <name of tar.bz2 file>             (To unpack the source code)

./configure                                       (To set everything up ready for the compile)
make                                              (To do the compile)
sudo make install                              (To install the compiled application)

2. There is no great advantage for a beginner to compile from source, unless you need the latest unstable or beta release of a product. Generally with different types of linux the install can be radically different and compiling from source is the lowest common denominator.

3. You can (and usually should) do the configure and make without the sudo. It is only required for the "make install" because you'll be copying files to protected directories.

Looking at this drivers package there is no README file and it comes with a couple of files called Kbuild and Kconfig, which are unfamiliar to me. I notice that there is a forum at [http://sourceforge.net/forum/?group_id=47406](http://sourceforge.net/forum/?group_id=47406) . If you search through this you'll find an Ubuntu user that has hit the same problem, but there's no response to his question. Not much help I'm afraid :(

Dave Mac

---

### Post by Matt Houston on 2005-10-29
Oh right, didn't realise sourceforge had a forum. Thanks for the help, I'll get it working somehow.

---

### Post by davmac on 2005-10-30
Matt,

If you don't get the answer at sourceforge though, come back and post here - you may still find someone who has hit and solved the same problem.

All the best,

Dave Mac

---

### Post by Matt Houston on 2005-11-01
Got an email Josep, they guy who wrote the driver, said he was too busy to help me but gave me the following info, can anybody make sense of the following: [http://accessrunner.sourceforge.net](http://accessrunner.sourceforge.net)

Obtaining the sources
Until the driver is included in the Linux kernel distribution, you can download it here.

Since the driver for AccessRunner-based modems is developed within the recently created usbatm subsystem of the Linux kernel, it is distributed as a whole drivers/usb/atm kernel subtree.

The development version of the usbatm subsystem is available via anonymous CVS. To get them run 

  cvs -z9 -q -d :pserver:anoncvs:anoncvs@cvs.infradead.org:/home/cvs co usbatmand put the files under drivers/usb/atm in the kernel source tree.

Configuring kernel build
You need to set up the kernel source tree to build the kernel tailored to your system. The details of this process are described elsewhere; here is the list of configuration options you need to select to m (module) or y (built in) to include the support for the AccessRunner-based ADSL modems:

Prompt for development and/or incomplete code/drivers (EXPERIMENTAL)
...
  Asynchronous Transfer Mode (ATM) (EXPERIMENTAL) (ATM)
...
Support for Host-side USB (USB)
...
USB DSL modem support (USB_ATM)
...
  Conexant AccessRunner USB support (USB_CXACRU)
    You'll probably need a lot more: the drivers for your USB host controllers, the networking options, etc. Please resort to the kernel documentation and your common sense.

Kernel firmware loader
Including firmware loader in the kernel
Kernel firmware loader is provided by firmware_class driver. Most distributions have it enabled in their kernel packages. Even if yours doesn't, it will be automatcially included in the kernel build when you select cxacru driver.

Setting up hotplug to load the firmware
When asked by the driver, the firmware loader calls out the hotplug system passing it the name of the requested fimware file in an environment variable. Most distributions ship the hotplug package with support for the fimware loader included, typically in /etc/hotplug/firmware.agent. You need to find out where your hotplug firmware agent looks for the firmware files (often /lib/firmware), and put your firmware files there.

For more information you are referred to the Linux Hotplug home page.

---

### Post by spako on 2006-01-21
hi i recently tried to install the above mentioned driver from [http://accessrunner.sourceforge.net](http://accessrunner.sourceforge.net) for my conexant adsl usb modem.

got make installed but havn't manager to get the driver complied with my kernel.

has anyone managed to install the above modem? if so how did you do it?

i'm quite new to linux so any help is appreciated!

---

### Post by fo3 on 2006-05-12
I'm trying to install a driver for a raid card (IT8212).  I've downloaded the files for it and have two questions.  First in the folders there is files for redhat, turbo, mandrake and readme's for them, there's one for deb 3 too, but no read me for that so now sure it would work. 
 in the source folder for kernel 2.6.x it has a iteraid.c and iteraid.h and makefile.  How do I compile them into a kernel I'm trying to build?  or even by themselves into the existing system kernel I'm running on?
Probably dumb questions, but hopefully I'll get an answer.  I did unix at school 5 years ago and have forgotten all of it.  I've tried what I've remembered (./configure make etc), and just it doesn't want to try.  I've downloaded and install most libraries due to me trying to build a kernel, so it's not missing programs.

---


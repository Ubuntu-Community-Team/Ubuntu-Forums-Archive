---
title: "Error Trying to Install Driver"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by nicolasqueen on 2008-04-12
Well, I think I was doing this at least! 

I am trying to get my wireless working on my laptop. I have an Atheros AR5008X wireless adapter. I used the make command as indicated in the INSTALL and I got this:

```
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/nickqueen/Desktop/madwifi-0.9.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/nickqueen/Desktop/madwifi-0.9.4/ath/if_ath.o
  CC [M]  /home/nickqueen/Desktop/madwifi-0.9.4/ath/if_ath_pci.o
  LD [M]  /home/nickqueen/Desktop/madwifi-0.9.4/ath/ath_pci.o
  CC [M]  /home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/ah_os.o
  HOSTCC  /home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c: At top level:
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c: In function 'main':
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal/uudecode] Error 1
make[2]: *** [/home/nickqueen/Desktop/madwifi-0.9.4/ath_hal] Error 2
make[1]: *** [_module_/home/nickqueen/Desktop/madwifi-0.9.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [modules] Error 2
nickqueen@nickqueen-laptop:~/Desktop/madwifi-0.9.4$ 


```

I am a newbie and this totally threw me for a loop. What am I doing wrong?

Nick

---

### Post by warbread on 2008-04-12
Please post the directions you were following.

---

### Post by nicolasqueen on 2008-04-12
Here goes. I get the error when using the make command. Also, how does one log in as root?

> MADWIFI: Multimode Atheros Driver for WiFi on Linux (VAP branch)
================================================================

* Copyright (c) 2002-2005 Sam Leffler.  All rights reserved.

Read the file COPYRIGHT for the complete copyright.


Requirements
------------

- Configured kernel sources of the target kernel.  Some Linux
  distributions provide headers, makefiles and configuration data - it
  should suffice.

- Wireless Extensions support (14 or later, 17 preferred) - option
  CONFIG_NET_RADIO in kernel .config file.

- Sysctl support - option CONFIG_SYSCTL in kernel .config file.

- Crypto API support - option CONFIG_CRYPTO in kernel .config file (AES
  support is used if present, otherwise the AES-CCMP cipher module falls
  back to a private implementation).

- gcc of same version that was used to compile the kernel.  At least
  make sure that the first two version numbers or the compiler are the
  same (e.g. it's OK to use gcc 3.4.6 to compile MadWifi if the kernel
  was compiled by gcc 3.4.2).  Ignoring this rule will cause "Invalid
  module format" errors during module load.

Linux 2.4.x kernels starting with 2.4.22 and 2.6 kernels should work
without problems.  Due to quick pace of Linux development, there is no
way compatibility with the future 2.6 kernels can be ensured.  However,
the latest 2.6 kernel at the time of the release should be expected to
work.

Automatic module loading support (CONFIG_KMOD) is recommended; otherwise, 
care will have to be taken to manually load needed modules.

Building the driver
-------------------

The driver is built using the Linux kernel build mechanism.  This means
you must have some part of the kernel source distribution installed on
the machine where you want to build the driver.  In particular, the
kernel include files, makefiles, build scripts and configuration must be
available.

This will be present if you built your kernel from source.  Otherwise
you may need to install an additional kernel development package from
your distribution that would match your kernel.  For example, the
development package for the default kernel is called linux-headers on
Debian and kernel-devel on Fedora Core.  Installing a package with full
kernel sources should not be generally necessary.

Note: in the following examples "$" stands for your system prompt;
you're not expected to type that as part of the actual command.  "#"
stands for the command prompt when the commands must be executed by
root.

Most people can just type:

  $ make

in the top-level MadWifi source directory to build all the modules for
the currently running system.

You MUST do a "make clean" before compiling for a different version of
Linux, e.g. building for 2.6 after building for 2.4.

If you want to compile MadWifi for a different kernel, you need to
specify the location of the kernel build tree, e.g.:

  $ make KERNELPATH=/usr/src/linux-2.6.3

Note that you can also specify this path by setting an environment
variable; e.g.

  $ export KERNELPATH=/usr/src/linux-2.6.3
  $ make

If the kernel was built outside the source directory, KERNELPATH should
point to the output directory where .config is located, not to the
sources.

MadWifi currently provides four different rate control algorithms,
ONOE, AMRR, SAMPLE and MINSTREL.  SAMPLE and MINSTREL are both very
advanced, but MINSTREL is quite new.  Consequently, SAMPLE is used by
default.  In order to make MadWifi use e.g. AMRR instead, you have to
specify that as the module parameter e.g.

  # modprobe ath_pci ratectl=amrr

NOTE: Changing the rate control is only required (and recommended) for
      users who want to setup an access point using MadWifi in difficult
      (e.g. lossy) environments and who know what they are doing.

This distribution includes support for a variety of target platforms.
Because of the binary nature of the HAL not all platforms are supported
(the list grows as time permits).  The supported target platforms can be
found with:

  $ ls hal/public/*.inc

A target specifies the CPU architecture, byte order (unless implied by
the CPU), and the ABI/file format.  For most popular platforms, the
build system will find the appropriate files.  When cross-compiling or
compiling for less common platforms, the target platform may need to be
specified using the TARGET variable, e.g:

  $ make TARGET=armv4-le-elf

Consult the contents of the .inc file to find out what the target
platform is and what toolchain was used to build the HAL object module. 
Beware of mixing toolchains; some target platforms require that the HAL
and driver be built with the same toolchain (i.e. compiler, assembler,
and linker) and the same compiler flags.  If you get warnings about
incompatible compiler flags, chances are that you are compiling for a
wrong target or using an incompatible compiler.


Cross-compiling
---------------

The build system is designed to support cross-compiling without any
modification to the distribution files.  It should be sufficient to
specify any parameters on the make command line.

In most cases, only KERNELPATH and CROSS_COMPILE need to be defined. 
CROSS_COMPILE is the prefix for cross-compiling tools.  For instance, if
the cross compiler is called arm-linux-gcc, set CROSS_COMPILE to
"arm-linux-":

  $ make KERNELPATH=/usr/src/linux-arm CROSS_COMPILE=arm-linux-

The build system determines ARCH and TARGET based on the .config file in
the Linux build tree.  TARGET still may need to be provided on the
command line some uncommon systems.  If ARCH is determined incorrectly,
please report it.


Loading the modules
-------------------

Building the software will generate numerous loadable modules:

  ath_pci		Atheros driver for PCI/Cardbus devices
  ath_hal		Atheros HAL
  wlan			802.11 support layer
  wlan_wep		WEP cipher support
  wlan_tkip		TKIP cipher support
  wlan_ccmp		AES-CCMP cipher support
  wlan_xauth		external authenticator
  wlan_acl		MAC ACL support for AP operation
  wlan_scan_ap		AP scanning support
  wlan_scan_sta		station scanning support
  ath_rate_onoe		ONOE rate control
  ath_rate_amrr		AMRR rate control
  ath_rate_sample	SAMPLE rate control

The ath_pci module must be loaded either manually or by the system, e.g.
through the hotplug or card manager support.  The remaining modules are
loaded automatically as needed, so after doing a "make install" you only
need to run following:

  # modprobe ath_pci

For automatic module loading you may need to modify your system's
configuration files so the necessary modules are loaded when an Atheros
device is recognized.  The exact procedure varies from system to system.

There are module parameters available to fit your needs, e.g. you can
set the countrycode manually if your card's EEPROM does not contain the
correct one for your location.  See
[http://www.unicode.org/onlinedat/countries.html](http://www.unicode.org/onlinedat/countries.html) to find your code.

To activate German frequencies you would specify:

  # modprobe ath_pci countrycode=276

To see all available module parameters type:

  $ modinfo ath_pci


Integrating into the kernel sources
-----------------------------------

It is also possible to patch Linux kernel sources to integrate MadWifi
directly into the kernel tree.  This allows building MadWifi as part of
the kernel.  This could be useful for embedded systems that don't
support loadable modules.  Please refer to patches/README for details.


Further information
-------------------

Further information on how to work with the driver can be found in the
file README.  In addition, the project's wiki has a lot of valuable
information:

[http://madwifi.org/](http://madwifi.org/)


---

### Post by Michael.Godawski on 2008-04-12
For compiling from source you often need the package build essential.
```
sudo apt-get install build-essential
```
You do not need to log in as root. Just use the sudo in front of a command to activate the root privileges temporarily.

---


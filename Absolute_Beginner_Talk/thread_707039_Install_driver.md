---
title: "Install driver"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by ieow on 2008-02-25
i just started using ubuntu 6.10
having difficult when installing nvidia graphic card driver.
pic att is when i run the file.

there is problem when installing WL230usb wireless adaptor.
below are the code after 'make'

ieow@ieow-desktop:~/WL230USBLnxDrv_2_12_0_0$ make
/lib/modules/2.6.20-15-generic/build
/home/ieow/WL230USBLnxDrv_2_12_0_0
-I/home/ieow/WL230USBLnxDrv_2_12_0_0/src/include -fomit-frame-pointer -O2 -Wall -DZDCONF_WE_STAT_SUPPORT=1 -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZDCONF_MENUDBG -DZDCONF_APDBG -DZDCONF_BANDEDGE_ADJUST -DZDCONF_SES_SUPPORT=1 -DZD1211B -DZDCONF_LP_SUPPORT=1
src/zd1205.o src/zdreq.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zddebug2.o src/zdlpmgt.o src/zdturbo_burst.o src/zdusb.o src/zd1211.o
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/ieow/WL230USBLnxDrv_2_12_0_0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/ieow/WL230USBLnxDrv_2_12_0_0/src/zd1205.o
/home/ieow/WL230USBLnxDrv_2_12_0_0/src/zd1205.c:34:26: error: linux/config.h: No such file or directory
/home/ieow/WL230USBLnxDrv_2_12_0_0/src/zd1205.c:466: error: expected declaration specifiers or ‘...’ before ‘write’
/home/ieow/WL230USBLnxDrv_2_12_0_0/src/zd1205.c:466: error: expected declaration specifiers or ‘...’ before ‘fd’
/home/ieow/WL230USBLnxDrv_2_12_0_0/src/zd1205.c:466: error: expected declaration specifiers or ‘...’ before ‘buf’
/home/ieow/WL230USBLnxDrv_2_12_0_0/src/zd1205.c:466: error: expected declaration specifiers or ‘...’ before ‘count’
/home/ieow/WL230USBLnxDrv_2_12_0_0/src/zd1205.c:467: warning: type defaults to ‘int’ in declaration of ‘_syscall3’
/home/ieow/WL230USBLnxDrv_2_12_0_0/src/zd1205.c:467: error: expected ‘,’ or ‘;’ before ‘_syscall3’
/home/ieow/WL230USBLnxDrv_2_12_0_0/src/zd1205.c:472: error: ‘dot11A_Channel’ undeclared here (not in a function)
/home/ieow/WL230USBLnxDrv_2_12_0_0/src/zd1205.c: In function ‘zd1205_validate_frame’:
/home/ieow/WL230USBLnxDrv_2_12_0_0/src/zd1205.c:2760: warning: unused variable ‘len1’
/home/ieow/WL230USBLnxDrv_2_12_0_0/src/zd1205.c: In function ‘zd1205_load_card_setting’:
/home/ieow/WL230USBLnxDrv_2_12_0_0/src/zd1205.c:8384: warning: implicit declaration of function ‘open’
/home/ieow/WL230USBLnxDrv_2_12_0_0/src/zd1205.c:8401: warning: implicit declaration of function ‘read’
/home/ieow/WL230USBLnxDrv_2_12_0_0/src/zd1205.c:8405: warning: implicit declaration of function ‘close’
/home/ieow/WL230USBLnxDrv_2_12_0_0/src/zd1205.c: In function ‘zd1205_save_card_setting’:
/home/ieow/WL230USBLnxDrv_2_12_0_0/src/zd1205.c:8557: warning: implicit declaration of function ‘write’
/home/ieow/WL230USBLnxDrv_2_12_0_0/src/zd1205.c: In function ‘zdcb_setup_next_send’:
/home/ieow/WL230USBLnxDrv_2_12_0_0/src/zd1205.c:8945: warning: unused variable ‘loopCnt’
/home/ieow/WL230USBLnxDrv_2_12_0_0/src/zd1205.c:8973: warning: unused variable ‘tmpDataTime’
/home/ieow/WL230USBLnxDrv_2_12_0_0/src/zd1205.c:8972: warning: unused variable ‘LastData’
/home/ieow/WL230USBLnxDrv_2_12_0_0/src/zd1205.c:8982: warning: label ‘TX_LOOP’ defined but not used
/home/ieow/WL230USBLnxDrv_2_12_0_0/src/zd1205.c:8880: warning: unused variable ‘LP_CNT_LAST_LATENCY’
/home/ieow/WL230USBLnxDrv_2_12_0_0/src/zd1205.c:8824: warning: unused variable ‘tbdidx’
/home/ieow/WL230USBLnxDrv_2_12_0_0/src/zd1205.c: In function ‘CalculateQuality’:
/home/ieow/WL230USBLnxDrv_2_12_0_0/src/zd1205.c:10220: warning: unused variable ‘rxOffset’
make[2]: *** [/home/ieow/WL230USBLnxDrv_2_12_0_0/src/zd1205.o] Error 1
make[1]: *** [_module_/home/ieow/WL230USBLnxDrv_2_12_0_0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [all] Error 2
ieow@ieow-desktop:~/WL230USBLnxDrv_2_12_0_0$ 



last problem is problem installing mplayer
there are problem when './configure' is typed

ieow@ieow-desktop:~/MPlayer-1.0rc2$ ./configure
Detected operating system: Linux
Detected host architecture: i386
Checking for cc version ... 4.1.2, ok 
Checking for host cc ... cc 
Checking for cross compilation ... yes 
Checking for CPU vendor ... AuthenticAMD (15:75:2) 
Checking for CPU type ...  AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ 
Checking for kernel support of mmx ... failed 
It seems that your kernel does not correctly support mmx.
To use mmx extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of mmxext ... failed 
It seems that your kernel does not correctly support mmxext.
To use mmxext extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of 3dnow ... failed 
It seems that your kernel does not correctly support 3dnow.
To use 3dnow extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of 3dnowext ... failed 
It seems that your kernel does not correctly support 3dnowext.
To use 3dnowext extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of sse ... failed 
It seems that your kernel does not correctly support sse.
To use sse extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of sse2 ... failed 
It seems that your kernel does not correctly support sse2.
To use sse2 extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of cmov ... failed 
It seems that your kernel does not correctly support cmov.
To use cmov extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for mtrr support ... yes 
Checking for GCC & CPU optimization abilities ... CPU optimization disabled. CPU not recognized or your compiler is too old. 
error 
Checking for assembler support of -pipe option ... no 
Checking for compiler support of named assembler arguments ... yes 
Checking for assembler (as 2.17.50) ... ok 
Checking for .align is a power of two ... no 
Checking for Linux kernel version ... 2.6.20-15-generic, ok 
Checking for -lposix ... no 
Checking for -lm ... no 
Checking for langinfo ... no 
Checking for language ... using en (man pages: en ) 
Checking for enable sighandler ... yes 
Checking for runtime cpudetection ... no 
Checking for restrict keyword ... none 
Checking for __builtin_expect ... no 
Checking for kstat ... no 
Checking for posix4 ... no 
Checking for lrintf ... no 
Checking for mkstemp ... no 
Checking for nanosleep ... no 
Checking for socklib ... no 
Checking for inet_pton() ... no (trying inet_aton next)
Checking for inet_aton() ... no (network support disabled)
Checking for network ... no 
Checking for inttypes.h (required) ... no 
Checking for bitypes.h (inttypes.h predecessor) ... 
Error: Cannot find header either inttypes.h or bitypes.h. There is no chance for compilation to succeed.

Check "configure.log" if you do not understand why it failed.
ieow@ieow-desktop:~/MPlayer-1.0rc2$ 


hope anyone can help my problem.

---

### Post by northern lights on 2008-02-25
Run your nvidia installer with "gksudo":```
gksudo nvdia-installer
```where "nvidia-installer" needs to be replaced with the comman you run.

Do you habe "build-essentials" installed?

---

### Post by ieow on 2008-02-25
sorry i dont know what is built-essentials.
i try but the out come is in att

---

### Post by northern lights on 2008-02-25
Prior to beginning the installation, you should exit the X server and kill all
OpenGL applications (note that it is possible that some OpenGL applications
persist even after the X server has stopped). You should also set the default
run level on your system such that it will boot to a VGA console, and not
directly to X

--> Check [these]("http://us.download.nvidia.com/XFree86/Linux-x86/96.43.05/README/README.txt") installation instructions...

---

### Post by Delkster on 2008-02-25
> **ieow said:**
> 
last problem is problem installing mplayer
there are problem when './configure' is typed

Is there a reason why you need to compile it yourself from source? MPlayer is also available in the Ubuntu repositories, so you could try just looking for it in Add/Remove Applications (or Synaptic Package Manager or whatever you happen to like). You need to have the "multiverse" software channel enabled for that. Add/Remove Applications should automatically prompt you for that if you try to install MPlayer. Note that you must search with "Show: all available applications" for MPlayer to show up in the search.

---

### Post by ieow on 2008-02-26
Thanks i will read and try it.

> **Delkster said:**
> Is there a reason why you need to compile it yourself from source? MPlayer is also available in the Ubuntu repositories, so you could try just looking for it in Add/Remove Applications (or Synaptic Package Manager or whatever you happen to like). You need to have the "multiverse" software channel enabled for that. Add/Remove Applications should automatically prompt you for that if you try to install MPlayer. Note that you must search with "Show: all available applications" for MPlayer to show up in the search.

Actually i am living in a hostel that did not provide internet services. therefore, i could not updat ubuntu or add any program directly (online).

---

### Post by ieow on 2008-03-03
having problem..

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Wed Feb 27 14:09:17 2008

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> The file '/tmp/.X0-lock' exists and appears to contain the process ID
   '12751' of a runnning X server.
ERROR: You appear to be running an X server; please exit X before installing. 
       For further details, please see the section INSTALLING THE NVIDIA DRIVER
       in the README available on the Linux driver download page at
       [www.nvidia.com](www.nvidia.com).
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

i seem there is .xo-lock exist in /tmp. But....

ieow@ieow-desktop:/tmp$ sh .X0-lock
.X0-lock: 1: 12751: not found
ieow@ieow-desktop:/tmp$ dir
gconfd-ieow           mapping-ieow    virtual-ieow.fnVWD8  virtual-ieow.KHn2SF
gedit.ieow.492688072  orbit-ieow      virtual-ieow.GXzXfx  virtual-ieow.Pqo6hs
keyring-nctB04        ssh-ISyqg13049  virtual-ieow.IXyk61
ieow@ieow-desktop:/tmp$ 


can anyone help???

---

### Post by northern lights on 2008-03-03
> **ieow said:**
> -> The file '/tmp/.X0-lock' exists and appears to contain the process ID
   '12751' of a running X server.
ERROR: You appear to be running an X server; please exit X before installing. 
Run your installation from the commandline only. In a terminal type ```
sudo /etc/init.d/gdm stop
```
Login with "Alt+F3"
Do your thing.
Restart your desktop environment: ```
sudo /etc/init.d/gdm start
```

---


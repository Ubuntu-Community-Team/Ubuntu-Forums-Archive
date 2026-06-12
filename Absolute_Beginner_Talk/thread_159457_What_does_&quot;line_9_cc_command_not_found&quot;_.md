---
title: "What does &quot;line 9: cc: command not found&quot; mean"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by Exile29 on 2006-04-12
I'm trying to install nForce drivers for my sound. Everything else works just fine. 
I've tinkered with it quite a bit up 'til now, and to be honest, I think getting this far has been quite a Linux n00b breakthrough for me.
Anyhow, when I run the nVidia installer, I get this in the log:

> nforce-installer log file '/var/log/nvidia-nforce-installer.log'
creation time: Wed Apr 12 22:42:15 2006

option status:
  license pre-accepted      : false
  expert                    : false
  uninstall                 : false
  driver info               : false
  no precompiled interface  : false
  no ncurses color          : false
  no questions              : false
  silent                    : false
  Installer install prefix  : /usr
  kernel source path        : /usr/src/linux-headers-2.6.12-10-386
  net kernel install path   : (not specified)
  audio kernel install path : (not specified)
  proc mount point          : /proc
  ui                        : (not specified)
  tmpdir                    : /tmp

Using: nvidia-installer ncurses user interface
-> Found package NVIDIA network driver for Linux-x86
-> Found package NVIDIA audio driver for Linux-x86
-> Please select packages for installation:
   Selections:
   NVIDIA audio driver for Linux-x86 (1.0-7)
-> Starting install of NVIDIA audio driver for Linux-x86
-> Checking for loaded module nvsound
-> Checking for loaded module nvaudio
-> License accepted.
-> Skipping check for conflicting rpms.
-> /proc/version is Linux version 2.6.12-10-386 (buildd@terranova) (gcc version
   3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8.1)) #1 Sat Mar 11
   16:13:17 UTC 2006
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Using the kernel source path '/usr/src/linux-headers-2.6.12-10-386' as
   specified by the '--kernel-source-path' commandline option.
-> Kernel source path: '/usr/src/linux-headers-2.6.12-10-386'
-> Kernel output path: '/lib/modules/2.6.12-10-386/build'
-> Performing cc_version_check with CC="gcc-3.4".
ERROR: ./nvsound/main/conftest.sh: line 9: cc: command not found
       
       If you are using a Linux 2.4 kernel, please make sure
       you either have configured kernel sources matching your
       kernel or the correct set of kernel headers installed
       on your system.
       
       If you are using a Linux 2.6 kernel, please make sure
       you have configured kernel sources matching your kernel
       installed on your system. If you specified a separate
       output directory using either the "KBUILD_OUTPUT" or
       the "O" KBUILD parameter, make sure to specify this
       directory with the SYSOUT environment variable or with
       the appropriate nvidia-installer command line option.
ERROR: Installation of the audio driver has failed.  Please see the file
       '/var/log/nvidia-nforce-installer.log' for details.  You may find
       suggestions on  fixing installation problems in the README available on
       the Linux driver download page at [www.nvidia.com](www.nvidia.com).

I look at this and don't see anything seriously wrong, but then again, I am a n00b. 
Could somebody please give me a bit of help?

Thanks in advance.

---

### Post by rmjokers on 2006-04-12
Looks like you need to install some compiler tools so that you can build the necessary software.  Try:

sudo apt-get install build-essential

This will install the gcc compiler and related utilities.

---

### Post by sn123 on 2006-04-12
[QUOTE=Exile29]I'm trying to install nForce drivers for my sound. Everything else works just fine. 
I've tinkered with it quite a bit up 'til now, and to be honest, I think getting this far has been quite a Linux n00b breakthrough for me.
Anyhow, when I run the nVidia installer, I get this in the log:



I look at this and don't see anything seriously wrong, but then again, I am a n00b. 
Could somebody please give me a bit of help?

Thanks in advance.[/QUOTE]

you would need to install gcc and libc6-dev for cc command to work.
EDIT: rmj beat me to it.

---

### Post by Exile29 on 2006-04-12
Hmm... I could've sworn I installed gcc-3.4.
Anyhow, I just ran "sudo apt-get install build-essential" and it looks like it installed gcc-4.0.1-3.
Should I have removed the 4.0.1 deb from the archives?
I'll run the installer again.

---

### Post by Exile29 on 2006-04-13
Worked!!!
Sweet, sweet sound!
Thanks for the advice sn123 and rmjokers.

---


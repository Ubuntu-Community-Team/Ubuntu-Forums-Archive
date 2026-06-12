---
title: "Failed installing nForce Drivers"
date: 2006-05-06
forum: Absolute Beginner Talk
---

### Post by Kuraboy on 2006-05-06
Hi!

I have problems installing nForce drivers Linux nForce Driver - IA32, Version: 1.0-0310.

I get en error message saying : 'No precompiled kernel interface was found to match your kernel; this means that the installer willl need to compile a new kernel interface'

I typed OK. 

then it said,  ERROR: Unable to fin the kernel source tree for the currently running kernel.....

here is log file:

```
nforce-installer log file '/var/log/nvidia-nforce-installer.log'
creation time: Sat May  6 20:10:20 2006

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
  kernel source path        : (not specified)
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
-> /proc/version is Linux version 2.6.12-9-386 (buildd@rothera) (gcc version
   3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36
   BST 2005
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel; on Red Hat Linux systems, for example, be sure you have the
       'kernel-source' rpm installed.  If you know the correct kernel source
       files are installed, you may specify the kernel source path with the
       '--kernel-source-path' commandline option.

```

I tryed installing Kernel 2.6.10 source code from synaptec but it didnt help.

any help is appriciated, thnx in advance ^_^

---

### Post by Ensnared on 2006-05-06
What you need is the kernel header-files for your current kernel. This is basically the part of the source-code that lets you compile drivers for the kernel.

To install it, do this:```
sudo apt-get install linux-headers-`uname -r`
```

There's a complete howto for installing these drivers on Breezy [here](http://doc.gwos.org/index.php/Latest_Nvidia_Breezy), and if you're using Dapper (e.g. the beta of the upcoming Ubuntu) there's a similar howto [here](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper).

EDIT: Ok, so it's the **nForce** drivers - didn't see that, sorry. Ignore the links above, but the package you need to compile them still applies :)

---

### Post by hw-tph on 2006-05-06
Why do you need to install these drivers? The audio should be supported (snd-intel8x0 driver) on most nforce series boards and nvidia network too (forcedeth driver). The nvidia sound driver is an OSS driver with, IMHO, very poor sound quality. Unless you have an 8 speaker setup I don't see much use in installing it.


Håkan

---


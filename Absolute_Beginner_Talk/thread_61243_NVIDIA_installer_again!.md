---
title: "NVIDIA installer again!"
date: 2005-08-30
forum: Absolute Beginner Talk
---

### Post by Knyven on 2005-08-30
Im using Hoary 5.04

I have downloaded the latest Nvidia driver 7676. And followed instructions.

1.) I have successfully stopped the X server and the installation went to Accept/Do not Accept menu.

2) Error: No precompiled kernel interface was found, and told me it will download at ftp:nvidia.com.. .but it did not find any:  Unable to find the kernel source tree for currently running kernel....... If you know the correct source files and installer you may specify the kernel source path with '--kernel-source-path' commandline options.

ok, ive searched the web and i found out to "apt-get install build-essential" and it didnt work.

i have downloaded and install "nvidia-kernel-source.tar.gz" and it didnt work, how do you "path" anyway usr/scr/

this is the nvidia install log file:
[COLOR=DarkRed]nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Wed Aug 31 11:36:44 2005

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  no precompiled interface: false
  no ncurses color        : false
  query latest driver ver : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : /usr/X11R6
  OpenGL install prefix   : /usr
  compat32 install prefix : (not specified)
  installer install prefix: /usr
  utility install prefix  : /usr
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
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel; on Red Hat Linux systems, for example, be sure you have the
       'kernel-source' rpm installed.  If you know the correct kernel source
       files are installed, you may specify the kernel source path with the
       '--kernel-source-path' commandline option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).
[/COLOR]

---

### Post by poofyhairguy on 2005-08-31
I can't help you the way you want...I failed at this as well. But I will point you to this:

[http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)

and promise that those drivers are still really good.

---


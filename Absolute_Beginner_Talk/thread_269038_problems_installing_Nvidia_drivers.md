---
title: "problems installing Nvidia drivers"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by Sambie on 2006-10-01
I'm trying to install the latest drivers for my graphics card. It tells me that I need to install binutils because I do not have ld. I have downloaded binutils-2.17.tar.gz but I do not know how to install it properly.Can somebody please explain? Please explain so that a newbie like me could explain.

---

### Post by kinematic on 2006-10-01
binutils is part of the build-essential package wich you can get from the repository.
if you do a> sudo aptitude install binutilsyou should be fine.

---

### Post by nudnik on 2006-10-01
If you don't need the absolute latest (8774), you could always use the repositories

sudo apt-get install nvidia-glx

The above command will install a Nvidia driver especially compiled for Ubuntu, if you have  recent card that is. If you are using a much older card, use the command below.

sudo apt-get install nvidia-glx-legacy

---

### Post by nudnik on 2006-10-01
Here is a HOW TO I wrote a week or so ago for it is worth. It was approved by the forum staff, so I assume it wont cause implosion or lycanthropy :mrgreen: 

Nvidia driver compile instructions for Ubuntu 6.06 "Dapper Drake" 32 bit.

All "CODE" must be typed and entered into the "Terminal" interface accessible from the upper left hand of the desktop by clicking on the "Applications" tab. A dialog box will drop down from which you should choose "Accessories" which will cause another box to appear from which you can activate the Terminal.

Navigate to [www.nvidia.com](www.nvidia.com) and download the latest IA32 driver to the desktop. (Currently NVIDIA-Linux-x86-1.0-8774-pkg1.run)

Make sure the headers for your kernel are installed.

Install the necessary build libraries, components from the repositories.
         CODE
sudo apt-get install gcc

sudo apt-get install libc6dev

[Additionally the following may be needed:
sudo apt-get install nvidia-kernel-common
sudo apt-get install nvidia-kernel-source
sudo apt-get install xorg-dev
sudo apt-get install xserver-xorg-dev]

Press Ctrl+Alt+F1 to exit graphical mode and access the command line. 

Log in.

Go root to avoid potential annoying problems.
 
 CODE
sudo -s

Stop the Gnome display manager.
            CODE
sudo /etc/init.d/gdm stop
Navigate to the Desktop directory.
   CODE
cd Desktop

Begin dialog with driver compiler/installer.
CODE
sh NVIDIA-Linux-x86-1.0-8774-pkg1.run

Accept the license agreement.

Nvidia package states your kernel is not compatible with the version it is attempting to install. The package will ask permission to check the Nvidia site for pre-compiled drivers compatible with your kernel. Click "OK". It will find none. The package will then offer to compile a driver for your kernel. Click "OK". The package should then compile a driver for your kernel. The package will then ask if you wish the configuration of your xserver settings. Answer in the affirmative.
 
Reboot the machine.
CODE
reboot

---

### Post by missmoondog on 2006-10-01
or, you could just install zenwalk 3.0 and it works out of the box! 

[http://users.zenwalk.org/](http://users.zenwalk.org/)

---

### Post by Sambie on 2006-10-01
Im getting this error

     NVIDIA Accelerated Graphics Driver for Linux-x86 (1.0-8774)



  ERROR: An NVIDIA kernel module 'nvidia' appears to already be loaded in your
         kernel.  This may be because it is in use (for example, by the X
         server), but may also happen if your kernel was configured without
         support for module unloading.  Please be sure you have exited X
         before attempting to upgrade your driver.  If you have exited X, know
         that your kernel supports module unloading, and still receive this
         message, then an error may have occured that has corrupted the NVIDIA
         kernel module's usage count; the simplest remedy is to reboot your
         computer.

                                       OK







  NVIDIA Software Installer for Unix/Linux                      [www.nvidia.com](www.nvidia.com)

and then

   NVIDIA Accelerated Graphics Driver for Linux-x86 (1.0-8774)





  ERROR: Installation has failed.  Please see the file
         '/var/log/nvidia-installer.log' for details.  You may find
         suggestions on fixing installation problems in the README available
         on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

                                       OK










  NVIDIA Software Installer for Unix/Linux                      [www.nvidia.com](www.nvidia.com)

after clicking Ok.

---

### Post by Sambie on 2006-10-01
> **Sambie said:**
> Im getting this error

     NVIDIA Accelerated Graphics Driver for Linux-x86 (1.0-8774)



  ERROR: An NVIDIA kernel module 'nvidia' appears to already be loaded in your
         kernel.  This may be because it is in use (for example, by the X
         server), but may also happen if your kernel was configured without
         support for module unloading.  Please be sure you have exited X
         before attempting to upgrade your driver.  If you have exited X, know
         that your kernel supports module unloading, and still receive this
         message, then an error may have occured that has corrupted the NVIDIA
         kernel module's usage count; the simplest remedy is to reboot your
         computer.

                                       OK







  NVIDIA Software Installer for Unix/Linux                      [www.nvidia.com](www.nvidia.com)

and then

   NVIDIA Accelerated Graphics Driver for Linux-x86 (1.0-8774)





  ERROR: Installation has failed.  Please see the file
         '/var/log/nvidia-installer.log' for details.  You may find
         suggestions on fixing installation problems in the README available
         on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

                                       OK










  NVIDIA Software Installer for Unix/Linux                      [www.nvidia.com](www.nvidia.com)

after clicking Ok.

Here is the log

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sun Oct  1 07:40:13 2006

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
ERROR: An NVIDIA kernel module 'nvidia' appears to already be loaded in your
       kernel.  This may be because it is in use (for example, by the X
       server), but may also happen if your kernel was configured without
       support for module unloading.  Please be sure you have exited X before
       attempting to upgrade your driver.  If you have exited X, know that your
       kernel supports module unloading, and still receive this message, then
       an error may have occured that has corrupted the NVIDIA kernel module's
       usage count; the simplest remedy is to reboot your computer.

---

